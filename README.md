# 🛳️ Exploratory Data Analysis (EDA) Titanic - Penambahan Variabel Baru `deck_known`

## 📌 Latar Belakang
Dataset **Titanic** menyediakan informasi tentang penumpang kapal Titanic, seperti usia, jenis kelamin, kelas, tarif, dan status keselamatan (survived).  
Namun, dataset ini juga memiliki kolom `deck` yang banyak mengandung **missing values**.  
Untuk memanfaatkan informasi ini, ditambahkan variabel baru bernama **`deck_known`**.

---

## 🆕 Variabel Baru: `deck_known`

### Definisi
- **`deck_known`** adalah variabel biner (0 atau 1) yang menunjukkan apakah informasi dek tempat penumpang berada **diketahui** atau **tidak**.  
- **Nilai variabel:**
  - `1` → deck diketahui  
  - `0` → deck tidak diketahui  

### Alasan Penambahan
- Kolom `deck` memiliki banyak missing values, sehingga sulit digunakan langsung dalam analisis.  
- Dengan mengubahnya menjadi variabel boolean (`deck_known`), kita dapat:
  - Mengukur **kualitas data** (apakah informasi deck tersedia).  
  - Menghubungkan informasi keberadaan dek dengan **kelas penumpang** dan **peluang selamat (survival rate)**.  
- Hipotesis: Penumpang dengan **deck diketahui** kemungkinan besar berasal dari **kelas lebih tinggi (1 atau 2)**, sehingga berpeluang lebih besar untuk selamat.

---

## 🔎 Analisis `deck_known` dengan Variabel Lain

### 1. `deck_known` vs `survived`
- Penumpang dengan **deck diketahui (1)** memiliki **survival rate lebih tinggi** dibanding penumpang dengan **deck tidak diketahui (0)**.  
- Hal ini konsisten dengan sejarah Titanic, di mana penumpang kelas atas ditempatkan di dek atas dan lebih dulu dievakuasi.

📊 **Visualisasi**  
*(tempat untuk barplot `deck_known` vs `survived`)*

---

### 2. `deck_known` vs `pclass`
- Penumpang **kelas 1** dan **kelas 2** lebih banyak memiliki `deck_known = 1`.  
- Penumpang **kelas 3** mayoritas `deck_known = 0`.  
- Artinya, `deck_known` bisa menjadi indikator **sosial-ekonomi** yang mirip dengan `pclass`.

📊 **Visualisasi**  
*(tempat untuk countplot / crosstab heatmap `deck_known` vs `pclass`)*

---

### 3. `deck_known` vs `fare`
- Penumpang dengan `deck_known = 1` cenderung membayar **fare (tarif tiket) lebih mahal**.  
- Hal ini sejalan dengan logika bahwa kelas atas (lebih mahal) tercatat lebih lengkap, termasuk informasi dek.

📊 **Visualisasi**  
*(tempat untuk boxplot / violin plot `fare` berdasarkan `deck_known`)*

---

## 📊 Kesimpulan
- Variabel baru **`deck_known`** adalah cara sederhana namun efektif untuk memanfaatkan informasi kolom `deck` yang banyak missing values.  
- Analisis menunjukkan:
  - `deck_known` berhubungan positif dengan **survival**.  
  - `deck_known` berkorelasi dengan variabel **pclass** dan **fare**, karena kelas atas lebih banyak memiliki deck yang tercatat.  
- Dengan demikian, **`deck_known` dapat menjadi prediktor tambahan** yang relevan untuk memodelkan peluang keselamatan penumpang Titanic.

---

## 🚀 Rekomendasi Lanjutan
- Gunakan `deck_known` sebagai salah satu variabel input dalam **model prediksi survival**.  
- Lakukan **uji korelasi numerik** (misalnya point-biserial correlation) antara `deck_known` dan variabel numerik (`fare`, `survived`).  
- Gabungkan dengan variabel lain seperti `sex`, `pclass`, dan `age` untuk membangun model machine learning yang lebih akurat.
