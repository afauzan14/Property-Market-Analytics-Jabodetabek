# 🏢 Jabodetabek Real Estate Market Analysis & Data Governance Audit

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=seaborn&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Real%20Estate%20Analytics-brightgreen?style=for-the-badge)

---

## 📌 Ringkasan Proyek & Business Understanding

**Real Property Prima Indonesia (RPPI)** adalah perusahaan agen properti yang beroperasi di wilayah aglomerasi Jabodetabek (Jakarta, Bogor, Depok, Tangerang, dan Bekasi). Untuk mempertahankan keunggulan kompetitif dan bertransformasi menjadi *data-driven company*, manajemen RPPI memerlukan wawasan mendalam mengenai dinamika pasar properti sekaligus mengevaluasi kualitas data internal yang dihimpun dari berbagai cabang.

Proyek ini bertujuan untuk menyelesaikan beberapa permasalahan strategis bisnis:
1. **Audit Kualitas Data:** Mengidentifikasi anomali, inkonsistensi penulisan satuan, missing values, dan memberikan rekomendasi teknis perbaikan ke tim *Data Engineer (DE)* dan *Database Administrator (DBA)*.
2. **Analisis Disparitas Harga Antar Wilayah:** Menganalisis sebaran harga properti lintas kota untuk memahami disparitas nilai dan faktor pendorong tingginya harga di pusat megapolitan.
3. **Rekomendasi Ekspansi Kantor Cabang:** Menentukan wilayah paling prospektif untuk pembukaan kantor cabang baru berbasis volume listing dan aktivitas pasar.
4. **Profil Hunian Terlaris:** Mengidentifikasi karakteristik properti (luas tanah, luas bangunan, fasilitas kamar tidur/mandi, daya listrik, dan arah hadap) yang paling banyak diserap oleh konsumen.
5. **Optimasi Portofolio Investasi Rp 25 Miliar:** Merumuskan strategi alokasi modal belanja properti untuk memaksimalkan potensi imbal hasil (*capital gain*) dan likuiditas dengan mitigasi risiko legalitas.

---

## 🔬 Metodologi Analisis & Data Cleansing

Dataset terdiri dari data listing properti mentah di 5 wilayah (Jakarta, Bogor, Depok, Tangerang, dan Bekasi) yang melalui tahapan integrasi dan pembersihan data terstruktur:

1. **Audit & Penyeragaman Satuan:** Menangani ketiadaan satuan baku pada data mentah (khususnya harga serta Luas Tanah/Bangunan di wilayah Depok dan Tangerang) serta mengonversi format nilai ke dalam standar mata uang Rupiah (`IDR`) dan satuan meter persegi (`m²`).
2. **Noise & Uninformative Feature Removal:** Menghapus kolom artifak tak berguna (seperti kolom `Unnamed`), baris kosong/duplikat akibat scraping/input manual, serta standardisasi label kategorik (sertifikat, arah hadap properti).
3. **Penanganan Missing Values & Outlier:** Imputasi nilai kosong pada variabel spesifikasi fisik dan pemisahan analisis *outlier* (lahan berskala > 3.000 m²) untuk segmen investasi khusus.
4. **Integrasi Data Multi-Wilayah (`dataGab`):** Menggabungkan seluruh data terstandarisasi ke dalam satu entitas data gabungan untuk perbandingan komparatif lintas kota menggunakan statistik deskriptif dan visualisasi distribusi (*Catplot, Barplot, Histplot, Swarmplot, Scatterplot*).

---

## 📊 Temuan Kunci (Key Findings)

### 1. Komparasi Pasar Properti Antar Kota Jabodetabek

| Kota | Karakteristik Sebaran Harga | Volume Listing | Potensi Pasar & Karakteristik Wilayah |
| :--- | :--- | :--- | :--- |
| **Jakarta** | Sangat variatif, dispersi harga tertinggi (hingga segmen ultra-luxury) | Menengah | Pusat bisnis dan ekonomi; didorong urbanisasi tinggi dan keterbatasan lahan ekstrem |
| **Bogor** | Terkonsentrasi di segmen terjangkau (< Rp 2 Miliar) | **Tertinggi** | Pasar residensial paling aktif; preferensi lingkungan nyaman dan hunian keluarga |
| **Tangerang** | Rentang harga menengah ke atas, variasi cukup tinggi | Tinggi | Aksesibilitas cepat ke pusat bisnis Jakarta; berkembang pesat untuk segmen *middle-up* |
| **Depok** | Dominasi segmen ramah anggaran (< Rp 2 Miliar) | Sedang | Area komuter dengan permintaan hunian tapak pertama (*first-time buyers*) yang kuat |
| **Bekasi** | Terkonsentrasi di segmen harga ekonomis/kompetitif | Menengah-Rendah | Kawasan industri dan residensial penyangga dengan perputaran harga stabil |

