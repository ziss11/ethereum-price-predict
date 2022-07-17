# **Laporan Proyek Machine Learning - Abdul Azis**
## **Domain Proyek**
### **Latar Belakang** 
Selama bertahun-tahun prediksi harga pasar telah menarik dan menantang investor serta peneliti, karena banyak ketidakpastian
yang terlibat dan banyak variabel yang mempengaruhi pasar. Beberapa tahun terakhir, pasar tidak hanya tentang saham tetapi juga mata uang digital atau _cryptocurrency_. _Cryptocurrency_ merupakan mata uang digital yang transaksinya dapat dilakukan menggunakan jaringan internet.

Saat ini telah banyak jenis mata uang kripto dan salah satu yang sedang terkenal saat ini adalah _Ethereum_. _Ethereum_ adalah token Aset Kripto yang mirip dengan _bitcoin_ karena dapat digunakan dalam transaksi peer-to-peer, atau dibeli dan dijual di bursa dengan nilai spekulatif. _Ethereum_ dan pasar _cryptocurrency_ lainnya dapat diperdagangkan setiap saat karena tidak memiliki periode tutup, inilah yang membedakannya dengan pasar lainnya. _Ethereum_ lebih mudah berubah dan berisiko bagi para pedagang. Faktor ketidakpastian yang ada, perlu dikurangi oleh para pedagang untuk meminimalkan risiko. Salah satu cara yang digunakan untuk melakukan hal tersebut adalah prediksi harga _Ethereum_ secara akurat.

Saat melakukan prediksi, di perlukan metode yang tepat. Salah satunya adalah dengan menerapkan machine learning. Machine Learning adalah cabang dari kecerdasan buatan (AI) dan ilmu komputer yang berfokus pada penggunaan data dan algoritma untuk meniru cara manusia belajar. Penerapan machine learning membantu dalam proses analisis data besar dan kompleks, sehingga tugas bisa diselesaikan dengan cepat.

Berdasarkan hal tersebut, maka dilakukan penelitian tentang prediksi harga _Ethereum_ menggunakan machine learning. Proyek machine learning ini di buat agar dapat memprediksi harga pasar _Ethereum_ di masa mendatang. Dengan penerapan machine learning di harapkan dapat mengurangi tingkat kerugian akibat harga mata uang _Ethereum_ yang tidak stabil.

