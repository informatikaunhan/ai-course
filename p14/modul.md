# Modul 14: Pembelajaran Mesin - Unsupervised Learning dan Reinforcement Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 14  
**Topik:** Pembelajaran Mesin - Unsupervised Learning dan Reinforcement Learning  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan motivasi dan aplikasi unsupervised learning
2. Mengimplementasikan algoritma K-Means clustering secara manual
3. Menjelaskan konsep hierarchical clustering dan dendrogramnya
4. Menerapkan metode evaluasi clustering (silhouette score, elbow method)
5. Menjelaskan konsep dasar dimensionality reduction dengan PCA
6. Menjelaskan komponen reinforcement learning (agent, environment, state, action, reward)
7. Memahami Markov Decision Process (MDP), policy, dan value function
8. Menerapkan algoritma Q-Learning pada permasalahan sederhana
9. Membandingkan tiga paradigma pembelajaran mesin dan mengidentifikasi aplikasi yang sesuai

---

## 1. Unsupervised Learning

### 1.1 Motivasi dan Konsep Dasar

> **Unsupervised Learning** adalah paradigma pembelajaran mesin di mana model belajar dari data yang **tidak memiliki label** (unlabeled data). Tujuannya adalah menemukan pola, struktur, atau pengelompokan tersembunyi dalam data.

Pada Pertemuan 13, kita telah mempelajari supervised learning di mana setiap data pelatihan memiliki label (jawaban yang benar). Dalam unsupervised learning, kita hanya memiliki data input tanpa mengetahui output yang diharapkan.

| Aspek | Supervised Learning | Unsupervised Learning |
|-------|--------------------|-----------------------|
| **Data** | Berlabel (x, y) | Tanpa label (x saja) |
| **Tujuan** | Memprediksi output | Menemukan struktur |
| **Evaluasi** | Langsung (bandingkan dengan label) | Tidak langsung (metrik internal) |
| **Contoh** | Klasifikasi, regresi | Clustering, dimensionality reduction |

**Aplikasi Unsupervised Learning:**
- **Clustering**: Pengelompokan pelanggan, segmentasi citra, deteksi anomali
- **Dimensionality Reduction**: Kompresi data, visualisasi data dimensi tinggi
- **Association Rules**: Market basket analysis, rekomendasi
- **Density Estimation**: Estimasi distribusi data

#### Solved Problem 1 ⭐

**Soal:** Sebuah unit intelijen militer memiliki dataset berisi 1000 sinyal komunikasi yang terintersepsi. Setiap sinyal memiliki fitur: frekuensi, durasi, bandwidth, dan waktu transmisi. Tidak ada label yang menunjukkan jenis sinyal. Paradigma pembelajaran mesin mana yang tepat digunakan? Jelaskan!

**Penyelesaian:**

*Step 1:* Identifikasi karakteristik data
- Data: 1000 sinyal komunikasi
- Fitur: frekuensi, durasi, bandwidth, waktu transmisi
- Label: **Tidak ada**

*Step 2:* Tentukan paradigma yang sesuai
- Karena tidak ada label → bukan supervised learning
- Tujuan: menemukan pola/kelompok sinyal → unsupervised learning

*Step 3:* Tentukan teknik spesifik
- Clustering dapat mengelompokkan sinyal berdasarkan kemiripan fitur
- Kelompok yang ditemukan mungkin merepresentasikan jenis komunikasi berbeda (misalnya: komunikasi taktis, logistik, komando)

**Jawaban:** Paradigma yang tepat adalah **Unsupervised Learning** dengan teknik **clustering**, karena data tidak memiliki label dan tujuannya adalah menemukan pengelompokan alami dalam data sinyal.

---

### 1.2 Clustering

> **Clustering** adalah teknik unsupervised learning yang bertujuan mengelompokkan data ke dalam **klaster (cluster)** sedemikian rupa sehingga data dalam satu klaster lebih mirip satu sama lain dibandingkan dengan data di klaster lain.

Prinsip dasar clustering:
- **Intra-cluster similarity**: Tinggi (data dalam klaster mirip)
- **Inter-cluster similarity**: Rendah (data antar klaster berbeda)

#### Solved Problem 2 ⭐

**Soal:** Diberikan data 2D berikut. Secara intuitif, berapa banyak klaster yang terdapat dalam data ini?

| Titik | x | y |
|-------|---|---|
| P1 | 1 | 2 |
| P2 | 2 | 1 |
| P3 | 1.5 | 1.5 |
| P4 | 8 | 8 |
| P5 | 9 | 7 |
| P6 | 8.5 | 8.5 |

**Penyelesaian:**

*Step 1:* Amati distribusi data
- P1(1,2), P2(2,1), P3(1.5,1.5) → terkonsentrasi di sekitar (1.5, 1.5)
- P4(8,8), P5(9,7), P6(8.5,8.5) → terkonsentrasi di sekitar (8.5, 7.8)

*Step 2:* Identifikasi kelompok alami
- Kelompok 1: {P1, P2, P3} — kiri bawah
- Kelompok 2: {P4, P5, P6} — kanan atas
- Jarak antar kelompok >> jarak dalam kelompok

**Jawaban:** Terdapat **2 klaster** yang terlihat jelas: {P1, P2, P3} di area (1-2, 1-2) dan {P4, P5, P6} di area (8-9, 7-8.5).

---

## 2. Algoritma K-Means Clustering

### 2.1 Konsep K-Means

> **K-Means** adalah algoritma clustering yang mempartisi n data ke dalam K klaster, di mana setiap data ditetapkan ke klaster dengan **centroid** (rata-rata) terdekat.

![Algoritma K-Means](images/p14-01-k-means-algorithm.png)

*Gambar 14.1: Alur algoritma K-Means clustering*

**Algoritma K-Means:**

```
Input: Dataset X = {x₁, x₂, ..., xₙ}, jumlah klaster K
Output: K klaster dan K centroid

1. Inisialisasi: Pilih K centroid awal secara acak (μ₁, μ₂, ..., μₖ)
2. REPEAT:
   a. Assignment Step: Untuk setiap xᵢ, tetapkan ke klaster terdekat
      cᵢ = arg min‖xᵢ - μⱼ‖²   (j = 1, ..., K)
   b. Update Step: Perbarui centroid setiap klaster
      μⱼ = (1/|Cⱼ|) Σ xᵢ   (untuk semua xᵢ ∈ Cⱼ)
3. UNTIL centroid tidak berubah (konvergen)
```

**Jarak Euclidean** digunakan untuk mengukur kedekatan:

$$d(x, y) = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2}$$

#### Solved Problem 3 ⭐

