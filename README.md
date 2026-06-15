# 🛒 Laporan Big Data Segmentasi Pelanggan E-Commerce Menggunakan Algoritma K-Means Clustering

**UAS Big Data - Kelas A/B**
* Ahmad Zayn Usman (2310511001)
* Fandi Yakub (2310511005)
* Fauzio Yunus Alim (2310511020)

---

## 📄 Abstrak
[cite_start]Pertumbuhan pesat industri e-commerce menghasilkan lonjakan volume data transaksi harian yang masif dan terus terakumulasi[cite: 35, 78]. [cite_start]Skala Big Data ini menyulitkan sistem basis data konvensional untuk memproses dan mengekstraksi wawasan berharga secara efisien[cite: 36, 79]. [cite_start]Tanpa arsitektur analitik yang memadai, perusahaan kehilangan kemampuan mendeteksi anomali, meramalkan tren penjualan, serta mencegah perpindahan pelanggan (churn)[cite: 38, 84]. 

[cite_start]Sebagai solusi, proyek ini mengimplementasikan alur pemrosesan analitik Big Data menggunakan *Synthetic U.S. E-Commerce Dataset* yang berisi jutaan baris pesanan[cite: 43]. [cite_start]Proses mencakup ekstraksi data, transformasi skala besar untuk menangani anomali, serta pemodelan Machine Learning *unsupervised*[cite: 44, 121].

[cite_start]Hasil dari proses pembersihan menyisakan lebih dari 2,19 juta baris data transaksi siap latih[cite: 178]. [cite_start]Analisis deskriptif menemukan dominasi penjualan pada kategori elektronik [cite: 211, 504] [cite_start]dan lonjakan volume pada akhir tahun (November-Desember)[cite: 188, 505]. [cite_start]Pemodelan K-Means berhasil mengidentifikasi 4 klaster optimal[cite: 507]. [cite_start]Segmentasi ini membagi pelanggan menjadi Pelanggan VIP, Loyal, Reguler, dan Pasif[cite: 486, 488, 490, 492]. [cite_start]Penemuan ini menghasilkan rekomendasi strategis aplikatif untuk menjaga retensi pelanggan berharga dan mendistribusikan promosi terarah guna mencegah pelanggan pasif meninggalkan platform[cite: 513].

---

## ⚙️ Metode (Pipeline Big Data)
[cite_start]Tahapan percobaan dalam arsitektur sistem Big Data ini dijalankan menggunakan lingkungan komputasi Google Colab yang diintegrasikan dengan Google Drive untuk efisiensi penyimpanan[cite: 73, 88].
1. [cite_start]**Extract:** Penarikan 1 juta baris *Synthetic U.S. E-Commerce Dataset* secara otomatis menggunakan Kaggle API[cite: 72, 86].
2. [cite_start]**Transform (Data Cleansing & Engineering):** Penanganan *missing values*, eliminasi duplikasi, rekayasa fitur waktu dan finansial, serta *downcasting* tipe data untuk optimasi RAM[cite: 92, 93, 94, 95].
3. [cite_start]**Load:** Pemuatan dan penyimpanan DataFrame bersih ke dalam format `.parquet` di *cloud storage*[cite: 98].
4. [cite_start]**Exploratory Data Analysis (EDA):** Analisis univariat, bivariat, dan multivariat (matriks korelasi) untuk mengekstraksi pola transaksi awal[cite: 106, 116].
5. [cite_start]**Modeling (K-Means):** Standardisasi fitur menggunakan `StandardScaler` [cite: 126][cite_start], penentuan klaster optimal dengan *Elbow Method* [cite: 138][cite_start], dan pelatihan model K-Means Clustering[cite: 121].

---

## 📊 Hasil Analisis

### 1. Data Quality
* [cite_start]**Integritas Tinggi:** Tidak ditemukan adanya baris transaksi yang ganda (0 baris duplikat)[cite: 173, 502].
* [cite_start]**Missing Values Logis:** Terdapat 6,62% data kosong pada kolom `order_delivered_carrier_date` dan `order_delivered_customer_date`[cite: 154, 155]. [cite_start]Hal ini wajar karena merepresentasikan pesanan yang belum dikirim atau dibatalkan[cite: 157]. [cite_start]Fitur ini diabaikan dalam pemodelan karena tidak esensial[cite: 176].
* [cite_start]**Dimensi Akhir:** Dataset siap latih berjumlah 2.199.819 baris transaksi[cite: 178].

