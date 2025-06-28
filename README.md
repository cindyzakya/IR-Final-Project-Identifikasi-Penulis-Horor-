# 🧠 IR Final Project – Identifikasi Penulis Teks Horor
Proyek ini merupakan tugas akhir mata kuliah *Information Retrieval* tahun 2025, yang bertujuan untuk **mengidentifikasi penulis dari teks-teks horor** berdasarkan karakteristik gaya penulisan. Dataset yang digunakan berisi teks karya tiga penulis terkenal: **EAP (Edgar Allan Poe), HPL (H. P. Lovecraft), dan MWS (Mary Shelley)** yang diambil dari _platform_ Kaggle.

---

## 📌 Tujuan
- Mengklasifikasikan teks berdasarkan penulisnya menggunakan metode pembelajaran mesin.
- Mengevaluasi performa model dengan metrik **log loss** dan **confusion matrix**.
- Menelusuri kekhasan gaya bahasa melalui fitur statistik, TF-IDF, dan n-gram karakter.

---

## 📁 Struktur Proyek
```
IR-Final-Project-Identifikasi-Penulis-Horor/
├── train.csv
├── test.csv
├── sample_submission.csv
├── IR_Final_Project_(XG_Boost_+_Multinomial_Naive_Bayes).ipynb
└── sub_fe.csv  # hasil prediksi akhir
```

---

## ⚙️ Alur dan Teknik yang Digunakan
### 1. Eksplorasi Data
- Melihat distribusi label (`EAP`, `HPL`, `MWS`)
- Visualisasi distribusi jumlah kata dan tanda baca
- Contoh sampel teks dari setiap penulis
### 2. Feature Engineering
- Fitur statistik:
  - `num_words`
  - `num_chars`
  - `num_stopwords`
  - `mean_word_len`
  - `num_punctuations`
- Ekstraksi fitur teks:
  - **TF-IDF** (word-level dan char-level, n-gram hingga 5)
  - **Count Vectorizer** (n-gram hingga 7)
  - **TruncatedSVD** (reduksi dimensi)
### 3. Modeling
- Model:
  - ✅ **XGBoost Classifier** (multi-class)
  - ✅ **Multinomial Naive Bayes**
- Validasi:
  - **5-Fold Cross Validation**
- Evaluasi:
  - Log Loss
  - Confusion Matrix
  - Feature Importance (XGBoost)

---

## 🔬 Hasil Model

| Model             | Fitur                             | Mean Log Loss  |
|-------------------|-----------------------------------|----------------|
| XGBoost (Baseline)| Meta                              | 1.025          |
| Naive Bayes       | TF-IDF (word-level n-gram)        | 0.842          |
| Naive Bayes       | Count Vectorizer (word n-gram)    | 0.4509         |
| Naive Bayes       | TF-IDF (char-level n-gram)        | 0.7904         |
| Naive Bayes       | Count Vectorizer (char n-gram)    | 3.853          |
| XGBoost           | Statistik + TF-IDF + char n-gram  | **0.3098**         |

---

## 🚀 Cara Menjalankan
1. Upload file `train.csv`, `test.csv`, dan `sample_submission.csv` ke Google Drive.
2. Buka `IR-Author-Classifier.ipynb` di Google Colab.
3. Jalankan sel secara berurutan.
4. File prediksi akhir akan tersimpan sebagai `sub_fe.csv`.

---

## 📤 Output
File `sub_fe.csv` berisi hasil prediksi probabilitas dari tiap penulis:
| id       | EAP     | HPL     | MWS     |
|----------|---------|---------|---------|
| id12345  | 0.65    | 0.25    | 0.10    |
| id23456  | 0.12    | 0.73    | 0.15    |
| ...      | ...     | ...     | ...     |

---

## 📝 Lisensi
Proyek ini dibuat untuk tujuan akademik. Dataset berasal dari sumber terbuka (Kaggle) dan digunakan hanya untuk keperluan pembelajaran.

---

## 📧 Kontak
Email: cindyzakya@gmail.com