**Soal:** Hitung jarak Euclidean antara titik A(2, 3) dan B(5, 7)!

**Penyelesaian:**

*Step 1:* Terapkan rumus jarak Euclidean

$$d(A, B) = \sqrt{(5-2)^2 + (7-3)^2}$$

*Step 2:* Hitung

$$d(A, B) = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5$$

**Jawaban:** Jarak Euclidean antara A(2,3) dan B(5,7) adalah **5**.

---

#### Solved Problem 4 ⭐⭐

**Soal:** Lakukan satu iterasi K-Means (K=2) pada data berikut dengan centroid awal μ₁=(1,1) dan μ₂=(5,5)!

| Titik | x | y |
|-------|---|---|
| A | 1 | 2 |
| B | 2 | 1 |
| C | 4 | 5 |
| D | 5 | 4 |
| E | 3 | 3 |

**Penyelesaian:**

*Step 1:* Hitung jarak setiap titik ke kedua centroid

| Titik | d(titik, μ₁) | d(titik, μ₂) | Klaster |
|-------|-------------|-------------|---------|
| A(1,2) | √((1-1)²+(2-1)²) = √1 = **1.00** | √((1-5)²+(2-5)²) = √25 = **5.00** | C₁ |
| B(2,1) | √((2-1)²+(1-1)²) = √1 = **1.00** | √((2-5)²+(1-5)²) = √25 = **5.00** | C₁ |
| C(4,5) | √((4-1)²+(5-1)²) = √25 = **5.00** | √((4-5)²+(5-5)²) = √1 = **1.00** | C₂ |
| D(5,4) | √((5-1)²+(4-1)²) = √25 = **5.00** | √((5-5)²+(4-5)²) = √1 = **1.00** | C₂ |
| E(3,3) | √((3-1)²+(3-1)²) = √8 = **2.83** | √((3-5)²+(3-5)²) = √8 = **2.83** | C₁ (tie, pilih C₁) |

*Step 2:* Tentukan anggota klaster
- C₁ = {A(1,2), B(2,1), E(3,3)}
- C₂ = {C(4,5), D(5,4)}

*Step 3:* Perbarui centroid

$$\mu_1^{new} = \left(\frac{1+2+3}{3}, \frac{2+1+3}{3}\right) = (2.0, 2.0)$$

$$\mu_2^{new} = \left(\frac{4+5}{2}, \frac{5+4}{2}\right) = (4.5, 4.5)$$

**Jawaban:** Setelah 1 iterasi: C₁ = {A, B, E} dengan centroid (2.0, 2.0), C₂ = {C, D} dengan centroid (4.5, 4.5).

---

#### Solved Problem 5 ⭐⭐

**Soal:** Lanjutkan Solved Problem 4 untuk iterasi kedua. Apakah algoritma sudah konvergen?

**Penyelesaian:**

*Step 1:* Gunakan centroid baru: μ₁=(2.0, 2.0) dan μ₂=(4.5, 4.5)

*Step 2:* Hitung jarak dan tetapkan klaster

| Titik | d(titik, μ₁) | d(titik, μ₂) | Klaster |
|-------|-------------|-------------|---------|
| A(1,2) | √(1+0) = **1.00** | √(12.25+6.25) = **4.30** | C₁ |
| B(2,1) | √(0+1) = **1.00** | √(6.25+12.25) = **4.30** | C₁ |
| C(4,5) | √(4+9) = **3.61** | √(0.25+0.25) = **0.71** | C₂ |
| D(5,4) | √(9+4) = **3.61** | √(0.25+0.25) = **0.71** | C₂ |
| E(3,3) | √(1+1) = **1.41** | √(2.25+2.25) = **2.12** | C₁ |

*Step 3:* Klaster tetap sama: C₁ = {A, B, E}, C₂ = {C, D}

*Step 4:* Perbarui centroid
- μ₁ = (2.0, 2.0) — sama seperti sebelumnya
- μ₂ = (4.5, 4.5) — sama seperti sebelumnya

**Jawaban:** Algoritma sudah **konvergen** karena centroid tidak berubah dan assignment klaster tetap sama.

---

### 2.2 Karakteristik K-Means

**Kelebihan K-Means:**
- Sederhana dan mudah diimplementasikan
- Efisien untuk dataset besar: O(n × K × t × d), di mana t = jumlah iterasi, d = dimensi
- Selalu konvergen

**Kelemahan K-Means:**
- Harus menentukan K di awal
- Sensitif terhadap inisialisasi centroid awal
- Hanya menghasilkan klaster berbentuk bulat (spherical)
- Sensitif terhadap outlier
- Konvergen ke local optimum, bukan global optimum

#### Solved Problem 6 ⭐

**Soal:** Jelaskan mengapa K-Means sensitif terhadap inisialisasi centroid awal!

**Penyelesaian:**

*Step 1:* K-Means adalah algoritma yang mencari **local minimum** dari fungsi objektif:

$$J = \sum_{j=1}^{K}\sum_{x_i \in C_j} \|x_i - \mu_j\|^2$$

*Step 2:* Inisialisasi yang berbeda menghasilkan local minimum yang berbeda.

*Step 3:* Contoh: Jika centroid awal kebetulan terlalu dekat, dua klaster alami bisa bergabung, menghasilkan hasil yang buruk.

**Jawaban:** K-Means sensitif terhadap inisialisasi karena algoritma ini hanya menjamin konvergensi ke **local optimum**, bukan global optimum. Centroid awal yang berbeda dapat menghasilkan klaster akhir yang berbeda. Solusi: gunakan **K-Means++** yang memilih centroid awal secara cerdas, atau jalankan K-Means beberapa kali dengan inisialisasi berbeda dan pilih hasil terbaik.

---

### 2.3 Menentukan Jumlah Klaster K

#### Elbow Method

> **Elbow Method** adalah teknik untuk menentukan jumlah klaster optimal dengan memplot nilai **inertia** (Within-Cluster Sum of Squares/WCSS) terhadap berbagai nilai K, lalu mencari titik "siku" di mana penurunan WCSS melambat secara signifikan.

$$WCSS = \sum_{j=1}^{K}\sum_{x_i \in C_j} \|x_i - \mu_j\|^2$$

![Elbow Method](images/p14-02-elbow-method.png)

*Gambar 14.2: Grafik elbow method untuk menentukan K optimal*

#### Solved Problem 7 ⭐⭐

**Soal:** Diberikan nilai WCSS untuk berbagai K. Tentukan K optimal menggunakan Elbow Method!

| K | WCSS |
|---|------|
| 1 | 500 |
| 2 | 200 |
| 3 | 100 |
| 4 | 80 |
| 5 | 75 |
| 6 | 72 |

