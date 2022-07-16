# Laporan Proyek Machine Learning - Abdul Azis
## Domain Proyek
### Latar Belakang 
Selama bertahun-tahun prediksi harga pasar telah menarik dan menantang investor serta peneliti, karena banyak ketidakpastian
yang terlibat dan banyak variabel yang mempengaruhi pasar. Beberapa tahun terakhir, pasar tidak hanya tentang saham tetapi juga mata uang digital atau cryptocurrency. Cryptocurrency merupakan mata uang digital yang transaksinya dapat dilakukan menggunakan jaringan internet.

Saat ini telah banyak jenis mata uang kripto dan salah satu yang sedang terkenal saat ini adalah Ethereum. Ethereum adalah token Aset Kripto yang mirip dengan bitcoin karena dapat digunakan dalam transaksi peer-to-peer, atau dibeli dan dijual di bursa dengan nilai spekulatif. Ethereum dan pasar cryptocurrency lainnya dapat diperdagangkan setiap saat karena tidak memiliki periode tutup, inilah yang membedakannya dengan pasar lainnya. Ethereum lebih mudah berubah dan berisiko bagi para pedagang. Faktor ketidakpastian yang ada, perlu dikurangi oleh para pedagang untuk meminimalkan risiko. Salah satu cara yang digunakan untuk melakukan hal tersebut adalah prediksi harga Ethereum secara akurat.

Saat melakukan prediksi, di perlukan metode yang tepat. Salah satunya adalah dengan menerapkan machine learning. Machine Learning adalah cabang dari kecerdasan buatan (AI) dan ilmu komputer yang berfokus pada penggunaan data dan algoritma untuk meniru cara manusia belajar. Penerapan machine learning membantu dalam proses analisis data besar dan kompleks, sehingga tugas bisa diselesaikan dengan cepat.

Berdasarkan hal tersebut, maka dilakukan penelitian tentang prediksi harga Ethereum menggunakan machine learning. Proyek machine learning ini di buat agar dapat memprediksi harga pasar Ethereum di masa mendatang. Dengan penerapan machine learning di harapkan dapat mengurangi tingkat kerugian akibat harga mata uang Ethereum yang tidak stabil.

Referensi:
- [Prediksi Harga Cryptocurrency dengan metode K-Nearest Neighbours](http://ejournal.nusamandiri.ac.id/index.php/pilar/article/view/30)

## Business Understanding
### Problem Statement
Berdasarkan pada latar belakang di atas, permasalahan yang dapat diselesaikan pada proyek ini adalah sebagai berikut:

* Bagaimana cara menganalisa data harga mata uang Kripto?
* Bagaimana cara memproses data harga mata uang Ethereum sehingga dapat di latih dengan baik oleh model?
* Bagaimana cara membangun model machine learning yang dapat memprediksi harga dengan baik?

### Goals
Tujuan dibuatnya proyek ini adalah sebagai berikut:

* Mendapatkan analisa yang cukup untuk memahami data Harga mata uang kripto.
* Melakukan persiapan pada data agar dapat dengan mudah di mengerti oleh model.
* Membuat model machine learning yang dapat memahami pola pada data dengan baik.
* Dapat memprediksi harga dengan akurat.

### Solution Statement
Solusi yang dapat diterapkan agar goals diatas terpenuhi adalah sebagai berikut:

* Melakukan analisa pada data untuk dapat memahami data yang ada dengan menerapkan teknik visualisasi data. Analisa yang dapat dilakukan yaitu, antara lain:
    * Menangani missing value (data yang hilang) pada data.
    * Memeriksa korelasi antar data penting untuk memahami hubungan data target dan data fitur.

* Melakukan pemrosesan pada data seperti:
    * Mengatasi outlier pada data dengan menerapkan IQR method.
    * Normalisasi data pada fitur numerik.

* Membangun model regresi yang dapat memprediksi bilangan kontinu sesuai dengan permasalahan yang ingin di selesaikan. Beberapa algoritma yang akan digunakan pada model regresi proyek ini yaitu, sebagai berikut:
    * Support Vector Machine
    * K-Nearest Neighbours
    * Random Forest

* Menerapkan teknik Grid Search untuk mendapatkan parameter-parameter terbaik pada masing-masing model.