### 2. Data Descriptive
* [cite_start]**Tren Waktu:** Terjadi lonjakan pesanan yang sangat drastis menembus 300.000 transaksi pada bulan November dan Desember (periode *holiday season* / *Black Friday*)[cite: 188, 189].
* [cite_start]**Produk Dominan:** Kategori komoditas yang merajai pangsa pasar adalah *electronics* (hampir 700.000 penjualan), disusul *fashion* dan *home goods*[cite: 211].
* [cite_start]**Anomali Nilai:** Terdapat pencilan (*outlier*) bernilai ekstrem di mana satu transaksi bisa bernilai hingga di atas 10.000 USD dengan kuantitas barang yang sedikit (1-2 barang), mengindikasikan pembelian barang elektronik *high-end*[cite: 236, 237, 254].

### 3. Diagnostic & Predictive Modeling
* [cite_start]Berdasarkan grafik *Elbow Method*, patahan kurva melandai secara drastis pada titik $k=4$, sehingga jumlah klaster optimal ditetapkan sebanyak 4 segmen[cite: 449].
* [cite_start]Model K-Means Clustering dengan $k=4$ berhasil memisahkan data dengan baik, divalidasi oleh *Silhouette Score* sebesar 0.3389 dan *Davies-Bouldin Index* di angka 1.0496[cite: 508].

---

## 💡 Insight & Actionable Strategy (Tindak Lanjut Bisnis)
Dari hasil diagnosis *centroid* klaster K-Means, berikut adalah karakteristik 4 segmen pelanggan beserta tindakan strategis bisnisnya:

* 👑 **Klaster 1: Pelanggan VIP / Sultan**
  * [cite_start]**Pola:** Pengeluaran belanja sangat tinggi (rata-rata 6.677,62 USD), membeli barang paling banyak, dan frekuensi sangat sering[cite: 487].
  * [cite_start]**Actionable Insight:** Berikan layanan eksklusif seperti *Personal Shopper*, gratis ongkos kirim tanpa batas, atau akses prioritas (Eksklusif VIP) untuk barang elektronik *high-end* yang baru rilis guna menjaga loyalitas absolut mereka[cite: 513].

* 🤝 **Klaster 2: Pelanggan Loyal / Setia**
  * [cite_start]**Pola:** Konsisten berbelanja dengan total pengeluaran cukup besar (5.019,63 USD) dan frekuensi kedatangan tinggi[cite: 489].
  * **Actionable Insight:** Implementasikan strategi *Cross-Selling*. Mengingat mereka suka belanja barang kategori *electronics* dan *fashion*, rekomendasikan produk aksesori pelengkap dengan bundel harga khusus.

* 🛒 **Klaster 0: Pelanggan Reguler / Menengah**
  * [cite_start]**Pola:** Merupakan kelompok mayoritas dengan nilai belanja wajar (2.857,33 USD) dan frekuensi standar[cite: 491].
  * **Actionable Insight:** Tingkatkan metrik frekuensi transaksi mereka dengan memberikan promosi *cashback* bersyarat atau program "Kumpulkan Poin" untuk menaikkan level mereka ke Klaster Loyal. 

* ⚠️ **Klaster 3: Pelanggan Pasif / Risiko Churn**
  * [cite_start]**Pola:** Daya beli sangat minim (hanya 1.337,80 USD) dan frekuensi kedatangan paling jarang[cite: 493].
  * [cite_start]**Actionable Insight:** Cegah mereka berpindah ke platform kompetitor (*churn mitigation*) dengan meluncurkan kampanye *retargeting* yang agresif, seperti mengirimkan notifikasi *Push/Email* berisi kupon retensi diskon besar[cite: 494, 513].

---

## 🎯 Kesimpulan
Eksperimen Big Data ini membuktikan bahwa kombinasi pemrosesan ETL yang teroptimasi dan algoritma K-Means dapat mengubah jutaan baris data mentah menjadi keputusan bisnis yang *actionable*. [cite_start]Platform didominasi oleh transaksi elektronik bernilai tinggi yang melonjak pada akhir tahun[cite: 504, 505, 506]. [cite_start]Melalui pengelompokan pelanggan ke dalam 4 profil klasifikasi (VIP, Loyal, Reguler, dan Pasif), manajemen kini memiliki visibilitas data-driven untuk mengalokasikan anggaran pemasaran secara efektif—memaksimalkan keuntungan dari pelanggan setia sekaligus memitigasi kerugian akibat *churn* pada pelanggan pasif[cite: 509, 510, 511, 512, 513].