**Penyelesaian:**

*Step 1:* Hitung penurunan WCSS

| K | WCSS | Penurunan | % Penurunan |
|---|------|-----------|-------------|
| 1→2 | 500→200 | 300 | 60% |
| 2→3 | 200→100 | 100 | 50% |
| 3→4 | 100→80 | 20 | 20% |
| 4→5 | 80→75 | 5 | 6.25% |
| 5→6 | 75→72 | 3 | 4% |

*Step 2:* Identifikasi "siku"
- Penurunan besar: K=1→2 (60%), K=2→3 (50%)
- Penurunan drastis berkurang pada K=3→4 (dari 50% ke 20%)
- Setelah K=3, penurunan minimal

**Jawaban:** K optimal adalah **K=3**, karena pada titik ini terjadi perubahan signifikan dalam laju penurunan WCSS (dari 50% ke 20%). Menambah klaster setelah K=3 tidak memberikan pengurangan WCSS yang berarti.

---

#### Silhouette Score

> **Silhouette Score** mengukur seberapa mirip sebuah data dengan klasternya sendiri dibandingkan dengan klaster lain.

Untuk data $i$:

$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$

dimana:
- $a(i)$ = rata-rata jarak $i$ ke semua data di klaster yang **sama**
- $b(i)$ = rata-rata jarak $i$ ke semua data di klaster **terdekat lainnya**

Interpretasi:
- $s(i) \approx +1$: data cocok dengan klasternya (baik)
- $s(i) \approx 0$: data berada di batas dua klaster
- $s(i) \approx -1$: data mungkin salah klaster (buruk)

#### Solved Problem 8 ⭐⭐

**Soal:** Diberikan data berikut dengan dua klaster C₁={A, B} dan C₂={C, D}. Hitung silhouette score untuk titik A(1,1)!

| Titik | Koordinat | Klaster |
|-------|-----------|---------|
| A | (1, 1) | C₁ |
| B | (2, 2) | C₁ |
| C | (8, 8) | C₂ |
| D | (9, 9) | C₂ |

**Penyelesaian:**

*Step 1:* Hitung a(A) — rata-rata jarak ke anggota klaster yang sama (C₁)
- d(A, B) = √((2-1)² + (2-1)²) = √2 ≈ 1.41
- a(A) = 1.41 (hanya 1 anggota lain)

*Step 2:* Hitung b(A) — rata-rata jarak ke klaster terdekat lainnya (C₂)
- d(A, C) = √((8-1)² + (8-1)²) = √98 ≈ 9.90
- d(A, D) = √((9-1)² + (9-1)²) = √128 ≈ 11.31
- b(A) = (9.90 + 11.31) / 2 = 10.61

*Step 3:* Hitung silhouette score

$$s(A) = \frac{b(A) - a(A)}{\max(a(A), b(A))} = \frac{10.61 - 1.41}{\max(1.41, 10.61)} = \frac{9.20}{10.61} = 0.87$$

**Jawaban:** Silhouette score untuk titik A adalah **0.87**, menunjukkan A sangat cocok dengan klasternya (nilai mendekati +1).

---

## 3. Hierarchical Clustering

### 3.1 Konsep Hierarchical Clustering

> **Hierarchical Clustering** membangun hierarki klaster dalam bentuk **dendrogram**, tanpa perlu menentukan K di awal.

Dua pendekatan:
- **Agglomerative (bottom-up)**: Setiap data dimulai sebagai klaster sendiri, kemudian klaster-klaster terdekat digabung secara iteratif
- **Divisive (top-down)**: Semua data dimulai dalam satu klaster, kemudian dipisah secara iteratif

**Algoritma Agglomerative Clustering:**

```
1. Mulai: setiap data adalah 1 klaster
2. REPEAT:
   a. Hitung jarak antar semua pasangan klaster
   b. Gabungkan dua klaster terdekat
3. UNTIL tersisa 1 klaster
```

**Metode Linkage (mengukur jarak antar klaster):**

| Metode | Formula | Karakteristik |
|--------|---------|---------------|
| **Single Linkage** | min d(a, b), a∈C₁, b∈C₂ | Jarak minimum, rawan chaining |
| **Complete Linkage** | max d(a, b), a∈C₁, b∈C₂ | Jarak maksimum, klaster kompak |
| **Average Linkage** | mean d(a, b), a∈C₁, b∈C₂ | Rata-rata, kompromi |

![Hierarchical Clustering Dendrogram](images/p14-03-dendrogram.png)

*Gambar 14.3: Contoh dendrogram hasil hierarchical clustering*

#### Solved Problem 9 ⭐⭐

**Soal:** Lakukan agglomerative clustering dengan single linkage pada data berikut! Gambarkan langkah-langkahnya!

| Titik | x | y |
|-------|---|---|
| A | 1 | 1 |
| B | 2 | 1 |
| C | 5 | 5 |
| D | 6 | 5 |

**Penyelesaian:**

*Step 1:* Hitung matriks jarak awal

|   | A | B | C | D |
|---|---|---|---|---|
| A | 0 | 1.0 | 5.66 | 6.40 |
| B |   | 0 | 5.0 | 5.66 |
| C |   |   | 0 | 1.0 |
| D |   |   |   | 0 |

- d(A,B) = √((2-1)²+(1-1)²) = 1.0
- d(A,C) = √((5-1)²+(5-1)²) = √32 = 5.66
- d(A,D) = √((6-1)²+(5-1)²) = √41 = 6.40
- d(B,C) = √((5-2)²+(5-1)²) = √25 = 5.0
- d(B,D) = √((6-2)²+(5-1)²) = √32 = 5.66
- d(C,D) = √((6-5)²+(5-5)²) = 1.0

*Step 2:* Iterasi 1 — Gabungkan pasangan terdekat
- Jarak terkecil: d(A,B) = 1.0 dan d(C,D) = 1.0 (tie, pilih A,B)
- Gabungkan A dan B → {A,B}

*Step 3:* Perbarui matriks jarak (single linkage = minimum)
- d({A,B}, C) = min(d(A,C), d(B,C)) = min(5.66, 5.0) = 5.0
- d({A,B}, D) = min(d(A,D), d(B,D)) = min(6.40, 5.66) = 5.66

|   | {A,B} | C | D |
|---|-------|---|---|
| {A,B} | 0 | 5.0 | 5.66 |
| C |   | 0 | 1.0 |
| D |   |   | 0 |

*Step 4:* Iterasi 2 — Gabungkan C dan D (jarak 1.0)
- {A,B}, {C,D}
- d({A,B}, {C,D}) = min(5.0, 5.66) = 5.0

