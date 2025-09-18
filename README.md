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
![survive](https://github.com/c14250130-ui/Exploratory-Data-Analysis-EDA---Titanic-Dataset/blob/main/Screenshot%202025-09-18%20115751.png)

---

### 2. `deck_known` vs `pclass`
- Penumpang **kelas 1** dan **kelas 2** lebih banyak memiliki `deck_known = 1`.  
- Penumpang **kelas 3** mayoritas `deck_known = 0`.  
- Artinya, `deck_known` bisa menjadi indikator **sosial-ekonomi** yang mirip dengan `pclass`.

📊 **Visualisasi**  
![pclass](https://github.com/c14250130-ui/Exploratory-Data-Analysis-EDA---Titanic-Dataset/blob/main/Screenshot%202025-09-18%20115805.png)

---

### 3. `deck_known` vs `fare`
- Penumpang dengan `deck_known = 1` cenderung membayar **fare (tarif tiket) lebih mahal**.  
- Hal ini sejalan dengan logika bahwa kelas atas (lebih mahal) tercatat lebih lengkap, termasuk informasi dek.

📊 **Visualisasi**  
![fare](https://github.com/c14250130-ui/Exploratory-Data-Analysis-EDA---Titanic-Dataset/blob/main/Screenshot%202025-09-18%20115822.png)

---

## 📊 Kesimpulan
- Variabel baru **`deck_known`** adalah cara sederhana namun efektif untuk memanfaatkan informasi kolom `deck` yang banyak missing values.  
- Analisis menunjukkan:
  - `deck_known` berhubungan positif dengan **survival**.  
  - `deck_known` berkorelasi dengan variabel **pclass** dan **fare**, karena kelas atas lebih banyak memiliki deck yang tercatat.  
- Dengan demikian, **`deck_known` dapat menjadi prediktor tambahan** yang relevan untuk memodelkan peluang keselamatan penumpang Titanic.

---

## 📂 Catatan
- FILE RAW = https://colab.research.google.com/drive/1-8XgpdgzRZ3yL4nKs0G46cTKtPL1TybI#scrollTo=btn0BuO-Fcus
- FILE HASIL IMPROVE DAN MODIFIKASI = https://colab.research.google.com/drive/1hNbRPk2X7ZBWXGnChskCq88-ir9wGDVD?usp=sharing
