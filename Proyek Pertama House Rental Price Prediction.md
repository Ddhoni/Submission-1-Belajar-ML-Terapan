# Proyek Pertama House Rental Price Prediction
###### Disusun Oleh : Muhammad Dhoni Apriyadi


## Domain Proyek
### Latar Belakang
Tempat tinggal atau properti merupakan suatu kebutuhan primer bagi manusia dalam menjalani kehidupan. Selain itu, properti yang memiliki banyak fasilitas,lokasi yang mudah dijangkau,luas bangunan,perabotan, serta fitur lainnya menjadi aset berharga atau nilai tambah dari tempat tinggal itu sendiri.

Harga dari setiap properti diukur dari nilai atau aset yang dimiliki oleh properti tersebut. Namun, harga ini tidak selalu pasti dan sulit untuk melakukan prediksi akurat secara manual. Faktor ketidakpastian perlu dikurangi oleh perusahaan sewa dengan membangun sistem prediksi yang dapat menentukan berapa harga sewa yang pantas untuk karakteristik properti tertentu.[[1]](https://ejournal.upnvj.ac.id/index.php/informatik/article/view/3635)

Dalam mencapai hal tersebut, maka dilakukan penelitian dalam memprediksi harga sewa tinggal menggunakan metode machine learning. Diharapkan metode ini mampu memprediksi harga sewa yang sesuai dengan harga pasar. Prediksi ini nantinya dijadikan acuan bagi perusahaan ataupun perseorangan dalam melakukan kegiatan sewa-menyewa tempat tinggal dengan harga yang dapat mendatangkan profit bagi perusahaan.

## Business Understanding

### Proyek ini dibangun untuk perusahaan dengan karakteristik bisnis sebagai berikut :

- Perusahaan memiliki atau membeli properti kemudian menyewakan  ke konsumen.
- Perusahaan membuka jasa konsultasi harga sewa rumah dan apartemen ke konsumen.


### Problem Statement
- Faktor apa yang paling berpengaruh terhadap harga sewa rumah atau apartemen?
- Bagaimana cara melakukan pemrosesan data agar memiliki model yang terbaik?
- Berapa harga sewa rumah di pasaran berdasarkan karakteristik tertentu?
Goals
### Goals
- Mengetahui faktor yang paling berpengaruh pada harga sewa rumah atau apartemen.
- Melakukan data *preprocessing* dan *feature engineering* yang baik sehingga mendapatkan model yang terbaik.
- Membuat model *machine learning* yang dapat memprediksi harga sewa rumah seakurat mungkin berdasarkan karakteristik tertentu.

### Solution Statement
- Menganalisis data dengan cara *univariate analysis* serta *multivariate analysis*. 
- Memahami data juga dapat dilakukan dengan visualisasi. Memahami data dapat membantu untuk mengetahui kolerasi antar fitur, mendeteksi pencilan serta yang utama adalah menemukan insight yang menarik.
- Menyiapkan data agar bisa digunakan dalam membangun model.
-  Algoritma yang digunakan dalam proyek ini adalah *Random Forest*, dan *AdaBoost*, *Support Vector Regressor*.

## Data Understanding
Dataset yang digunakan dalam proyek ini merupakan data harga sewa rumah dengan berbagai karakteristik di India. Dataset ini dapat diunduh di [Kaggle : House Rent Prediction Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/house-rent-prediction-dataset)

Berikut informasi pada dataset :

- Dataset berada dalam format CSV (*Comma-Seperated Values*).
- Dataset memiliki jumlah 4746 data dengan 12 fitur.
- Dataset memiliki 2 jenis tipe data yaitu, 4 fitur bertipe  int64 dan 8 fitur bertipe object.
- Tidak ada missing value dalam dataset.

### Variabel - variabel pada dataset
- *Posted On*: Tanggal data diposting.
- *BHK*: Jumlah dari kamar tidur, aula, dan dapur.
- *Rent*: Harga sewa dari properti.
- *Size*: Luas dari properti dalam square feet (sqft).
- *Floor*: Letak dan jumlah lantai properti.
- *Area Type*: Ukuran dari rumah dalam kategori *Super Area* atau *Carpet Area* atau *Build Area*.
- *Area Locality*: Lokasi properti.
- *City*: Kota dimana properti berada.
- *Furnishing Status*: Status perabotan properti, baik Furnished atau Semi-Furnished atau Unfurnished.
- *Tenant Preferred*: Jenis penyewa yang diutamakan pemilik atau agen.
- *Bathroom*: Jumlah kamar mandi.
- *Point of Contact* : Kontak yang dihubungi untuk informasi lebih lanjut mengenai rumah/apartemen.

Dari ke 12 fitur dapat dilihat bahwa fitur Point of Contract dan Posted On dianggap dapat mempengaruhi harga sewa properti sehingga akan dihapus. Hal ini dikarenakan kedua fitur tersebut tidak diperlukan dalam membangun model prediksi harga sewa.

### Univariate Analysis
#### Analisis Sebaran pada setiap fitur kategorik 


Fitur kategorik City, Furnishing Status, dan Tenant Preferred memiliki sebaran sample yang cukup merata.




| City |              | 
| -------- | -------- |
| Bangalore  |   886  | 
| Chennai  |   890  | 
| Delhi  |   605  | 
| Hyderabad  |  867   | 
| Kolkata  |  524   | 
| Mumbai  |  972   |

**Tabel 1**

| Furnishing Status|      | 
| --------        | ----- |
| Furnished       |679    | 
| Semi-Furnished  | 2251  | 
| Unfurnised      | 1814  |

**Tabel 2**
 | Tenant Preferred|      | 
| --------        | ----- |
| Bachelors    |830    | 
| Bachelors/Family  | 3442  | 
| Family      | 472  |

**Tabel 3**


#### Analisis sebaran pada setiap fitur numerik
![Gambar1](https://i.imgur.com/H7QdPFG.png)
            **Gambar 1**


Pada histogram Gambar 4 diatas didapatkan insight yaitu :

-  Sebagian besar rumah memiliki 1 sampai 3 BHK dan 1 sampai 3 kamar mandi.
-  Sebagian besar rumah memiliki luas di bawah 2000 sqft.
-  Rentang harga sewa cukup tinggi, yaitu dari 1200 hingga 3500000. Namun, rata-rata harga rumah hanya 35003. Distribusi harga yang kurang bagus seperti ini dapat berimplikasi pada model.

### Multivariate Analysis

Multivariate Analysis menunjukkan hubungan antara dua atau lebih fitur dalam data.

#### Analisis fitur kategorik

Analisis ini dilakukan untuk melihat kolerasi antara fitur kategorik dengan fitur target.

- #### Fitur City

Dapat dilihat pada histogram Gambar 5 dibawah bahwa fitur *City* memiliki pengaruh cukup signifikan terhadap rata-rata harga sewa, terutama jika properti berada di kota Mumbai. Hal ini dibuktikan dengan sebaran properti yang mencapai harga tertinggi di kota Mumbai. Mumbai merupakan kota  dengan harga properti paling mahal di India untuk ditinggali, disusul dengan dengan Delhi.

![Gambar2](https://i.imgur.com/1lKTCJO.png)
            **Gambar 2**
- #### Fitur Area Type
![Gambar3](https://i.imgur.com/IN1KIOo.png)
             **Gambar 3**
Dapat dilihat bahwasannya fitur Area Type memiliki sedikit pengaruh  terhadap rata-rata harga sewa.


- #### Furnishing Status
![Gambar4](https://i.imgur.com/770n5U5.png)
             **Gambar 4**
 Dapat dilihat fitur Furnishing Status memiliki pengaruh signifikan terhadap rata-rata harga sewa. Merupakan hal biasa bila properti yang memiliki perabotan lengkap akan diberi harga sewa lebih tinggi daripada properti tanpa perabotan.
 
 - #### Fitur Tenant Preferred

![Gambar5](https://i.imgur.com/mFkrdJj.png)
             **Gambar 5**
 Dapat dilihat pada Gambar 8 bahwa fitur T*enant Preferred* memiliki pengaruh yang lumayan signifikan terhadap rata-rata harga sewa. Dari grafik dapat terlihat bahwa properti yang sangat disarankan untuk disewa oleh keluarga memiliki rata-rata harga sewa yang lebih mahal dibanding lainnya


#### Analisis fitur numerik
* Fitur Size dan BHK (Menghapus BHK Outlier) Kedua fitur ini dianalisis karena tidak biasa untuk rumah dengan 1 BHK memiliki luas 100 sqft. Untuk itu ditentukan treshold atau batas 300 sqft/bhk. Data yang berada di bawah batas akan dihapus. Hal ini menyebabkan berkurangnya jumlah sample sebesar 548.

* Fitur Size dan Rent (Menghapus Price per sqft Outlier) Untuk memudahkan dalam mendeteksi outlier, maka dibuat fitur baru 'Price_per_sqft' dari kedua fitur tersebut untuk menganalisis harga sewa per luas sqft.

|  -  |        -    |
| --- | --------     |
|count|4196.000000   |
| mean|32827.385605  | 
| std |41300.048982  | 
| min |571.428571    | 
| 25% |13000.000000  | 
| 50% |18511.595708  | 
| 75% |34896.788991  | 
| max |1400000.000000| 

**Tabel 4**
Pada Tabel 4 terlihat bahwa harga 571 per sqft sangat rendah dan harga 1400000 per sqft sangat tinggi. Untuk itu penghapusan outlier price per sqft outlier dengan mean dan one standard deviation yang telah dikelompokkan berdasarkan kota. Hal ini menyebabkan berkurangnya jumlah sample sebesar 497.

- Fitur Bathroom dan BHK (Menghapus Bathroom Outlier) Kedua fitur ini dianalisis karena tidak biasa untuk rumah dengan 2 BHK memiliki 4 kamar mandi. Untuk itu ditentukan batas bahwa jumlah kamar mandi tidak boleh melebihi jumlah BHK + 2. Hal ini menyebabkan berkurangnya sample sebesar 3.
- Melihat kolerasi antara semua fitur numerik
![Gambar 6](https://i.imgur.com/zXgeffB.png)
**Gambar 6**

Fitur *BHK*, *Size*, serta *Bathroom* memiliki korelasi yang tidak signifikan dengan fitur target. Hal ini mungkin disebabkan oleh kurangnya data dalam penelitian ini.Fitur *BHK* dan *Bathroom berkolerasi signifikan dengan fitur size. Hal ini sudah sesuai harapan dari penghapusan pencilan yang sudah dilakukan sebelumnya.






## Data Preparation

Dalam Data preparation dilakukan beberapa langkah dan metode supaya model yang dibangun berjalan dengan baik yaitu, 

- One Hot Encoding

One hot encoding adalah teknik mengubah data kategorik menjadi data numerik dimana setiap kategori menjadi kolom baru dengan nilai 0 atau 1. Fitur yang akan diubah menjadi numerik pada proyek ini adalah *Area Type*, *City*, *Furnishing Status*, dan *Tenant Preferred*.

- Train Test Split

Train test split aja proses membagi data menjadi data latih dan data validasi . Data train akan digunakan untuk membangun model, sedangkan data uji akan digunakan untuk menguji performa model. Pada proyek ini dataset sebesar 3696 dibagi menjadi 3511 untuk data latih dan 185 untuk data validasi. Dengan rasio 95% data pada data train dan 5% pada data validasi.

- Normalization

Model yang dibangun akan memiliki performa lebih baik dan bekerja lebih cepat jika dimodelkan dengan data seragam yang memiliki skala relatif sama. Salah satu teknik normalisasi yang digunakan pada proyek ini adalah Standarisasi dengan sklearn.preprocessing.StandardScaler.

## Modeling
Algoritma Penelitian ini melakukan pemodelan dengan 3 algoritma, yaitu Random Forest, AdaBoost dan SVM-Regressor

*   Random Forest 
Merupakan model yang termasuk teknik bagging dengan terdiri dari beberapa model dan bekerja secara bersama-sama.[[2]](https://repository.usd.ac.id/35513/2/155314090_full.pdf)

    
    -  Tahapan Umum Cara kerja *Random Forest*

    Diawali dengan pemilihan k pada sampel dataset yang diambil secara acak dengan pengembalian
    Gunakan dataset untuk membangun decision tree ke-i
    Ulangi langkah kedua langkah di atas sebanyak k.
    Pada kasus proyek ini bertipe regresi maka dari itu yang digunakan adalah *Random Forest Regressor* dari *library scikit-learn*.dengan beberapa nilai parameter. Berikut adalah parameter-parameter yang digunakan:

    `n_estimator`: jumlah trees (pohon) di forest. dalam model yang dibangun diset n_estimator=50.
    `max_depth`: kedalaman atau panjang pohon.Di proyek ini menggunakan max_depth = 16
    `random_state`: digunakan untuk mengontrol random number generator yang digunakan. Dalam membangun model digunakan random_state = 55.

#### Kelebihan & Kekurangan Random Forest

Kelebihan: yaitu dapat mengatasi noise dan missing value serta dapat mengatasi data dalam jumlah yang besar.
Kekurangan:  pada algoritma *Random Forest* yaitu interpretasi yang sulit dan membutuhkan tuning model yang tepat untuk data.

- Adaboost 
Algoritma ini bekerja dengan menggabungkan beberapa model sederhana dan dianggap lemah (*weak learners*) sehingga membentuk suatu model yang kuat (strong *ensemble learner*). Algoritma boosting muncul dari gagasan mengenai apakah algoritma yang sederhana seperti *linear regression* dan *decision tree* dapat dimodifikasi untuk dapat meningkatkan performa.

     - Tahapan umum cara Kerja *AdaBOOST *
 
     Awalnya, semua kasus dalam data latih memiliki weight atau bobot yang sama setelah itu model akan memeriksa apakah observasi yang dilakukan sudah benar. Lalu bobot yang lebih tinggi kemudian diberikan pada model yang salah sehingga mereka akan dimasukkan ke dalam tahapan selanjutnya. Proses iteratif ini berlanjut sampai model mencapai akurasi yang diinginkan kemudian membangun model pada dataset pelatihan, kemudian model kedua dibangun untuk memperbaiki kesalahan yang ada pada model pertama. Prosedur ini dilanjutkan sampai dan kecuali kesalahan diminimalkan, dan kumpulan data diprediksi dengan benar.

    Berikut merupakan parameter-parameter yang digunakan pada proyek ini :

    `learning_rate`: bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting, pada proyek ini digunakan learning_rate = 0.05
    `random_state`: digunakan untuk mengontrol random number generator yang digunakan, pada proyek ini digunakan random_state = 55

    #### Kelebihan & Kekurangan AdaBOOST

    Kelebihan: Relatif lebih mudah untuk diimplementasikan dan waktu pengujian yang relatif cepat sehingga cocok dipakai dalam implementasi kondisi real time.
    Kekurangan: Membutuhkan hyperparameter tuning yang tepat dalam mentuning sebuah model.


- SVM Regressor
merupakan Model ML multifungsi yang dapat digunakan untuk menyelesaikan permasalahan klasifikasi, regresi, dan pendeteksian outlier.
    -  Tahapan Umum Cara Kerja *Support Vector Regression* (SVR)
    menggunakan prinsip yang sama dengan SVM pada kasus klasifikasi. Perbedaannya adalah jika pada kasus klasifikasi, SVM berusaha mencari ‘jalan’ terbesar yang bisa memisahkan sampel-sampel dari kelas berbeda, maka pada kasus regresi SVR berusaha mencari jalan yang dapat menampung sebanyak mungkin sampel di ‘jalan’ dan , pada SVR support vector adalah sampel yang menjadi pembatas jalan yang dapat menampung seluruh sampel pada data. Pada proyek ini digunakan SVR tanpa parameter
    
    #### Kelebihan & Kekurangan SVM Regressor

    Kelebihan : SVM efektif pada data berdimensi tinggi (data dengan jumlah fitur atau atribut yang sangat banyak) serta jumlah fitur pada data lebih besar daripada sampel

    Kekurangan : Sulit dipakai dalam problem berskala besar. Skala besar dalam hal ini dimaksudkan dengan jumlah sample yang diolah

## Evaluation

Metrik evaluasi yang digunakan pada proyek ini adalah akurasi dan *mean squared error (MSE)*. Akurasi menentukan tingkat kemiripan antara hasil prediksi dengan nilai yang sebenarnya. *Mean squared error* (MSE) mengukur galat dalam model statistik dengan cara menghitung rata-rata galat dari kuadrat hasil sebenarnya dikurang hasil prediksi. 

Berikut formula MSE : 
$$ \sum_{i=1}^{D} \frac{1}{n}(y_i-y_p)^2 $$ 

Dimana;
n, banyaknya data
yi, nilai sebenarnya
yp , nilai prediksi

Secara komputasi didapatkan nilai dari formula MSE yaitu,

|           | Train              | Test             |
| ----      | --------           | --------          |
| RF        |34694984.664362     |189690332.370555  |
| Boosting  |189673493.550402    |296705630.45973    |
| SVM       |1256652466.449838   |2688190525.953401  |

**Tabel 5** 
Terlihat pada tabel 5 dalam bentuk grafik visualisasi : 

![Gambar7](https://i.imgur.com/IUX21uH.png)
**Gambar 7** 
Dari visualisasi pada Gambar 7. Terlihat bahwa, model *Random Forest* memiliki nilai galat paling kecil dibandingkan dua model yang lainnya. Sehingga dapat dipilih model *Random Forest* sebagai model terbaik dalam melakukan Prediksi pada *House Rental Price*.



### Kesimpulan

Dapat dilihat dari Tiga model Algoritma yang dikembangkan, dapat disimpulkan dari hasil perbandingan serta visualisasi perbandingan prediksi 3 Algoritma yaitu, *Random Forest*, *AdaBoost* , dan *SVM*. dapat disimpulkan model *Random Forest* memiliki nilai galat pada data test yang paling kecil kemudian model dengan *Boosting* memiliki nilai galat yang sedikit lebih banyak daripada model *Random Forest*. Sedangkan model *SVM* memiliki lebih banyak nilai galat dibandingkan *boosting* .
## Referensi 
[1]  M. L. Mu'tashim, T. Muhayat, S. A. Damayanti, H. N. Zaki, and R. Wirawan, “Analisis prediksi harga Rumah Sesuai spesifikasi Menggunakan multiple linear regression,” Informatik : Jurnal Ilmu Komputer.

[2] R.Aji Haristu."Penerapan Metode Random Forest untuk Prediksi Win Ratio Pemain Player Unknown Battleground . Skripsi thesis, Universitas Sanata Dharma (2019)