*Step 5:* Iterasi 3 — Gabungkan {A,B} dan {C,D} (jarak 5.0)
- Satu klaster: {A, B, C, D}

**Jawaban:** Urutan penggabungan:
1. A + B pada jarak 1.0
2. C + D pada jarak 1.0
3. {A,B} + {C,D} pada jarak 5.0

---

#### Solved Problem 10 ⭐

**Soal:** Apa perbedaan antara single linkage dan complete linkage? Kapan masing-masing lebih cocok digunakan?

**Penyelesaian:**

*Step 1:* Identifikasi perbedaan

| Aspek | Single Linkage | Complete Linkage |
|-------|----------------|------------------|
| **Formula** | Jarak minimum antar klaster | Jarak maksimum antar klaster |
| **Kecenderungan** | Klaster memanjang (chaining) | Klaster bulat dan kompak |
| **Sensitif terhadap** | Noise/bridge points | Outlier |

*Step 2:* Kapan digunakan
- **Single linkage**: Cocok untuk klaster non-spherical (berbentuk tidak beraturan)
- **Complete linkage**: Cocok ketika menginginkan klaster yang compact dan berukuran mirip

**Jawaban:** Single linkage menggunakan jarak minimum (rawan chaining), cocok untuk klaster berbentuk tidak beraturan. Complete linkage menggunakan jarak maksimum (klaster lebih kompak), cocok ketika menginginkan klaster berukuran seragam.

---

### 3.2 K-Means vs Hierarchical Clustering

| Aspek | K-Means | Hierarchical |
|-------|---------|--------------|
| **Input K** | Harus ditentukan | Tidak perlu (potong dendrogram) |
| **Kompleksitas** | O(n × K × t) | O(n³) atau O(n² log n) |
| **Bentuk klaster** | Spherical | Fleksibel |
| **Deterministik** | Tidak (tergantung inisialisasi) | Ya |
| **Scalability** | Baik untuk data besar | Kurang baik untuk data besar |

---

## 4. Dimensionality Reduction: PCA

### 4.1 Konsep PCA

> **Principal Component Analysis (PCA)** adalah teknik dimensionality reduction yang mentransformasi data ke ruang dimensi lebih rendah dengan mempertahankan sebanyak mungkin **variansi** data asli.

**Motivasi:** Data berdimensi tinggi sulit divisualisasikan dan dapat menyebabkan curse of dimensionality. PCA mencari arah (principal components) yang memaksimalkan variansi data.

**Langkah PCA (ringkas):**
1. Standarisasi data
2. Hitung matriks kovarians
3. Hitung eigenvalue dan eigenvector
4. Urutkan eigenvector berdasarkan eigenvalue (terbesar dahulu)
5. Pilih K eigenvector teratas sebagai principal components
6. Transformasi data ke ruang baru

#### Solved Problem 11 ⭐

**Soal:** Dataset memiliki 100 fitur. Setelah PCA, 3 principal component pertama menjelaskan 60%, 25%, dan 10% variansi. Berapa total variansi yang dijelaskan oleh 3 komponen ini? Apakah cukup?

**Penyelesaian:**

*Step 1:* Jumlahkan explained variance
- Total = 60% + 25% + 10% = **95%**

*Step 2:* Evaluasi
- Rule of thumb: 95% variansi sudah sangat baik
- Dari 100 dimensi menjadi 3 dimensi → reduksi drastis
- Hanya kehilangan 5% informasi

**Jawaban:** Total variansi yang dijelaskan adalah **95%**, yang sangat baik. Tiga komponen utama cukup untuk merepresentasikan data 100 dimensi dengan kehilangan informasi minimal.

---

#### Solved Problem 12 ⭐⭐

**Soal:** Sebuah sistem surveillance militer memiliki 50 sensor yang masing-masing menghasilkan 1 fitur setiap detik. Jelaskan bagaimana PCA dapat membantu dalam pemrosesan data real-time!

**Penyelesaian:**

*Step 1:* Identifikasi masalah
- 50 fitur per detik → dimensi tinggi
- Banyak sensor mungkin berkorelasi (redundan)
- Pemrosesan real-time memerlukan efisiensi

*Step 2:* Aplikasi PCA
- Reduksi dari 50 fitur menjadi (misalnya) 5-10 principal components
- Mempertahankan >95% variansi data
- Menghilangkan redundansi antar sensor

*Step 3:* Manfaat
- Pemrosesan lebih cepat (10x lebih sedikit fitur)
- Deteksi anomali lebih efektif di dimensi rendah
- Bandwidth komunikasi berkurang
- Visualisasi situasi lebih mudah

**Jawaban:** PCA dapat mereduksi 50 fitur sensor menjadi beberapa principal components (misal 5-10) yang mempertahankan informasi penting. Ini mempercepat pemrosesan real-time, menghilangkan redundansi antar sensor, mengurangi kebutuhan bandwidth, dan memudahkan deteksi anomali.

---

## 5. Reinforcement Learning

### 5.1 Konsep Dasar Reinforcement Learning

> **Reinforcement Learning (RL)** adalah paradigma pembelajaran mesin di mana **agen** belajar mengambil **tindakan** dalam suatu **lingkungan** untuk memaksimalkan **reward kumulatif** melalui trial and error.

![Komponen Reinforcement Learning](images/p14-04-reinforcement-learning.png)

*Gambar 14.4: Interaksi agen-lingkungan dalam reinforcement learning*

**Komponen RL:**

| Komponen | Simbol | Deskripsi |
|----------|--------|-----------|
| **Agent** | - | Entitas yang belajar dan mengambil keputusan |
| **Environment** | - | Dunia tempat agen berinteraksi |
| **State** | $s_t$ | Situasi agen pada waktu t |
| **Action** | $a_t$ | Tindakan agen pada waktu t |
| **Reward** | $r_t$ | Sinyal feedback numerik |
| **Policy** | $\pi(s)$ | Strategi: pemetaan state → action |
| **Value Function** | $V(s)$ | Estimasi reward kumulatif dari state s |

**Perbedaan dengan paradigma lain:**

| Aspek | Supervised | Unsupervised | Reinforcement |
|-------|-----------|--------------|---------------|
| **Feedback** | Label lengkap | Tidak ada | Reward (delayed) |
| **Tujuan** | Prediksi | Struktur | Maksimalkan reward |
| **Data** | Statis | Statis | Interaksi sekuensial |
| **Contoh** | Decision tree | K-Means | Q-Learning |

#### Solved Problem 13 ⭐

**Soal:** Identifikasi komponen RL (state, action, reward) pada skenario drone otonom yang belajar bermanuver menghindari rintangan!

