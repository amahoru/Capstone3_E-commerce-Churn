# Capstone3_E-commerce-Churn

1. Latar Belakang (Background)
Dalam industri E-Commerce yang sangat kompetitif, biaya untuk mengakuisisi pelanggan baru (Customer Acquisition Cost / CAC) diperkirakan 5 hingga 25 kali lebih mahal dibandingkan dengan mempertahankan pelanggan yang sudah ada. Ketika seorang pelanggan berhenti melakukan transaksi atau berpindah ke platform pesaing (Customer Churn), perusahaan tidak hanya kehilangan pelanggan tersebut, tetapi juga kehilangan potensi pendapatan jangka panjang mereka (Customer Lifetime Value / CLV).

Selama ini, tim marketing berupaya mencegah churn dengan membagikan insentif berupa voucher promosi (diskon/cashback) secara massal atau acak. Strategi blind marketing ini menimbulkan dua masalah besar:

Pemborosan Anggaran (Waste of Budget): Voucher diberikan kepada pelanggan yang sebenarnya sudah loyal.

Kehilangan Pendapatan (Loss of Revenue): Pelanggan yang benar-benar berniat kabur justru terlewat dari radar dan gagal diselamatkan.

Oleh karena itu, perusahaan membutuhkan pendekatan berbasis data untuk mengidentifikasi pelanggan yang berisiko tinggi untuk churn agar alokasi anggaran promosi bisa dilakukan secara presisi dan tepat sasaran.

2. Tujuan (Objectives)
Proyek Data Science ini dijalankan dengan tiga tujuan utama:

Menganalisis Pola Pelanggan: Mengidentifikasi karakteristik, perilaku, dan faktor utama yang mendorong seorang pelanggan E-Commerce untuk churn berdasarkan data historis.

Membangun Model Prediktif: Mengembangkan model Machine Learning klasifikasi yang mampu memprediksi probabilitas churn pelanggan di masa depan dengan tingkat Recall yang tinggi (meminimalisir kegagalan deteksi pelanggan yang berniat kabur).

Memaksimalkan Profitabilitas Bisnis: Mengoptimalkan ambang batas (threshold) dari model prediksi untuk menghasilkan strategi pembagian voucher yang memberikan Keuntungan Bersih (Net Benefit) tertinggi bagi perusahaan.

3. Pemahaman Data (Data Understanding)
Dataset yang digunakan berisi profil demografis dan histori interaksi pelanggan E-Commerce. Variabel target yang digunakan adalah Churn, dengan kelas 1 (Pelanggan kabur) dan 0 (Pelanggan tetap bertahan/setia).

Beberapa atribut (fitur) penting di dalam data ini meliputi:

Tenure: Lama waktu berlangganan (dalam bulan).

Complain: Status apakah pelanggan pernah mengajukan komplain atau keluhan.

Prefered Order Category: Kategori produk yang paling sering dibeli (misal: Mobile Phone, Laptop & Accessory, dll).

Cashback Amount: Rata-rata nominal cashback yang diterima pelanggan.

Warehouse to Home: Jarak fisik dari gudang pengiriman ke alamat pelanggan.

Data ini dievaluasi secara finansial menggunakan asumsi Cost & Benefit, di mana biaya voucher retensi diasumsikan sebesar $5, sedangkan nilai pelanggan (CLV) yang melayang jika terjadi churn adalah $50.

4. Analisis Data Eksploratif (Exploratory Data Analysis - EDA)
Dari tahapan eksplorasi data, ditemukan beberapa wawasan bisnis (Business Insights) yang krusial:

Fase Kritis Onboarding: Tingkat churn meroket tajam pada pelanggan dengan Tenure di bawah 6 bulan. Hal ini menunjukkan bahwa bulan-bulan pertama adalah masa yang paling rentan bagi pelanggan baru.

Efek Fatal Komplain: Pelanggan yang memiliki riwayat pernah mengajukan komplain memiliki persentase kemungkinan churn yang jauh lebih tinggi dibandingkan yang tidak. Ini menandakan sensitivitas layanan (Customer Experience).

Kategori Rawan: Pelanggan yang mayoritas berbelanja di kategori Mobile Phone merupakan segmentasi dengan loyalitas paling rendah (Churn Rate tertinggi).

5. Pemodelan Machine Learning (Modeling)
Tahapan pemodelan dilakukan melalui alur yang komprehensif (Pipeline siap deploy):

Preprocessing: Meliputi penanganan missing values menggunakan median, perbaikan inkonsistensi teks, scaling data numerik, dan encoding data kategorikal. Mengingat proporsi kelas target tidak seimbang (Imbalanced Data), teknik SMOTE diaplikasikan pada data latih.

Algoritma Model: Dilakukan benchmarking pada berbagai algoritma (Logistic Regression, Decision Tree, Random Forest, XGBoost, dan KNN). Algoritma K-Nearest Neighbors (KNN) terpilih sebagai Champion Model karena menghasilkan metrik Recall terbaik, yang kemudian ditingkatkan lagi melalui proses Hyperparameter Tuning.

Threshold Optimization: Alih-alih menggunakan ambang batas tebakan bawaan (50%), model dioptimasi secara matematis untuk mencari threshold probabilitas yang memberikan Net Benefit (uang yang diselamatkan dikurangi biaya voucher) paling besar.

Interpretability: Menggunakan SHAP (SHapley Additive exPlanations) untuk membedah Black Box model, sehingga tim bisnis dapat mengetahui persis mengapa seorang pelanggan diprediksi akan kabur (misalnya karena Tenure rendah dikombinasikan dengan riwayat komplain).
