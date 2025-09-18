# 🛳️ Exploratory Data Analysis (EDA) - Titanic Dataset

## 📌 Latar Belakang
Dataset **Titanic** adalah salah satu dataset paling populer untuk pembelajaran analisis data dan machine learning.  
Dataset ini berisi informasi tentang penumpang Titanic, termasuk usia, jenis kelamin, kelas, tarif tiket, serta apakah penumpang tersebut selamat atau tidak.

Analisis ini bertujuan untuk memahami pola data, missing values, distribusi variabel, serta faktor-faktor yang memengaruhi kemungkinan penumpang untuk selamat.

---

## 📂 Langkah Analisis

### 1. Import Library dan Load Dataset
- Digunakan library: **Pandas, Numpy, Matplotlib, Seaborn**
- Dataset Titanic dimuat langsung dari **Seaborn** (`sns.load_dataset('titanic')`).

### 2. Data Preparation
- Membuat variabel baru `sex_numeric`:  
  - `male = 1`  
  - `female = 0`  

- Membuat variabel baru `deck_known`:  
  - `1 = informasi deck tersedia`  
  - `0 = informasi deck tidak tersedia`

### 3. Informasi Dataset
- Dataset terdiri dari **891 baris** dan **15 kolom** (sebelum penambahan variabel baru).
- Terdapat missing values pada beberapa kolom, terutama:
  - `age`
  - `deck`
  - `embark_town`

### 4. Analisis Missing Values
- Missing values divisualisasikan dengan **heatmap**.
- Kolom `deck` memiliki missing values terbanyak.

### 5. Analisis Variabel Kategorik
- Distribusi penumpang berdasarkan **jenis kelamin**: mayoritas adalah laki-laki.
- Distribusi **survival** menunjukkan lebih banyak penumpang yang **tidak selamat**.
- Distribusi berdasarkan **kelas (pclass)**: kelas 3 paling banyak.

### 6. Analisis Variabel Numerik
- **Usia (age)** berdistribusi dengan puncak pada usia muda hingga dewasa.
- **Boxplot age vs pclass**: penumpang kelas 1 cenderung lebih tua dibanding kelas 3.
- **Fare (tarif)** memiliki banyak outlier (beberapa tiket sangat mahal).

### 7. Analisis Korelasi
- Korelasi antar variabel numerik divisualisasikan dengan **heatmap**.
- `fare` berkorelasi negatif dengan `pclass` → semakin tinggi kelas, semakin mahal tarif tiket.
- `sex_numeric` berkorelasi dengan `survived` → perempuan lebih banyak selamat.

### 8. Analisis Hubungan Antar Variabel
- **Scatter plot age vs fare** menunjukkan sebagian besar penumpang dengan tarif mahal berada di kelas lebih tinggi.
- **Pairplot** memperlihatkan hubungan antar `age`, `fare`, dan `pclass` dengan label `survived`.

### 9. Variabel Baru: `deck_known`
- Penambahan variabel baru `deck_known` (1 jika deck diketahui, 0 jika tidak).
- Hasil analisis:
  - Penumpang dengan **deck diketahui** memiliki survival rate lebih tinggi.  
  - Hal ini masuk akal karena penumpang dengan informasi deck biasanya berasal dari kelas 1 atau 2 (kelas atas).

---

## 📊 Kesimpulan Sementara
- **Jenis kelamin** berpengaruh besar terhadap survival → perempuan lebih banyak selamat.  
- **Kelas penumpang** berhubungan dengan survival → kelas 1 lebih tinggi peluang selamatnya dibanding kelas 3.  
- **Variabel baru `deck_known`** memberikan insight tambahan → penumpang dengan deck diketahui (kelas lebih tinggi) cenderung lebih banyak selamat.  
- Missing values cukup signifikan, terutama pada kolom `deck` dan `age`, sehingga perlu penanganan sebelum digunakan untuk modeling machine learning.

---

## 📌 Catatan
Analisis ini masih bersifat eksploratif.  
Tahap selanjutnya bisa berupa:
- **Data preprocessing lebih lanjut** (imputasi missing values, encoding variabel kategorik).
- **Modeling machine learning** untuk memprediksi `survived`.