**Penyelesaian:**

*Step 1:* Identifikasi setiap komponen

| Komponen | Contoh pada Drone |
|----------|-------------------|
| **Agent** | Drone otonom |
| **Environment** | Ruang udara dengan rintangan |
| **State** | Posisi (x,y,z), kecepatan, jarak ke rintangan terdekat, orientasi |
| **Action** | Naik, turun, belok kiri, belok kanan, maju, mundur, hover |
| **Reward** | +1 setiap timestep berhasil terbang tanpa tabrakan; -100 jika tabrakan; +10 jika mencapai tujuan |
| **Policy** | Aturan yang dipelajari: "jika rintangan di depan, belok kiri" |

**Jawaban:** State meliputi posisi dan kondisi drone, action adalah perintah manuver, dan reward dirancang untuk mendorong penerbangan aman menuju tujuan sambil menghindari tabrakan.

---

### 5.2 Markov Decision Process (MDP)

> **Markov Decision Process (MDP)** adalah kerangka matematis formal untuk memodelkan pengambilan keputusan sekuensial, di mana hasil sebagian bersifat acak dan sebagian dikendalikan oleh agen.

MDP didefinisikan oleh tuple $(S, A, T, R, \gamma)$:
- $S$: himpunan state
- $A$: himpunan action
- $T(s'|s,a)$: fungsi transisi (probabilitas berpindah ke s' dari s setelah action a)
- $R(s,a,s')$: fungsi reward
- $\gamma$: discount factor (0 ≤ γ ≤ 1)

> **Markov Property**: State saat ini berisi semua informasi yang relevan untuk pengambilan keputusan. Masa depan hanya bergantung pada state saat ini, bukan pada sejarah.

$$P(s_{t+1} | s_t, a_t, s_{t-1}, a_{t-1}, ...) = P(s_{t+1} | s_t, a_t)$$

#### Solved Problem 14 ⭐⭐

**Soal:** Sebuah robot patroli perbatasan beroperasi di grid 2×2 dengan state {S1, S2, S3, S4}. Robot dapat bergerak Atas (U), Bawah (D), Kiri (L), Kanan (R). S4 adalah base camp dengan reward +10. Setiap langkah mendapat reward -1. Formulasikan sebagai MDP!

**Penyelesaian:**

*Step 1:* Definisikan komponen MDP

```
Grid:
┌────┬────┐
│ S1 │ S2 │
├────┼────┤
│ S3 │ S4 │   ← base camp (goal)
└────┴────┘
```

*Step 2:* Tentukan komponen

- **S** = {S1, S2, S3, S4}
- **A** = {U, D, L, R}
- **T**: Deterministik (probabilitas 1.0 untuk arah yang diambil, jika menabrak dinding tetap di tempat)
- **R**: R = -1 untuk setiap langkah; R = +10 saat mencapai S4
- **γ** = 0.9 (discount factor)

*Step 3:* Contoh transisi

| State | Action | Next State | Reward |
|-------|--------|------------|--------|
| S1 | R | S2 | -1 |
| S1 | D | S3 | -1 |
| S1 | L | S1 | -1 (menabrak dinding) |
| S2 | D | S4 | +10 |
| S3 | R | S4 | +10 |

**Jawaban:** MDP terdefinisi dengan S={S1-S4}, A={U,D,L,R}, transisi deterministik pada grid 2×2, reward -1 per langkah dan +10 saat mencapai S4, dengan γ=0.9.

---

### 5.3 Policy dan Value Function

> **Policy** ($\pi$) adalah strategi yang memetakan setiap state ke action: $\pi(s) \rightarrow a$.

> **Value Function** ($V^\pi(s)$) adalah expected cumulative reward yang didapatkan dari state s jika mengikuti policy $\pi$:

$$V^\pi(s) = E\left[\sum_{t=0}^{\infty} \gamma^t r_{t+1} \mid s_0 = s, \pi\right]$$

> **Q-Function** ($Q^\pi(s,a)$) adalah expected cumulative reward dari state s, mengambil action a, lalu mengikuti policy $\pi$:

$$Q^\pi(s,a) = E\left[\sum_{t=0}^{\infty} \gamma^t r_{t+1} \mid s_0 = s, a_0 = a, \pi\right]$$

**Optimal Policy** ($\pi^*$) adalah policy yang memaksimalkan value function untuk semua state:

$$\pi^*(s) = \arg\max_a Q^*(s, a)$$

#### Solved Problem 15 ⭐⭐

**Soal:** Dari MDP grid 2×2 di Solved Problem 14, hitung value V(S2) dan V(S3) jika policy-nya adalah "selalu menuju S4 secepat mungkin" dengan γ=0.9!

**Penyelesaian:**

*Step 1:* Identifikasi policy optimal
- Dari S2: action D → langsung ke S4
- Dari S3: action R → langsung ke S4
- Dari S1: action D → S3 → S4, atau action R → S2 → S4

*Step 2:* Hitung V(S2) — satu langkah ke S4
- S2 → S4 (reward +10, kemudian episode berakhir)

$$V(S2) = R(S2, D) = +10$$

Catatan: Jika setelah S4 episode berakhir, V(S2) = 10.

Jika S4 bukan terminal dan robot tetap di S4 mendapat reward 0:

$$V(S2) = -1 + \gamma \cdot V(S4)$$

Namun karena S4 adalah goal state, anggap reward +10 diterima saat memasuki S4:

$$V(S2) = +10$$

*Step 3:* Hitung V(S3) — serupa, satu langkah ke S4

$$V(S3) = +10$$

*Step 4:* Hitung V(S1) — dua langkah ke S4

$$V(S1) = -1 + \gamma \cdot V(S2) = -1 + 0.9 \times 10 = -1 + 9 = 8$$

**Jawaban:** V(S2) = 10, V(S3) = 10, dan V(S1) = 8. State yang lebih dekat ke goal memiliki value lebih tinggi.

---

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Jelaskan perbedaan antara exploration dan exploitation dalam reinforcement learning! Mengapa keseimbangan keduanya penting? Berikan contoh dalam konteks drone militer!

**Penyelesaian:**

*Step 1:* Definisikan kedua konsep

| Aspek | Exploration | Exploitation |
|-------|-------------|--------------|
| **Definisi** | Mencoba aksi baru untuk menemukan informasi | Menggunakan pengetahuan terbaik saat ini |
| **Tujuan** | Menemukan strategi lebih baik | Memaksimalkan reward segera |
| **Risiko** | Reward rendah dalam jangka pendek | Terjebak di solusi sub-optimal |

*Step 2:* Jelaskan pentingnya keseimbangan
- **Terlalu banyak exploration**: Agen tidak pernah memanfaatkan pengetahuan yang sudah didapat
- **Terlalu banyak exploitation**: Agen tidak menemukan strategi yang lebih baik

*Step 3:* Contoh drone militer

**Skenario:** Drone pengintai belajar rute patroli optimal

**Exploitation:** Drone terus menggunakan Rute A yang diketahui aman dan efisien. Risiko: musuh mempelajari pola dan menyiapkan pertahanan.

**Exploration:** Drone sesekali mencoba rute baru (B, C, D). Mungkin menemukan rute yang lebih efisien atau mendeteksi ancaman baru. Risiko: mungkin terbang ke area berbahaya.

**Solusi: ε-greedy strategy**
- Dengan probabilitas (1-ε): pilih aksi terbaik (exploitation)
- Dengan probabilitas ε: pilih aksi random (exploration)
- ε dikurangi seiring waktu (lebih banyak exploit setelah cukup belajar)

**Jawaban:** Exploration mencoba hal baru, exploitation memanfaatkan pengetahuan. Keseimbangan penting agar agen menemukan solusi optimal tanpa terlalu banyak mengambil risiko. Strategi ε-greedy yang menurunkan ε secara bertahap adalah solusi umum.

---

## 6. Algoritma Q-Learning

### 6.1 Konsep Q-Learning

> **Q-Learning** adalah algoritma reinforcement learning **model-free** yang mempelajari nilai Q(s,a) — expected utility dari mengambil action a di state s — tanpa perlu mengetahui model transisi lingkungan.

**Update Rule Q-Learning:**

$$Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]$$

