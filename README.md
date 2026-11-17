# Preprocessing Teks Ulasan E-Commerce Berbahasa Indonesia untuk Analisis Sentimen

Proyek tugas Natural Language Processing (NLP) untuk melakukan tahapan preprocessing data teks ulasan produk e-commerce berbahasa Indonesia dari Hugging Face (`dipawidia/ecommerce-product-reviews-sentiment`).

---

## 👤 Identitas Mahasiswa
- **Nama** : [ROJA HUBBIL KHAIRI]
- **NIM**  : [24146036]
- **Mata Kuliah** : Natural Language Processing (NLP)
- **Dataset** : [Hugging Face - dipawidia/ecommerce-product-reviews-sentiment](https://huggingface.co/datasets/dipawidia/ecommerce-product-reviews-sentiment)

---

## 📌 Ringkasan Tugas
1. Menggunakan dataset ulasan e-commerce berbahasa Indonesia dari Hugging Face.
2. Menampilkan informasi dataset, meliputi jumlah data (11.606 ulasan), kolom (`review`, `sentimen`, `translate`), dan distribusi label sentimen (50% positif, 50% negatif).
3. Melakukan tahapan preprocessing teks:
   - **Case folding**: Mengubah teks menjadi huruf kecil (*lowercase*).
   - **Cleaning**: Menghapus URL, angka, tanda baca, simbol emotikon, dan karakter khusus.
   - **Tokenisasi**: Memecah kalimat menjadi satuan token kata.
   - **Stopword removal**: Menghapus kata-kata umum yang tidak penting (dengan preservasi kata negasi penting).
   - **Stemming**: Mengubah kata berimbuhan menjadi bentuk dasar menggunakan pustaka **Sastrawi**.
4. Menampilkan 10 contoh teks sebelum dan sesudah preprocessing dalam bentuk tabel perbandingan.
5. Menjelaskan secara singkat dan komprehensif pengaruh preprocessing terhadap kualitas data teks.

---

## 📂 Struktur Repositori
```
.
├── preprocessing_ulasan_ecommerce.ipynb   # Jupyter Notebook utama (lengkap dengan kode, visualisasi, dan hasil eksekusi)
├── requirements.txt                       # Daftar dependensi library Python
├── .gitignore                             # Konfigurasi file yang diabaikan Git
└── README.md                              # Dokumentasi repositori & identitas
```

---

## 🚀 Panduan Menjalankan Notebook

### 1. Clone Repositori
```bash
git clone <https://github.com/rojahbbil/ecommerce-sentiment-preprocessing.git>
cd <ecommerce-sentiment-preprocessing
>
```

### 2. Buat & Aktifkan Virtual Environment (Opsional)
```bash
# Windows
python -m venv venv
.\venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependensi
```bash
pip install -r requirements.txt
```

### 4. Jalankan Jupyter Notebook / Jupyter Lab
```bash
jupyter notebook preprocessing_ulasan_ecommerce.ipynb
# atau
jupyter lab
```

---

## 📊 Hasil Analisis Statistik Preprocessing

| Indikator Metrik | Sebelum Preprocessing | Sesudah Preprocessing | Penurunan / Efisiensi (%) |
| :--- | :---: | :---: | :---: |
| **Total Baris Data** | 11.606 | 11.606 | 0.0% (Utuh) |
| **Distribusi Label** | 50% Positif / 50% Negatif | 50% Positif / 50% Negatif | Seimbang (*Balanced*) |
| **Rata-rata Panjang Karakter** | 103,57 | 67,40 | 34,9% |
| **Median Panjang Karakter** | 78,0 | 52,0 | 33,3% |
| **Rata-rata Jumlah Kata** | 15,76 kata | 11,08 kata | 29,7% |
| **Median Jumlah Kata** | 12,0 kata | 9,0 kata | 25,0% |
| **Maksimum Jumlah Kata** | 235 kata | 127 kata | 46,0% |
| **Ukuran Kosakata (Vocabulary)** | 23.371 kata | 10.040 kata | **57,0%** |

**Catatan kualitas:** setelah preprocessing, terdapat **18 ulasan yang menjadi kosong** (0,16%) dan **758 ulasan dengan ≤ 2 token** (6,53%). Kedua hal ini perlu diperhatikan pada tahap pemodelan dan dilaporkan sebagai keterbatasan.

---

## 💡 Ringkasan Pengaruh Preprocessing terhadap Kualitas Teks
1. **Reduksi Noise & Dimensionalitas**: Tanda baca, angka, karakter khusus, dan stopword berhasil dieliminasi. Ukuran kosakata menyusut sebesar **57,0%** (dari 23.371 menjadi 10.040 kata dasar unik), yang secara signifikan memadatkan matriks fitur (TF-IDF/Bag-of-Words) dan mempercepat komputasi.
2. **Standardisasi Morfologis**: Stemming Sastrawi menyatukan ragam kata turunan berafiks (*pengiriman*, *dikirim*, *kirimkan* $\rightarrow$ *kirim*) ke dalam satu token dasar.
3. **Preservasi Sentimen**: Kata-kata negasi krusial (*tidak, bukan, kurang, belum, gak*) diproteksi dari penghapusan stopword agar polaritas emosional kalimat ulasan tidak berbalik.
