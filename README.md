# Analisis Sentimen Ulasan Produk Pembersih Toilet

Proyek ini bertujuan untuk menganalisis sentimen konsumen terhadap produk pembersih toilet berdasarkan data ulasan (*review*). Menggunakan teknik *Natural Language Processing* (NLP) untuk pengolahan teks dan visualisasi data, proyek ini memisahkan serta memetakan persepsi pelanggan ke dalam kategori **Sentimen Positif** dan **Sentimen Negatif**.

## 📌 1. Ringkasan Proyek

* **Dataset:** Data ulasan konsumen produk pembersih toilet (`review_pembersih_toilet.xlsx`).
* **Pendekatan NLP:** Menghapus duplikasi, pembersihan teks (emoji, angka, simbol), *Case Folding*, Normalisasi Kata (Kamus Kata Baku), Tokenisasi, *Stopword Removal* (NLTK), dan *Stemming* (Sastrawi).
* **Kriteria Pelabelan Sentimen:**
  * **Positive:** Bintang 4 dan 5 (`star_level >= 4`)
  * **Negative:** Bintang 1, 2, dan 3 (`star_level < 4`)
* **Visualisasi:** *WordCloud* per kelas sentimen, Grafik Frekuensi Kata (*Top 20 Words*), dan Distribusi Sentimen.

## 🛠️ 2. Tahapan Alur Kerja (Pipeline Data)

### 📊 A. Data Preprocessing & Cleaning
1. **Deduplikasi:** Menghapus baris duplikat berdasarkan kombinasi `user_name` dan `review_text`.
2. **Text Cleaning:** 
   * Menghapus emoji menggunakan pustaka `emoji`.
   * Menghapus karakter khusus, simbol, dan angka menggunakan *Regular Expression* (`re`).
   * Memperbaiki format spasi setelah tanda koma.
3. **Case Folding:** Mengubah seluruh teks menjadi huruf kecil (*lowercase*).
4. **Word Normalization:** Mengganti kata-kata tidak baku/singkatan menjadi kata standar berbasis kamus eksternal (`kamuskatabaku.xlsx`).

### ✂️ B. Text Processing (NLP)
1. **Tokenization:** Memecah string kalimat menjadi daftar kata (*list of tokens*).
2. **Stopword Removal:** Menghapus kata hubung/umum dalam bahasa Indonesia menggunakan pustaka `NLTK`.
3. **Stemming:** Mengubah kata berimbuhan menjadi kata dasar menggunakan pustaka `Sastrawi`.

### 🏷️ C. Pelabelan Sentimen
Mengklasifikasikan data berdasarkan nilai `star_level` ke dalam dua kelas sentimen: `positive` dan `negative`.

## 📈 3. Hasil & Visualisasi Utama

1. **WordCloud Sentimen Negatif:** Memvisualisasikan kata-kata yang paling sering muncul pada ulasan buruk/keluhan pelanggan.
2. **WordCloud Sentimen Positif:** Memvisualisasikan kata-kata yang merepresentasikan kepuasan pelanggan terhadap produk.
3. **Top 20 Kata Sering Muncul:** Histogram frekuensi 20 kata teratas untuk masing-masing kategori sentimen guna mengidentifikasi topik keluhan maupun keunggulan produk secara spesifik.
4. **Distribusi Sentimen:** Bar plot interaktif (menggunakan `Plotly`) yang menunjukkan perbandingan jumlah ulasan positif dan negatif.