Referensi:
- [Prediksi Harga Cryptocurrency dengan metode K-Nearest Neighbours](http://ejournal.nusamandiri.ac.id/index.php/pilar/article/view/30)

## **Business Understanding**
### **Problem Statement**
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

* Bagaimana cara menganalisa data harga mata uang Kripto?
* Bagaimana cara memproses data harga mata uang Ethereum sehingga dapat di latih dengan baik oleh model?
* Bagaimana cara membangun model machine learning yang dapat memprediksi harga dengan baik?

### **Goals**
Tujuan dibuatnya proyek ini adalah sebagai berikut:

* Mendapatkan analisa yang cukup untuk memahami data Harga mata uang kripto.
* Melakukan persiapan pada data agar dapat dengan mudah di mengerti oleh model.
* Membuat model machine learning yang dapat memahami pola pada data dengan baik.
* Dapat memprediksi harga dengan akurat.

### **Solution Statement**
Solusi yang dapat diterapkan agar goals diatas terpenuhi adalah sebagai berikut:

* Melakukan analisa pada data untuk dapat memahami data yang ada dengan menerapkan teknik visualisasi data. Analisa yang dapat dilakukan yaitu, antara lain:
    * Menangani _missing value_ (data yang hilang) pada data.
    * Memeriksa korelasi antar data penting untuk memahami hubungan data target dan data fitur.

* Melakukan pemrosesan pada data seperti:
    * Mengatasi outlier pada data dengan menerapkan IQR method.
    * Normalisasi data pada fitur numerik.

* Membangun model regresi yang dapat memprediksi bilangan kontinu sesuai dengan permasalahan yang ingin di selesaikan. Beberapa algoritma yang akan digunakan pada model regresi proyek ini yaitu, sebagai berikut:
    * Support Vector Machine
    * K-Nearest Neighbours
    * Random Forest

* Menerapkan teknik Grid Search untuk mendapatkan parameter-parameter dengan performa terbaik pada masing-masing model.

## **Data Understanding**
Dataset yang di gunakan pada proyek machine learning ini merupakan dataset riwayat harga mata uang Ethereum dari waktu ke waktu. Dataset tersebut dapat di unduh di website kaggle: [Cryptocurrency Historical Prices](https://www.kaggle.com/datasets/sudalairajkumar/cryptocurrencypricehistory?select=coin_Ethereum.csv).

Setelah dilakukan analisa pada data, didapatkan informasi bahwa:

* Format dataset yaitu CSV (Comma-Seperated Values)
* Jumlah kolom data yang terdapat didalam dataset berjumla 10 kolom, antara lain: _SNo, Name, Symbol, Date, High, Low, Open, Close, Volume, Marketcap_.
* Terdapat 2161 jumlah sample yang terdapat didalam dataset.
* Terdapat 6 kolom data yang memiliki tipe data Float yaitu (_High, Low, Open, Close, Volume, Marketcap_), 
* Terdapat 1 kolom data yang memiliki tipe data Integer yaitu (_SNo_)
* Terdapat 2 kolom data yang memiliki tipe data Object atau String yaitu (_Name, Symbol_)
* Tidak terdapat _missing value_ pada dataset
### **Variabel-variabel pada dataset adalah sebagai berikut:**

* Name: Nama mata uang kripto
* Symbol: Simbol mata uang kripto
* Date: Tanggal pencatatan data
* High : Harga tertinggi pada hari tertentu
* Low : Harga terendah pada hari tertentu
* Open : Harga pembukaan pada hari tertentu
* Close : Harga penutupan pada hari tertentu
* Volume : Volume transaksi pada hari tertentu
* Mastercap : Kapitalisasi pasar dalam USD

Sebelum melakukan pemrosesan data untuk pelatihan, perlu dilakukan analisa pada data untuk mengetahui keadaan pada data seperti korelasi antar fitur dan _outlier_ pada data. Berikut visualisasi data yang menunjukkan korelasi atar fitur dan _outlier_ pada data:

* Menangani _Oulier_</br>
  Jika dilihat divisualisasi _outlier_ dibawah hampir semua data numeric memiliki data _outlier_. Terdapat beberapa teknik untuk mengatasi _outlier_ pada data. Pada proyek ini akan menerapkan teknik _IQR Method_ yaitu dengan menghapus data yang berada diluar _interquartile range_. Interquartile merupakan range diantara kuartil pertama(25%) dan kuartil ketiga(75%).
  
  <image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/outlier%20visualization.png' style='background-color: #FFFFFF;' width= 500/>

* Univariate Analysis</br>
  Karena target prediksi dari dataset ini ada pada fitur Close_Price yang merupakan harga crypto coin Ethereum, jadi hanya fokus menganalisis korelasi data pada feature tersebut. Dari hasil visualisasi data dibawah dapat disimpulkan bahwa peningkatan harga crypto coin ethereum sebanding dengan penurunan jumlah sampel data.</br>

  <image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/univariate%20analysis.png' style='background-color: #FFFFFF;' width=500/>

* Multivariate Analysis</br>
  Jika di lihat dari visualisasi data dibawah. Fitur Close pada sumbu y memiliki korelasi dengan data pada fitur High, Low, Open, dan Marketcap. Korelasi yang terdapat pada data-data tersebut merupakan korelas yang tinggi, sedangkan untuk fitur Volume terlihat memiliki korelasi yang cukup lemah karena sebaran datanya tidak membentuk pola.</br>

  <image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/multivariate%20analisis.png' style='background-color: #FFFFFF;' width=500/></br>

  Untuk lebih jelasnya dapat dilihat melalui visualisasi dibawah yang menunjukkan skor korelasi di tiap fitur dengan fitur Close. Pada fitur High, Low, Open dan Marketcap memiliki skor korelasi yang terbilang tinggi yaitu di atas 0.9. Sedangkan pada fitur Volume memiliki skor korelasi yang cukup rendah yaitu 0.38. Sehingga fitur Volume ini dapat didrop dari dataset.</br>

  <image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/matrix%20correlation.png' style='background-color: #FFFFFF;' width=500/>

## **Data Preparation**
Berikut merupakan tahapan dalam mempersiapkan data untuk keperluan pelatihan model:
### **Menghapus data yang tidak diperlukan dan merubah nama column**
Kolom data seperti (SNo, Name, Symbol, Date, Marketcap) tidak diperlukan untuk pelatihan, karena data tersebut akan mengganggu model dalam mempelajari data. Karena isi dari data tersebut tidak memiliki value yang berarti untuk dipelajari oleh model. Lalu, mengubah nama kolom High, Low, Open, Close menjadi nama kolom yang dapat lebih dipahami.
|  From  |      To     |
| ------ | ----------- |
| High   | High_Price  |
| Low    | Low_Price   |
| Open   | Open_Price  |
| Close  | Close_Price |
### **Split dataset**
Membagi dataset menjadi data latih (_train_) dan data uji (_test_) merupakan hal yang harus kita lakukan sebelum membuat model.Data latih adalah sekumpulan data yang akan digunakan oleh model untuk melakukan pelatihan. Sedangkan, data uji adalah sekumpulan data yang akan digunakan untuk memvalidasi kinerja pada model yang telah dilatih. Karena data uji berperan sebagai data baru yang belum pernah dilihat oleh model, maka cara ini efektif untuk memeriksa performa model setelah proses pelatihan dilakukan. Proporsi pembagian dataset pada proyek ini menggunakan proporsi pembagian 90:10 yang berarti sebanyak 90% merupakan data latih dan 10% persen merupakan data uji.
### **Normalisasi data**
Melakukan transformasi pada data fitur fitur yang akan dipelajari oleh model menggunakan _library_ _MinMaxScaler_. _MinMaxScaler_ mentransformasikan fitur dengan menskalakan setiap fitur ke rentang tertentu. _Library_ ini menskalakan dan mentransformasikan setiap fitur secara individual sehingga berada dalam rentang yang diberikan pada set pelatihan, pada _library_ ini memiliki range default antara 0 dan 1. Dengan merenapkan teknik normalisasi data, model akan dengan lebih mudah mengenali pola-pola yang terdapat pada data sehingga akan menghasilkan prediksi yang lebih baik daripada tidak menggunakan teknik normalisasi.

## **Modeling**
Algoritma _machine learning_ yang digunakan pada proyek ini yaitu _Support Vector Regression, K-Nearest Neighbours, Random Forest_.
### **Support Vector Regression**
_Support Vector Regression_ (SVR) menggunakan prinsip yang sama dengan SVM pada kasus klasifikasi. Perbedaannya adalah jika pada kasus klasifikasi, SVM berusaha mencari ‘jalan’ terbesar yang bisa memisahkan sampel-sampel dari kelas berbeda, maka pada kasus regresi SVR berusaha mencari jalan yang dapat menampung sebanyak mungkin sampel di ‘jalan’. Pada pembuatan model ini dilakukan dengan menggunakan modul yang tersedia di library _scikit-learn_ dengan menggunakan beberapa parameter sebagai berikut: 

* `kernel` = rbf. Parameter ini merupakan metode yang digunakan untuk mengambil data sebagai input dan mengubahnya menjadi bentuk pemrosesan data yang diperlukan.
* `gamma` = 0.003. Secara intuitif, parameter gamma menentukan seberapa jauh pengaruh satu contoh pelatihan mencapai, dengan nilai rendah berarti 'jauh' dan nilai tinggi berarti 'dekat'. Parameter gamma dapat dilihat sebagai kebalikan dari radius pengaruh sampel yang dipilih oleh model sebagai vektor pendukung.
* `C (parameter Regularisasi)` = 100000. Parameter C menukar klasifikasi yang benar dari contoh pelatihan terhadap maksimalisasi margin fungsi keputusan. Untuk nilai C yang lebih besar, margin yang lebih kecil akan diterima jika fungsi keputusan lebih baik dalam mengklasifikasikan semua titik pelatihan dengan benar. C yang lebih rendah akan mendorong margin yang lebih besar, oleh karena itu fungsi keputusan yang lebih sederhana, dengan mengorbankan akurasi pelatihan. Dengan kata lain C berperilaku sebagai parameter regularisasi dalam SVR.

Pada tahap ini model akan melakukan pelatihan terhadap data latih untuk mendapatkan error seminimal mungkin, kemudian setelah pelatihan model melakukan prediksi terhadap data yang belum pernah di lihat sebelumnya menggunakan data uji. Namun algoritma ini memiliki keunggulan dan kekurangan.

Berikut keunggulan Support Vector Machine:

* SVR efektif pada data berdimensi tinggi (data dengan jumlah fitur atau atribut yang sangat banyak).
* SVR efektif pada kasus di mana jumlah fitur pada data lebih besar dari jumlah sampel.
* SVR menggunakan subset poin pelatihan dalam fungsi keputusan (disebut support vector) sehingga membuat penggunaan memori menjadi lebih efisien.   

Berikut kelemahan Support Vector Machine:

* Sulit dipakai dalam problem berskala besar. Skala besar dalam hal ini dimaksudkan dengan jumlah sample yang diolah.
### **K-Nearest Neighbours**
K-nearest neighbor adalah salah satu algoritma machine learning dengan pendekatan supervised learning yang bekerja dengan mengkelaskan data baru menggunakan kemiripan antara data baru dengan sejumlah data (k) pada lokasi yang terdekat yang telah tersedia. Algoritma ini menerapkan lazy learning” atau “instant based learning” dan merupakan algoritma non parametrik. Algoritma KNN digunakan untuk klasifikasi dan regresi. Pada pembuatan model ini akan menggunaka modul KNN yang terlah di sediakan oleh library _scikit-learn_ .Pada model ini hanya akan menggunakan 1 parameter yaitu `n_neighbours` (Jumlah tetangga). Jumlah _neighbours_ yang di gunakan yaitu sejumlah 5 neighbours. Kemudian, untuk menentukan titik mana dalam data yang paling mirip dengan input baru, KNN menggunakan perhitungan ukuran jarak. Metrik ukuran jarak yang digunakan secara default pada library sklearn adalah Minkowski distance. Setelah menentukan nilai-nilai pada parameter model melakukan pelatihan menggunakan data latih setelah itu model akan melakukan prediksi terhadap data yang belum pernah dilihat dengan menggunakan data uji. Namun algoritma ini memiliki keunggulan dan kekurangan.

Berikut keunggulan K-Nearest Neighbours:

* Sangat sederhana dan mudah dipahami
* Sangat mudah diterapkan
* Dapat digunakan dalam proses klasifikasi maupun regresi.
* Sangat mudah jika akan dilakukan penambahan data
* Parameter yang diperlukan sedikit, yaitu hanya jumlah tetangga yang dipertimbangkan (K), dan metode perhitungan jaraknya (distance metrik)

Berikut kelemahan K-Nearest Neighbours:

* Perlu menentukan nilai K yang tepat.
* Computation cost yang tinggi
* Waktu pemrosesan yang lama jika datasetnya sangat besar.
* Tidak cukup bagus jika diterapkan pada high dimensional data
* Sangat sensitif pada data yang memiliki banyak noise (noisy data), banyak data yang hilang (missing data), dan pencilan (outliers).

### **Random Forest**
Algoritma ini merupakan sekumpulan algoritma decision tree. Konsep dasar decision tree adalah mengubah data menjadi aturan-aturan keputusan. Kombinasi dari masing–masing decision tree yang baik kemudian dikombinasikan ke dalam satu model. Random Forest bergantung pada sebuah nilai vector random dengan distribusi yang sama pada semua pohon yang masing masing decision tree memiliki kedalaman yang maksimal. Algoritma ini bisa menyelesaikan permasalahan klasifikasi dan regresi. Pada kasus klasifikasi, prediksi akhir diambil dari prediksi terbanyak pada seluruh pohon. Sedangkan, pada kasus regresi, prediksi akhir adalah rata-rata prediksi seluruh pohon. Untuk pembuatan model Random Forest, akan menggunakan beberapa parameter, antara lain:

* `n_estimator`: jumlah trees (pohon) di forest. Di sini kita set `n_estimator`=50.
* `max_depth`: kedalaman atau panjang pohon. Ia merupakan ukuran seberapa banyak pohon dapat membelah (splitting) untuk membagi setiap node ke dalam jumlah pengamatan yang diinginkan.

Setelah itu model akan melakukan pelatihan menggunakan data latih, setelah itu model bisa melakukan prediksi pada data yang belum pernah diliath dengan menggunakan data uji. Namun model ini memiliki beberapa keuntungan dan juga kelemahan.

Berikut keunggulan Random Forest:

* Algoritma Random Forest merupakan algoritma dengan pembelajaran paling akurat yang tersedia. Untuk banyak kumpulan data, algoritma ini menghasilkan pengklasifikasi yang sangat akurat.
* Berjalan secara efisien pada data besar.
* Dapat menangani ribuan variabel input tanpa penghapusan variabel.
* Memiliki metode yang efektif untuk memperkirakan data yang hilang dan menjaga akurasi ketika sebagian besar data hilang.

Berikut kelemahan Random Forest:

* Algoritma Random Forest overfiting untuk beberapa kumpulan data dengan tugas klasifikasi/regresi yang bising/noise.
* Untuk data yang menyertakan variabel kategorik dengan jumlah level yang berbeda, Random Forest menjadi bias dalam mendukung atribut dengan level yang lebih banyak. Oleh karena itu, skor kepentingan variabel dari Random Forest tidak dapat diandalkan untuk jenis data ini.

Pada proyek ini yang menjadi model dengan solusi terbaik adalah _Support Vector Regression (SVR)_. Dimana model ini memiliki nilai error paling rendah dari kedua model lainnya dan hasil prediksinya yang paling mendekati dengan angka sebenarnya.

## **Evaluation**
Pada proyek machine learning ini, metrik evaluasi yang digunakan yaitu _mean squared error (MSE)_ yang mana metrik ini merupakan ukuran seberapa dekat garis pas dengan titik data. Untuk setiap titik data, model mengambil jarak secara vertikal dari titik ke nilai y yang sesuai pada kecocokan kurva (kesalahan), dan kuadratkan nilainya.

<image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/rumus%20MSE.jpg' style='background-color: #FFFFFF;' width=500/>

dimana:</br>
At = Nilai Aktual permintaan</br>
Ft = Nilai hasil prediksi</br>
n = banyaknya data</br>

Setelah melakukan evaluasi menggunakan metrik _mean squared error_ pada model dengan menggunakan data uji didapatkan hasil seperti berikut:

<image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/result%20mse.png' style='background-color: #FFFFFF;' width=500/></br>

Dapat dilihat dari visulisasi diatas bahwa MSE pada model SVR merupakan MSE yang paling rendah dari kedua model lainnya, selain itu jumlah error pada saat pengujian tidak berbeda jauh dengan error pada saat pelatihan.

<image src='https://raw.githubusercontent.com/ziszz/ethereum-price-predict/master/visualizations/predict%20visulization.png' style='background-color: #FFFFFF;' width=500/></br>

Dapat juga dilihat melalui visualisasi diatas bahwa angka prediksi pada model SVR yang paling mendekati dengan angka sebenarnya.