dimana:
- $\alpha$: learning rate (0 < α ≤ 1)
- $r$: reward yang diterima
- $\gamma$: discount factor
- $s'$: state berikutnya
- $\max_{a'} Q(s', a')$: estimasi value terbaik dari state berikutnya

![Algoritma Q-Learning](images/p14-05-q-learning-algorithm.png)

*Gambar 14.5: Alur algoritma Q-Learning*

**Algoritma Q-Learning:**

```
Inisialisasi Q(s,a) = 0 untuk semua s, a
FOR setiap episode:
    Inisialisasi state s
    REPEAT (untuk setiap langkah episode):
        Pilih action a dari s menggunakan ε-greedy
        Lakukan action a, amati reward r dan state baru s'
        Q(s,a) ← Q(s,a) + α[r + γ max_a' Q(s',a') - Q(s,a)]
        s ← s'
    UNTIL s adalah terminal state
```

#### Solved Problem 17 ⭐⭐

**Soal:** Diberikan grid 1×3 dengan state {S1, S2, S3}. S3 adalah goal dengan reward +10. Setiap langkah mendapat reward -1. Actions: Left (L) dan Right (R). Semua Q(s,a) awalnya 0. Lakukan satu episode Q-Learning dengan α=0.5, γ=0.9, dan path S1→R→S2→R→S3!

**Penyelesaian:**

*Step 1:* Inisialisasi Q-table

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | 0 |
| S2 | 0 | 0 |
| S3 | - | - |

*Step 2:* Langkah 1: S1 → R → S2, reward = -1

$$Q(S1, R) \leftarrow 0 + 0.5 \times [-1 + 0.9 \times \max(Q(S2,L), Q(S2,R)) - 0]$$
$$Q(S1, R) \leftarrow 0 + 0.5 \times [-1 + 0.9 \times \max(0, 0) - 0]$$
$$Q(S1, R) \leftarrow 0 + 0.5 \times [-1 + 0 - 0] = -0.5$$

*Step 3:* Langkah 2: S2 → R → S3 (goal), reward = +10

$$Q(S2, R) \leftarrow 0 + 0.5 \times [10 + 0.9 \times \max Q(S3,\cdot) - 0]$$

S3 terminal, maka $\max Q(S3, \cdot) = 0$:

$$Q(S2, R) \leftarrow 0 + 0.5 \times [10 + 0 - 0] = 5.0$$

*Step 4:* Q-table setelah episode 1

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | **-0.5** |
| S2 | 0 | **5.0** |

**Jawaban:** Setelah satu episode, Q(S1,R) = -0.5 dan Q(S2,R) = 5.0. Agen sudah mulai mempelajari bahwa bergerak ke kanan dari S2 sangat baik (menuju goal), sedangkan Q(S1,R) masih negatif karena belum memperhitungkan reward masa depan secara penuh.

---

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Lanjutkan Solved Problem 17 untuk episode kedua dengan path yang sama (S1→R→S2→R→S3). Bagaimana Q-table berubah? Apa yang terjadi setelah banyak episode?

**Penyelesaian:**

*Step 1:* Gunakan Q-table dari episode 1

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | -0.5 |
| S2 | 0 | 5.0 |

*Step 2:* Langkah 1 Episode 2: S1 → R → S2, reward = -1

$$Q(S1, R) \leftarrow -0.5 + 0.5 \times [-1 + 0.9 \times \max(0, 5.0) - (-0.5)]$$
$$Q(S1, R) \leftarrow -0.5 + 0.5 \times [-1 + 4.5 + 0.5]$$
$$Q(S1, R) \leftarrow -0.5 + 0.5 \times 4.0 = -0.5 + 2.0 = 1.5$$

*Step 3:* Langkah 2 Episode 2: S2 → R → S3, reward = +10

$$Q(S2, R) \leftarrow 5.0 + 0.5 \times [10 + 0 - 5.0]$$
$$Q(S2, R) \leftarrow 5.0 + 0.5 \times 5.0 = 5.0 + 2.5 = 7.5$$

*Step 4:* Q-table setelah episode 2

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | **1.5** |
| S2 | 0 | **7.5** |

*Step 5:* Analisis konvergensi

| Episode | Q(S1, R) | Q(S2, R) |
|---------|----------|----------|
| 0 | 0 | 0 |
| 1 | -0.5 | 5.0 |
| 2 | 1.5 | 7.5 |
| ... | ... | ... |
| ∞ | ~8.0 | ~10.0 |

Nilai konvergen:
- V*(S2) = 10 (satu langkah ke goal, reward +10)
- V*(S1) = -1 + 0.9 × 10 = 8.0 (dua langkah ke goal)

**Jawaban:** Setelah episode 2, Q(S1,R) = 1.5 dan Q(S2,R) = 7.5. Dengan banyak episode, Q-values konvergen ke nilai optimal: Q(S2,R) → 10 dan Q(S1,R) → 8.0. Agen belajar bahwa bergerak ke kanan adalah optimal dari kedua state.

---

### 6.2 Discount Factor dan Pengaruhnya

> **Discount Factor** ($\gamma$) menentukan seberapa penting reward masa depan dibanding reward sekarang.

| Nilai γ | Interpretasi |
|---------|-------------|
| γ = 0 | Hanya peduli reward segera (myopic) |
| γ = 0.5 | Seimbang antara sekarang dan masa depan |
| γ = 1.0 | Reward masa depan sama pentingnya (far-sighted) |

#### Solved Problem 19 ⭐

**Soal:** Sebuah drone harus memilih antara dua rute: Rute A memberikan reward 5 sekarang, Rute B memberikan reward 0 sekarang tapi reward 10 di langkah berikutnya. Dengan γ=0.8, mana yang lebih baik?

**Penyelesaian:**

*Step 1:* Hitung total discounted reward

- **Rute A**: $R_A = 5 + \gamma \times 0 = 5$
- **Rute B**: $R_B = 0 + \gamma \times 10 = 0 + 0.8 \times 10 = 8$

*Step 2:* Bandingkan
- Rute B (8) > Rute A (5)

**Jawaban:** Dengan γ=0.8, **Rute B** lebih baik (discounted reward 8 vs 5) karena agen cukup menghargai reward masa depan.

---

## 7. Perbandingan Tiga Paradigma Pembelajaran Mesin

![Perbandingan Tiga Paradigma ML](images/p14-06-three-ml-paradigms.png)

*Gambar 14.6: Perbandingan supervised, unsupervised, dan reinforcement learning*

| Aspek | Supervised | Unsupervised | Reinforcement |
|-------|-----------|--------------|---------------|
| **Data** | Berlabel (x, y) | Tanpa label (x) | Interaksi (s, a, r) |
| **Feedback** | Langsung (label) | Tidak ada | Delayed (reward) |
| **Tujuan** | Prediksi | Temukan pola | Maksimalkan reward |
| **Evaluasi** | Accuracy, F1, dll. | Silhouette, WCSS | Cumulative reward |
| **Contoh Algoritma** | Decision Tree, Naive Bayes, Regresi | K-Means, Hierarchical, PCA | Q-Learning, SARSA, DQN |
| **Contoh Aplikasi** | Klasifikasi tumor, spam filter | Segmentasi pelanggan, anomali | Robot navigasi, game AI |
| **Konteks Pertahanan** | Klasifikasi citra satelit | Clustering sinyal intelijen | Strategi drone otonom |

#### Solved Problem 20 ⭐⭐

**Soal:** Untuk setiap skenario berikut, tentukan paradigma ML yang paling sesuai dan jelaskan!

a) Mengelompokkan pola komunikasi musuh yang terintersepsi
b) Melatih drone untuk bermanuver dalam kondisi angin kencang
c) Memprediksi jenis kendaraan dari citra satelit