---

### 2. Profil Hunian yang Paling Banyak Diminati & Dijual

Berdasarkan analisis visualisasi distribusi data gabungan, karakteristik rumah yang mencatatkan serapan pasar tertinggi memiliki spesifikasi:

| Parameter Fisik | Karakteristik Paling Diminati | Interpretasi Bisnis |
| :--- | :--- | :--- |
| **Luas Bangunan (LB)** | `< 100 m²` | Rumah kompak/minimalis mendominasi; efisiensi biaya perawatan dan harga beli |
| **Luas Tanah (LT)** | `< 500 m²` (Mayoritas < 150 m²) | Preferensi hunian modern tapak kompak di kawasan urban-suburban |
| **Kamar Tidur (KT)** | 2 hingga 3 Kamar | Ideal untuk keluarga muda (nuklir) yang menjadi segmen pembeli mayoritas |
| **Kamar Mandi (KM)** | 2 hingga 4 Kamar | Standar kenyamanan harian tanpa memicu antrean fasilitas sanitasi |
| **Fasilitas Carport** | 1 Mobil | Kapasitas parkir standar untuk satu kendaraan roda empat pribadi |
| **Kapasitas Listrik** | `2.200 VA` s.d. `4.400 VA` | Rentang daya optimal untuk kebutuhan elektronik rumah tangga modern |
| **Arah Hadap** | **Menghadap Timur** | Mendapat pencahayaan alami matahari pagi dan menghindari panas terik sore hari |

---

## 💡 Rekomendasi Strategis & Bisnis

### 1. Tata Kelola Data (*Data Governance*) untuk Tim Data Engineer (DE) & Database Administrator (DBA)
* **Standardisasi Format Input:** Terapkan skema validasi ketat pada sistem pemasukan data (*entry form*) dengan satuan baku yang eksplisit (misal: Harga dalam juta Rupiah, LT/LB dalam m², Listrik dalam VA/Watt).
* **Eliminasi Anomali & Redundansi:** Hapus permanen kolom indeks artifak (`Unnamed`), sediakan validasi *regex* untuk kolom kategorik (arah hadap dan jenis sertifikat), serta bangun pipeline ETL terpusat agar data antar kantor cabang tidak memiliki schema drift.
* **Hierarki Lokasi Terstruktur:** Lakukan normalisasi basis data dengan mencatat lokasi bertingkat (Provinsi > Kota/Kabupaten > Kecamatan > Kelurahan) guna mempermudah analisis spasial mikro.

### 2. Ekspansi Kantor Cabang Baru
* **Prioritas Utama: Kota Bogor**
  * **Justifikasi Data:** Bogor mencatatkan volume listing properti tertinggi di antara seluruh wilayah Jabodetabek, menandakan perputaran pasar yang sangat likuid.
  * **Strategi Penetrasi:** Menempatkan kantor cabang di Bogor akan mendekatkan RPPI langsung ke ekosistem pemilik properti dan pembeli segmen *family-oriented*, memaksimalkan konversi komisi agen.

### 3. Alokasi Modal Investasi Rp 25 Miliar
* **Strategi Diversifikasi Multi-Unit (Likuiditas Tinggi):** Alokasikan modal utama untuk mengakuisisi unit rumah dengan harga < Rp 2 Miliar di koridor **Depok, Bogor, dan Bekasi**. Segmen ini memiliki pasar pembeli paling luas (*broadest target market*) sehingga risiko likuiditas saat *resale* jauh lebih rendah.
* **Prioritas Sertifikasi Legalitas SHM:** Fokuskan transaksi pada aset bersertifikat **Sertifikat Hak Milik (SHM)** atau paket **SHM + IMB/PBG + PBB** guna menjamin keamanan hak atas tanah dan mempermudah pembiayaan KPR bagi pembeli berikutnya.
* **Peluang Land Banking (Kavling Lahan Outlier):** Pertimbangkan alokasi selektif pada lahan luas (outlier > 3.000 m²) yang bernilai miring untuk dipecah (*split*) menjadi beberapa unit kavling siap bangun (*land subdivision*) demi menghasilkan margin *capital gain* berlipat.