**Penyelesaian:**

*Step 1:* Analisis setiap skenario

**(a) Mengelompokkan pola komunikasi musuh:**
- Data: sinyal komunikasi tanpa label
- Tujuan: menemukan kelompok alami
- **Unsupervised Learning (Clustering)**

**(b) Melatih drone bermanuver:**
- Agen: drone
- Environment: ruang udara dengan angin
- Feedback: reward berdasarkan stabilitas terbang
- Belajar dari trial and error
- **Reinforcement Learning**

**(c) Memprediksi jenis kendaraan dari citra:**
- Data: citra satelit berlabel (tank, truk, APC, dll.)
- Tujuan: klasifikasi
- **Supervised Learning**

**Jawaban:** (a) Unsupervised Learning — data tanpa label, cari pola; (b) Reinforcement Learning — agen belajar manuver dari reward; (c) Supervised Learning — data berlabel, prediksi kategori.

---

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Sebuah sistem C6ISR harus menganalisis data dari berbagai sumber (radar, SIGINT, HUMINT, citra satelit). Rancang arsitektur AI yang mengombinasikan ketiga paradigma ML! Jelaskan peran masing-masing paradigma!

**Penyelesaian:**

*Step 1:* Identifikasi sub-tugas dan paradigma yang sesuai

| Sub-tugas | Data | Paradigma | Algoritma |
|-----------|------|-----------|-----------|
| Klasifikasi ancaman dari citra | Berlabel | Supervised | CNN (deep learning) |
| Clustering sinyal SIGINT | Tanpa label | Unsupervised | K-Means, DBSCAN |
| Alokasi aset pertahanan | Interaksi | Reinforcement | Multi-Agent RL |
| Deteksi anomali jaringan | Semi-label | Unsupervised | Clustering + outlier detection |
| Prediksi rute musuh | Historical data | Supervised | Sequence models |

*Step 2:* Rancang arsitektur

```
Layer 1: Data Preprocessing
├── Citra satelit → Feature extraction
├── Sinyal SIGINT → Signal processing
├── HUMINT reports → NLP processing
└── Radar data → Track processing

Layer 2: ML Processing
├── Supervised: Klasifikasi ancaman (citra, track)
├── Unsupervised: Clustering sinyal, anomali detection
└── Reinforcement: Alokasi aset real-time

Layer 3: Fusion & Decision Support
├── Data fusion dari semua paradigma
├── Threat assessment terintegrasi
└── Rekomendasi COA (Course of Action)
```

*Step 3:* Jelaskan sinergi
- **Unsupervised** menemukan pola baru yang belum diketahui
- **Supervised** mengklasifikasikan berdasarkan pengetahuan yang ada
- **Reinforcement** mengoptimalkan pengambilan keputusan secara adaptif

**Jawaban:** Arsitektur tiga-layer mengombinasikan supervised (klasifikasi ancaman), unsupervised (clustering sinyal, anomali), dan reinforcement learning (alokasi aset adaptif) dalam pipeline pemrosesan bertingkat yang menghasilkan rekomendasi terpadu untuk komandan.

---

## 8. Trend Terkini: Deep Learning (Overview)

### 8.1 Pengenalan Deep Learning

> **Deep Learning** adalah subset dari machine learning yang menggunakan **neural network** dengan banyak layer (deep neural network) untuk mempelajari representasi data secara hierarkis.

**Konsep Dasar:**
- **Neuron artifisial**: unit komputasi yang menerima input, menerapkan bobot, dan menghasilkan output melalui activation function
- **Layer**: kumpulan neuron (input layer, hidden layers, output layer)
- **Deep**: neural network dengan banyak hidden layers

**Arsitektur populer:**

| Arsitektur | Aplikasi | Contoh |
|------------|----------|--------|
| **CNN** (Convolutional NN) | Computer Vision | Klasifikasi citra, deteksi objek |
| **RNN/LSTM** | Sequence data | NLP, time series, speech |
| **Transformer** | NLP, multimodal | GPT, BERT, ChatGPT |
| **GAN** | Generative | Image generation, deepfake |

**Deep Learning dalam Pertahanan:**
- Deteksi objek dari citra satelit dan drone (CNN)
- Analisis komunikasi dan SIGINT (NLP/Transformer)
- Autonomous navigation (Deep RL)
- Cybersecurity threat detection (Autoencoder)

> **Catatan:** Topik deep learning akan dibahas lebih mendalam pada mata kuliah **Machine Learning (Semester 5)**.

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Jelaskan bagaimana deep reinforcement learning (Deep RL) berbeda dari Q-Learning tabular! Mengapa Deep RL diperlukan untuk aplikasi nyata seperti autonomous drone?

**Penyelesaian:**

*Step 1:* Identifikasi keterbatasan Q-Learning tabular

| Aspek | Q-Learning Tabular | Deep RL |
|-------|-------------------|---------|
| **State representation** | Tabel (finite states) | Neural network (continuous states) |
| **Scalability** | Buruk untuk state besar | Baik untuk state besar/kontinu |
| **Generalisasi** | Tidak ada | Neural network generalisasi ke state baru |
| **Memori** | O(|S| × |A|) | Fixed (parameter neural network) |

*Step 2:* Mengapa Deep RL diperlukan untuk drone

Autonomous drone memiliki:
- **State space**: posisi (x,y,z), kecepatan, orientasi, sensor readings → dimensi sangat tinggi dan kontinu
- Tabel Q tidak feasible (infinite states)
- Neural network dapat meng-aproksimasi Q-function: Q(s,a) ≈ Q(s,a; θ)

*Step 3:* Contoh: Deep Q-Network (DQN)
- Menggunakan neural network untuk meng-aproksimasi Q-values
- Input: state (misal pixel citra dari kamera drone)
- Output: Q-values untuk setiap action
- Dilatih dengan experience replay dan target network

**Jawaban:** Deep RL mengganti tabel Q dengan neural network, memungkinkan penanganan state space kontinu dan berdimensi tinggi. Ini diperlukan untuk aplikasi nyata seperti drone di mana state (posisi, kecepatan, citra kamera) tidak bisa direpresentasikan dalam tabel terbatas. DQN dan variannya meng-aproksimasi Q-function dan generalisasi ke state yang belum pernah dilihat.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Sebutkan tiga perbedaan utama antara K-Means dan hierarchical clustering!

**Jawaban:**
1. K-Means memerlukan K di awal, hierarchical tidak
2. K-Means O(nKt), hierarchical O(n²) atau O(n³)
3. K-Means menghasilkan klaster spherical, hierarchical lebih fleksibel

---

### Problem S2 ⭐⭐
**Soal:** Jika silhouette score rata-rata sebuah clustering adalah 0.15, apa interpretasinya?

**Jawaban:** Silhouette score 0.15 mendekati 0, menunjukkan bahwa data berada di batas antar klaster. Clustering tidak memberikan pemisahan yang jelas. Perlu mencoba nilai K yang berbeda atau algoritma clustering lain.

---

### Problem S3 ⭐⭐
**Soal:** Dalam RL, apa yang terjadi jika discount factor γ = 0? Berikan contoh skenario di mana ini mungkin sesuai!

**Jawaban:** Dengan γ = 0, agen hanya mempertimbangkan reward segera (myopic). Cocok untuk: sistem respons darurat yang harus mengambil tindakan terbaik saat ini tanpa perencanaan jangka panjang (misal: penghindaran tabrakan instan pada drone).

---

### Problem S4 ⭐⭐
**Soal:** Mengapa K-Means tidak cocok untuk mendeteksi klaster berbentuk non-spherical (misalnya klaster berbentuk bulan sabit)?

**Jawaban:** K-Means menggunakan jarak Euclidean ke centroid, sehingga secara implisit mengasumsikan klaster berbentuk bulat (spherical). Data yang berbentuk bulan sabit akan dipaksa masuk ke partisi Voronoi yang bulat, menghasilkan clustering yang salah. Alternatif: DBSCAN atau spectral clustering.

---

### Problem S5 ⭐⭐⭐
**Soal:** Rancang reward function untuk AUV (Autonomous Underwater Vehicle) patroli yang harus menyeimbangkan: area coverage, stealth, efisiensi baterai, dan deteksi ancaman!

**Jawaban:**
$$R(s, a) = w_1 \cdot coverage + w_2 \cdot stealth - w_3 \cdot battery\_cost + w_4 \cdot detection$$

Dengan bobot: w₁=0.3, w₂=0.25, w₃=0.20, w₄=0.25

- coverage: +1 untuk setiap grid baru yang di-survey
- stealth: +1 jika tidak terdeteksi, -5 jika terdeteksi musuh
- battery_cost: -0.1 per langkah, -0.5 untuk manuver cepat
- detection: +10 jika berhasil mendeteksi ancaman, +5 untuk data oseanografi penting

Reward function ini mendorong AUV untuk memaksimalkan area patroli sambil tetap tidak terdeteksi, efisien dalam penggunaan baterai, dan proaktif dalam deteksi ancaman.

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Unsupervised Learning** | Pembelajaran dari data tanpa label, menemukan pola tersembunyi |
| **Clustering** | Mengelompokkan data berdasarkan kemiripan |
| **K-Means** | Algoritma clustering partisi dengan K centroid |
| **Hierarchical Clustering** | Clustering berbasis hierarki (dendrogram) |
| **Elbow Method** | Menentukan K optimal dari grafik WCSS |
| **Silhouette Score** | Mengukur kualitas clustering (-1 hingga +1) |
| **PCA** | Reduksi dimensi dengan mempertahankan variansi maksimal |
| **Reinforcement Learning** | Agen belajar dari reward melalui interaksi dengan lingkungan |
| **MDP** | Framework formal: (S, A, T, R, γ) |
| **Policy** | Pemetaan state → action |
| **Value Function** | Estimasi reward kumulatif dari suatu state |
| **Q-Learning** | Algoritma RL model-free yang mempelajari Q(s,a) |
| **Discount Factor (γ)** | Menentukan pentingnya reward masa depan |
| **Deep Learning** | Neural network dengan banyak layer untuk representasi hierarkis |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 19-22**.
2. Mitchell, T. (1997). *Machine Learning*. McGraw-Hill. **Chapter 13**.
3. Bishop, C.M. (2006). *Pattern Recognition and Machine Learning*. Springer. **Chapter 9**.
4. Sutton, R.S. & Barto, A.G. (2018). *Reinforcement Learning: An Introduction* (2nd Ed.). MIT Press.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
