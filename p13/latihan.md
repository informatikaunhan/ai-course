# Latihan Pertemuan 13: Pembelajaran Mesin - Supervised Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 13  
**Topik:** Pembelajaran Mesin - Supervised Learning  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Petunjuk Pengerjaan

1. Kerjakan semua soal secara mandiri
2. Waktu pengerjaan: 120 menit
3. Untuk soal pilihan ganda, pilih satu jawaban yang paling tepat
4. Untuk soal uraian, jawab dengan lengkap dan sistematis
5. Studi kasus memerlukan analisis mendalam dan penerapan konsep

---

## Bagian A: Soal Pilihan Ganda (20 Soal)

### Soal 1
Menurut definisi Tom Mitchell, sebuah program komputer dikatakan "belajar" dari pengalaman E terhadap tugas T dengan ukuran kinerja P jika:

A. Program memiliki database yang besar  
B. Program dapat menjalankan tugas tanpa error  
C. Kinerja P pada tugas T meningkat seiring dengan pengalaman E  
D. Program ditulis oleh programmer yang ahli  
E. Program dapat berkomunikasi dengan manusia

---

### Soal 2
Paradigma pembelajaran mesin di mana model belajar dari data yang TIDAK memiliki label disebut:

A. Supervised Learning  
B. Unsupervised Learning  
C. Reinforcement Learning  
D. Semi-Supervised Learning  
E. Transfer Learning

---

### Soal 3
Manakah yang merupakan contoh masalah supervised learning?

A. Mengelompokkan pelanggan berdasarkan perilaku belanja  
B. Menemukan pola anomali dalam lalu lintas jaringan  
C. Mengklasifikasikan email sebagai spam atau bukan spam berdasarkan contoh berlabel  
D. Melatih agen bermain game melalui trial-and-error  
E. Mereduksi dimensi data dari 100 fitur menjadi 10

---

### Soal 4
Pada decision tree, node internal (internal node) merepresentasikan:

A. Keputusan akhir (kelas)  
B. Pengujian terhadap suatu atribut  
C. Probabilitas prior  
D. Nilai entropy  
E. Bobot fitur

---

### Soal 5
Jika sebuah dataset memiliki 10 sampel kelas "Ancaman" dan 10 sampel kelas "Aman", maka entropy dataset tersebut adalah:

A. 0  
B. 0.5  
C. 0.811  
D. 1.0  
E. 2.0

---

### Soal 6
Entropy bernilai 0 ketika:

A. Data terbagi rata 50:50 antara dua kelas  
B. Semua data termasuk dalam satu kelas yang sama  
C. Data memiliki noise yang tinggi  
D. Jumlah atribut lebih besar dari jumlah sampel  
E. Data belum dinormalisasi

---

### Soal 7
Rumus Information Gain yang benar adalah:

A. IG(S, A) = H(S) + H(S|A)  
B. IG(S, A) = H(S) − H(S|A)  
C. IG(S, A) = H(S|A) − H(S)  
D. IG(S, A) = H(S) × H(S|A)  
E. IG(S, A) = H(S) / H(S|A)

---

### Soal 8
Pada algoritma ID3, atribut yang dipilih sebagai root node adalah atribut dengan:

A. Entropy tertinggi  
B. Entropy terendah  
C. Information Gain tertinggi  
D. Information Gain terendah  
E. Jumlah nilai unik paling sedikit

---

### Soal 9
Overfitting pada decision tree terjadi ketika:

A. Model terlalu sederhana sehingga tidak menangkap pola  
B. Model terlalu kompleks sehingga menghafal data training termasuk noise  
C. Data training terlalu banyak  
D. Jumlah atribut terlalu sedikit  
E. Model tidak memiliki bias

---

### Soal 10
Teknik pruning pada decision tree bertujuan untuk:

A. Menambah kedalaman tree agar lebih akurat  
B. Mengurangi kompleksitas tree untuk mencegah overfitting  
C. Menambah jumlah atribut yang diuji  
D. Mengubah decision tree menjadi random forest  
E. Menghilangkan data outlier dari dataset

---

### Soal 11
Asumsi utama yang mendasari Naive Bayes classifier adalah:

A. Semua fitur memiliki distribusi normal  
B. Semua fitur bersifat independen satu sama lain given kelas  
C. Probabilitas prior selalu sama untuk semua kelas  
D. Jumlah data training harus sangat besar  
E. Data harus berskala numerik

---

### Soal 12
Laplace smoothing pada Naive Bayes digunakan untuk mengatasi masalah:

A. Data yang tidak seimbang  
B. Probabilitas nol akibat fitur yang tidak muncul di training data  
C. Overfitting pada data training  
D. Komputasi yang terlalu lambat  
E. Fitur yang berkorelasi tinggi

---

### Soal 13
Pada regresi linear ŷ = w₀ + w₁x, komponen w₀ disebut:

A. Slope  
B. Gradient  
C. Intercept (bias)  
D. Coefficient of determination  
E. Learning rate

---

### Soal 14
Metode Least Squares pada regresi linear bertujuan untuk:

A. Memaksimalkan jumlah kuadrat residual  
B. Meminimalkan jumlah kuadrat selisih antara nilai prediksi dan nilai aktual  
C. Menghilangkan outlier dari dataset  
D. Menormalisasi data input  
E. Memaksimalkan korelasi antara fitur

---

### Soal 15
Pada confusion matrix, True Positive (TP) adalah:

A. Data yang diprediksi positif dan aktualnya negatif  
B. Data yang diprediksi negatif dan aktualnya positif  
C. Data yang diprediksi positif dan aktualnya memang positif  
D. Data yang diprediksi negatif dan aktualnya memang negatif  
E. Jumlah seluruh data yang diprediksi benar

---

### Soal 16
Rumus Precision yang benar adalah:

A. TP / (TP + FN)  
B. TP / (TP + FP)  
C. (TP + TN) / (TP + TN + FP + FN)  
D. TN / (TN + FP)  
E. 2 × (Precision × Recall) / (Precision + Recall)

---

### Soal 17
Dalam konteks sistem deteksi rudal musuh, metrik evaluasi yang PALING penting untuk dioptimalkan adalah:

A. Accuracy  
B. Precision  
C. Recall  
D. Specificity  
E. F1-Score

---

### Soal 18
Pada 5-fold cross-validation, berapa persen data yang digunakan sebagai test set pada setiap iterasi?

A. 5%  
B. 10%  
C. 20%  
D. 50%  
E. 80%

---

### Soal 19
Stratified K-Fold Cross-Validation berbeda dari K-Fold biasa karena:

A. Menggunakan lebih banyak fold  
B. Memastikan setiap fold memiliki proporsi kelas yang sama  
C. Hanya menggunakan data numerik  
D. Tidak memerlukan data test  
E. Memerlukan data yang sudah di-shuffle

---

### Soal 20
Peningkatan dari algoritma ID3 ke C4.5 meliputi hal-hal berikut, KECUALI:

A. Penggunaan Gain Ratio sebagai pengganti Information Gain  
B. Kemampuan menangani atribut numerik/kontinu  
C. Penanganan missing values  
D. Penggunaan ensemble learning dengan multiple trees  
E. Mekanisme pruning otomatis

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara supervised learning, unsupervised learning, dan reinforcement learning! Berikan satu contoh aplikasi pertahanan untuk masing-masing paradigma!

---

### Soal 2 ⭐
Identifikasi komponen T (Task), P (Performance), dan E (Experience) untuk sistem klasifikasi citra satelit yang mendeteksi kendaraan militer!

---

### Soal 3 ⭐
Jelaskan apa yang dimaksud dengan entropy dalam konteks decision tree! Kapan entropy bernilai maksimum dan kapan bernilai minimum?

---

### Soal 4 ⭐
Sebutkan dan jelaskan empat komponen utama sebuah decision tree (root node, internal node, branch, dan leaf node)!

---

### Soal 5 ⭐⭐
Diberikan dataset berikut untuk klasifikasi ancaman radar:

| No | Kecepatan | Altitude | Klasifikasi |
|----|-----------|----------|-------------|
| 1  | Tinggi    | Tinggi   | Ancaman     |
| 2  | Tinggi    | Rendah   | Ancaman     |
| 3  | Rendah    | Tinggi   | Aman        |
| 4  | Rendah    | Rendah   | Aman        |
| 5  | Tinggi    | Tinggi   | Ancaman     |
| 6  | Rendah    | Rendah   | Aman        |

Hitung entropy awal dataset S! Tunjukkan langkah perhitungan secara detail!

---

### Soal 6 ⭐⭐
Menggunakan dataset pada Soal 5, hitung Information Gain untuk atribut "Kecepatan"! Atribut mana yang lebih baik untuk root node: Kecepatan atau Altitude? (Tunjukkan perhitungan IG untuk keduanya)

---

### Soal 7 ⭐⭐
Jelaskan perbedaan antara overfitting dan underfitting pada decision tree! Apa dampak masing-masing terhadap performa model pada data baru? Bagaimana teknik pruning membantu mengatasi overfitting?

---

### Soal 8 ⭐⭐
Sebuah dataset email memiliki data berikut:

| | Kata "gratis" muncul | Kata "rapat" muncul |
|---|---|---|
| Spam (8 email) | 6 | 1 |
| Bukan Spam (12 email) | 2 | 8 |

Gunakan Naive Bayes untuk mengklasifikasikan email baru yang mengandung kata "gratis" tetapi TIDAK mengandung kata "rapat"! Tunjukkan perhitungan lengkap!

---

### Soal 9 ⭐⭐
Jelaskan mengapa Laplace smoothing diperlukan pada Naive Bayes! Berikan contoh numerik di mana tanpa Laplace smoothing menghasilkan masalah, dan bagaimana Laplace smoothing menyelesaikannya!

---

### Soal 10 ⭐⭐
Diberikan data training untuk regresi linear:

| Jam Latihan (x) | Akurasi Tembakan (y) |
|-----------------|---------------------|
| 2               | 55                  |
| 4               | 62                  |
| 6               | 70                  |
| 8               | 78                  |

Hitung parameter w₁ (slope) dan w₀ (intercept) menggunakan metode Least Squares! Prediksi akurasi tembakan jika jam latihan = 10!

---

### Soal 11 ⭐⭐
Sebuah sistem deteksi intrusi jaringan militer menghasilkan confusion matrix berikut:

|                    | Prediksi: Intrusi | Prediksi: Normal |
|--------------------|:-----------------:|:----------------:|
| **Aktual: Intrusi** | 42               | 8                |
| **Aktual: Normal**  | 5                | 145              |

Hitung: (a) Accuracy, (b) Precision, (c) Recall, (d) F1-Score!

---

### Soal 12 ⭐⭐⭐
Jelaskan langkah-langkah algoritma ID3 secara lengkap! Kemudian, bangun decision tree menggunakan dataset berikut:

| No | Cuaca   | Angin   | Visibilitas | Misi Terbang? |
|----|---------|---------|-------------|---------------|
| 1  | Cerah   | Lemah   | Baik        | Ya            |
| 2  | Cerah   | Kencang | Baik        | Ya            |
| 3  | Mendung | Lemah   | Baik        | Ya            |
| 4  | Hujan   | Lemah   | Buruk       | Tidak         |
| 5  | Hujan   | Kencang | Buruk       | Tidak         |
| 6  | Mendung | Kencang | Buruk       | Tidak         |
| 7  | Cerah   | Lemah   | Buruk       | Ya            |
| 8  | Hujan   | Lemah   | Baik        | Tidak         |

Tunjukkan perhitungan entropy dan information gain untuk setiap atribut pada langkah pertama!

---

### Soal 13 ⭐⭐⭐
Bandingkan Naive Bayes classifier dengan Decision Tree dalam hal: (a) asumsi yang mendasari, (b) penanganan atribut kontinu, (c) interpretabilitas, (d) performa pada dataset kecil, dan (e) contoh kasus pertahanan yang paling sesuai untuk masing-masing!

---

### Soal 14 ⭐⭐⭐
Jelaskan secara detail mengapa recall lebih penting daripada precision untuk sistem deteksi rudal! Berikan contoh skenario numerik dengan confusion matrix yang menunjukkan: (a) model dengan precision tinggi tapi recall rendah, dan (b) model dengan recall tinggi tapi precision sedang. Analisis konsekuensi masing-masing dalam konteks pertahanan!

---

### Soal 15 ⭐⭐⭐
Jelaskan konsep K-Fold Cross-Validation secara lengkap! Mengapa cross-validation lebih baik daripada single train/test split? Kapan sebaiknya menggunakan Stratified K-Fold? Berikan contoh ilustratif dengan dataset klasifikasi sinyal radar yang memiliki kelas tidak seimbang (90% normal, 10% ancaman)!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Klasifikasi Ancaman Udara Berbasis Machine Learning

**Latar Belakang:**

Komando Pertahanan Udara Nasional (Kohanudnas) sedang mengembangkan sistem klasifikasi otomatis untuk mengidentifikasi objek udara yang terdeteksi radar. Sistem harus mampu mengklasifikasikan objek ke dalam empat kategori: Pesawat Sipil, Pesawat Militer Kawan, Pesawat Militer Asing, dan Drone/UAV Tidak Dikenal.

Data training dikumpulkan dari 500 catatan historis radar dengan atribut berikut:

| Atribut | Tipe | Deskripsi |
|---------|------|-----------|
| Kecepatan | Numerik | Kecepatan objek (knots) |
| Altitude | Numerik | Ketinggian terbang (feet) |
| RCS | Numerik | Radar Cross Section (m²) |
| Transponder | Kategorik | IFF response (Kawan/Netral/Tidak Ada) |
| Pola Terbang | Kategorik | Lurus/Bermanuver/Loiter |
| Zona | Kategorik | ADIZ/FIR/Territorial |

Distribusi kelas:
- Pesawat Sipil: 300 (60%)
- Pesawat Militer Kawan: 100 (20%)
- Pesawat Militer Asing: 50 (10%)
- Drone/UAV: 50 (10%)

**Pertanyaan:**

**1a.** Identifikasi komponen T, P, dan E dari sistem ini berdasarkan definisi Tom Mitchell! (10 poin)

**1b.** Jelaskan mengapa distribusi kelas yang tidak seimbang menjadi masalah! Metrik evaluasi apa yang paling tepat untuk digunakan dan mengapa? Apakah accuracy saja cukup? (15 poin)

**1c.** Seorang analis menyarankan menggunakan Decision Tree untuk sistem ini. Jelaskan kelebihan dan kekurangan decision tree untuk kasus ini! Atribut mana yang menurut Anda akan memiliki Information Gain tertinggi sebagai root node? Berikan alasannya! (15 poin)

**1d.** Analis lain menyarankan Naive Bayes. Identifikasi masalah utama penerapan Naive Bayes pada dataset ini berkaitan dengan asumsi independence! Atribut mana yang kemungkinan besar TIDAK independen? (10 poin)

**1e.** Tim memutuskan menggunakan 10-fold Stratified Cross-Validation untuk evaluasi model. Jelaskan mengapa Stratified CV diperlukan untuk dataset ini! Berapa jumlah sampel di setiap fold untuk masing-masing kelas? (15 poin)

---

### Studi Kasus 2: Prediksi Kesiapan Tempur Unit Militer

**Latar Belakang:**

Staf Perencanaan TNI mengembangkan sistem prediksi kesiapan tempur unit-unit militer menggunakan machine learning. Sistem harus memprediksi apakah suatu unit memenuhi standar kesiapan tempur (Siap/Tidak Siap) berdasarkan data historis.

Dataset training terdiri dari 200 catatan evaluasi unit dengan atribut berikut:

| No | Personel (%) | Materiel (%) | Latihan (jam/bln) | Moral (1-10) | Siap? |
|----|-------------|-------------|-------------------|-------------|-------|
| 1  | 95          | 90          | 120               | 9           | Ya    |
| 2  | 80          | 75          | 80                | 7           | Ya    |
| 3  | 60          | 50          | 40                | 4           | Tidak |
| 4  | 90          | 85          | 100               | 8           | Ya    |
| 5  | 70          | 60          | 60                | 5           | Tidak |
| ... | ... | ... | ... | ... | ... |

Ringkasan statistik:
- Total: 200 unit, 130 Siap (65%), 70 Tidak Siap (35%)
- Rata-rata Personel: Siap = 88%, Tidak Siap = 65%
- Rata-rata Materiel: Siap = 83%, Tidak Siap = 55%
- Rata-rata Latihan: Siap = 105 jam, Tidak Siap = 50 jam

Setelah model dibangun, confusion matrix pada test set (40 unit) adalah:

|                        | Prediksi: Siap | Prediksi: Tidak Siap |
|------------------------|:--------------:|:--------------------:|
| **Aktual: Siap**       | 22             | 4                    |
| **Aktual: Tidak Siap** | 3              | 11                   |

**Pertanyaan:**

**2a.** Hitung entropy awal dataset (130 Siap vs 70 Tidak Siap)! Jika atribut "Personel" di-discretisasi menjadi dua kelompok (≥80% dan <80%), dan distribusinya adalah: ≥80% → 110 Siap & 20 Tidak Siap; <80% → 20 Siap & 50 Tidak Siap, hitung Information Gain atribut Personel! (15 poin)

**2b.** Berdasarkan confusion matrix di atas, hitung semua metrik evaluasi: Accuracy, Precision, Recall, dan F1-Score! Interpretasikan hasil dalam konteks kesiapan tempur! (15 poin)

**2c.** Seorang perwira menyatakan: "Lebih berbahaya menilai unit yang TIDAK siap sebagai Siap daripada sebaliknya." Jelaskan metrik mana yang paling relevan dengan pernyataan ini! Apakah model saat ini sudah baik dalam konteks ini? Berikan rekomendasi perbaikan! (15 poin)

**2d.** Rancang model regresi linear sederhana untuk memprediksi jam latihan optimal berdasarkan tingkat kesiapan personel! Gunakan data sampel berikut untuk menghitung w₀ dan w₁:

| Personel (%) | Latihan Optimal (jam) |
|-------------|----------------------|
| 60          | 120                  |
| 70          | 100                  |
| 80          | 80                   |
| 90          | 60                   |
| 95          | 50                   |

Interpretasikan makna slope dalam konteks militer! (10 poin)

**2e.** Jelaskan bagaimana Anda akan menerapkan 5-fold cross-validation pada dataset 200 unit ini! Apa yang harus diperhatikan agar evaluasi valid? Jika rata-rata akurasi dari 5 fold adalah 82% dengan standar deviasi 5%, apakah model cukup stabil? Jelaskan! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | Definisi Mitchell: kinerja P pada tugas T meningkat seiring pengalaman E |
| 2 | **B** | Unsupervised learning belajar dari data tanpa label (menemukan pola/struktur tersembunyi) |
| 3 | **C** | Klasifikasi email berdasarkan contoh berlabel adalah supervised learning (ada input + output label) |
| 4 | **B** | Internal node merepresentasikan pengujian/pertanyaan terhadap suatu atribut |
| 5 | **D** | H(S) = −(10/20)log₂(10/20) − (10/20)log₂(10/20) = −0.5×(−1) − 0.5×(−1) = 1.0 |
| 6 | **B** | Entropy = 0 ketika semua data murni (satu kelas saja), karena −1×log₂(1) = 0 |
| 7 | **B** | Information Gain = Entropy awal − Entropy setelah split: IG(S,A) = H(S) − H(S|A) |
| 8 | **C** | ID3 memilih atribut dengan Information Gain tertinggi sebagai root |
| 9 | **B** | Overfitting terjadi saat model terlalu kompleks dan menghafal data training termasuk noise |
| 10 | **B** | Pruning mengurangi kompleksitas tree dengan memangkas cabang yang tidak signifikan |
| 11 | **B** | Asumsi Naive Bayes: semua fitur independen satu sama lain given kelas (conditional independence) |
| 12 | **B** | Laplace smoothing menambahkan konstanta kecil agar tidak ada probabilitas nol |
| 13 | **C** | w₀ adalah intercept atau bias, yaitu nilai y saat x = 0 |
| 14 | **B** | Least Squares meminimalkan Sum of Squared Errors (SSE) = Σ(yᵢ − ŷᵢ)² |
| 15 | **C** | True Positive: diprediksi positif dan aktualnya memang positif |
| 16 | **B** | Precision = TP / (TP + FP), mengukur ketepatan prediksi positif |
| 17 | **C** | Recall (TP/(TP+FN)) paling penting untuk deteksi rudal karena rudal yang terlewat (FN) sangat fatal |
| 18 | **C** | 5-fold: setiap iterasi menggunakan 1/5 = 20% data sebagai test set |
| 19 | **B** | Stratified menjaga proporsi kelas sama di setiap fold, penting untuk dataset tidak seimbang |
| 20 | **D** | Ensemble learning dengan multiple trees adalah Random Forest, bukan peningkatan ID3→C4.5 |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Supervised Learning:**
- Model belajar dari data berlabel (pasangan input-output)
- Tujuan: memprediksi output untuk input baru
- **Contoh pertahanan:** Klasifikasi sinyal radar (ancaman/aman) berdasarkan data historis berlabel

**Unsupervised Learning:**
- Model belajar dari data tanpa label
- Tujuan: menemukan pola atau struktur tersembunyi
- **Contoh pertahanan:** Clustering pola komunikasi musuh untuk menemukan kelompok aktivitas mencurigakan

**Reinforcement Learning:**
- Agen belajar melalui interaksi dengan lingkungan, menerima reward/punishment
- Tujuan: memaksimalkan reward kumulatif
- **Contoh pertahanan:** Melatih drone otonom untuk navigasi medan perang melalui simulasi trial-and-error

---

#### Jawaban Soal 2 ⭐

**Task (T):** Mengklasifikasikan citra satelit untuk mendeteksi dan mengidentifikasi jenis kendaraan militer (tank, APC, truk logistik, dll.)

**Performance (P):** Akurasi deteksi (persentase kendaraan yang teridentifikasi benar), recall (proporsi kendaraan aktual yang berhasil terdeteksi), dan precision (ketepatan deteksi)

**Experience (E):** Database citra satelit historis yang telah dianotasi oleh analis citra intelijen, berisi lokasi dan jenis kendaraan militer yang teridentifikasi

---

#### Jawaban Soal 3 ⭐

**Entropy** adalah ukuran ketidakmurnian (impurity) atau ketidakpastian dalam sebuah dataset. Dalam konteks decision tree, entropy mengukur seberapa "campur" data dalam hal distribusi kelas.

Rumus: $H(S) = -\sum_{c \in C} p(c) \log_2 p(c)$

dimana p(c) adalah proporsi sampel kelas c dalam dataset S.

**Entropy maksimum (H = 1 untuk 2 kelas):** Terjadi ketika data terbagi rata 50:50 antara kelas. Ini menunjukkan ketidakpastian tertinggi — kita tidak bisa menebak kelas tanpa informasi tambahan.

**Entropy minimum (H = 0):** Terjadi ketika semua data termasuk dalam satu kelas yang sama. Ini menunjukkan kemurnian sempurna — tidak ada ketidakpastian sama sekali.

---

#### Jawaban Soal 4 ⭐

| Komponen | Penjelasan |
|----------|------------|
| **Root Node** | Node paling atas pada tree, berisi atribut pertama yang diuji. Dipilih berdasarkan Information Gain tertinggi. Semua data mengalir melalui node ini. |
| **Internal Node** | Node di antara root dan leaf. Merepresentasikan pengujian terhadap suatu atribut. Data dibagi berdasarkan nilai atribut tersebut. |
| **Branch** | Cabang yang menghubungkan node. Merepresentasikan hasil dari pengujian atribut (nilai atribut tertentu). |
| **Leaf Node** | Node paling bawah (terminal). Merepresentasikan keputusan akhir, yaitu label kelas yang diberikan kepada data yang mencapai node ini. |

---

#### Jawaban Soal 5 ⭐⭐

**Dataset S:** 6 sampel, 3 Ancaman, 3 Aman

*Step 1:* Hitung proporsi setiap kelas

$$p(Ancaman) = 3/6 = 0.5$$
$$p(Aman) = 3/6 = 0.5$$

*Step 2:* Hitung entropy

$$H(S) = -p(Ancaman) \log_2 p(Ancaman) - p(Aman) \log_2 p(Aman)$$
$$H(S) = -0.5 \log_2(0.5) - 0.5 \log_2(0.5)$$
$$H(S) = -0.5 \times (-1) - 0.5 \times (-1)$$
$$H(S) = 0.5 + 0.5 = 1.0$$

**Jawaban:** Entropy awal H(S) = 1.0 (maksimum untuk dua kelas), menunjukkan data terbagi rata.

---

#### Jawaban Soal 6 ⭐⭐

**Langkah 1: IG untuk atribut Kecepatan**

Partisi berdasarkan Kecepatan:
- Kecepatan = Tinggi: {1, 2, 5} → 3 Ancaman, 0 Aman
- Kecepatan = Rendah: {3, 4, 6} → 0 Ancaman, 3 Aman

Entropy masing-masing partisi:
$$H(S_{Tinggi}) = -1 \log_2(1) - 0 = 0$$
$$H(S_{Rendah}) = -0 - 1 \log_2(1) = 0$$

Entropy setelah split:
$$H(S|Kecepatan) = \frac{3}{6} \times 0 + \frac{3}{6} \times 0 = 0$$

Information Gain:
$$IG(S, Kecepatan) = H(S) - H(S|Kecepatan) = 1.0 - 0 = 1.0$$

**Langkah 2: IG untuk atribut Altitude**

Partisi berdasarkan Altitude:
- Altitude = Tinggi: {1, 3, 5} → 2 Ancaman, 1 Aman
- Altitude = Rendah: {2, 4, 6} → 1 Ancaman, 2 Aman

Entropy masing-masing:
$$H(S_{Tinggi}) = -(2/3)\log_2(2/3) - (1/3)\log_2(1/3)$$
$$= -0.667 \times (-0.585) - 0.333 \times (-1.585) = 0.390 + 0.528 = 0.918$$

$$H(S_{Rendah}) = -(1/3)\log_2(1/3) - (2/3)\log_2(2/3) = 0.918$$

Entropy setelah split:
$$H(S|Altitude) = \frac{3}{6} \times 0.918 + \frac{3}{6} \times 0.918 = 0.918$$

Information Gain:
$$IG(S, Altitude) = 1.0 - 0.918 = 0.082$$

**Kesimpulan:** Kecepatan sebagai root node karena IG(Kecepatan) = 1.0 > IG(Altitude) = 0.082. Kecepatan memisahkan data secara sempurna.

---

#### Jawaban Soal 7 ⭐⭐

**Overfitting:**
- Model terlalu kompleks (tree sangat dalam)
- Performa sangat baik pada data training tetapi buruk pada data baru
- Model "menghafal" noise dan detail spesifik data training
- **Dampak:** False confidence — model tampak akurat tapi gagal di lapangan

**Underfitting:**
- Model terlalu sederhana (tree sangat dangkal)
- Performa buruk baik pada data training maupun data baru
- Model tidak mampu menangkap pola yang ada
- **Dampak:** Model tidak berguna karena tidak menangkap informasi yang relevan

**Teknik Pruning:**
- **Pre-pruning:** Menghentikan pertumbuhan tree lebih awal (batasi kedalaman, minimum sampel per leaf)
- **Post-pruning:** Membiarkan tree tumbuh penuh lalu memangkas cabang yang tidak signifikan

Pruning mengurangi kompleksitas tree sehingga model tidak terlalu spesifik terhadap data training, meningkatkan kemampuan generalisasi pada data baru.

---

#### Jawaban Soal 8 ⭐⭐

**Data:**
- Total email: 20 (8 Spam, 12 Bukan Spam)
- P(Spam) = 8/20 = 0.4
- P(Bukan Spam) = 12/20 = 0.6

**Likelihood untuk kata "gratis" muncul:**
- P(gratis | Spam) = 6/8 = 0.75
- P(gratis | Bukan Spam) = 2/12 = 0.167

**Likelihood untuk kata "rapat" TIDAK muncul:**
- P(¬rapat | Spam) = (8−1)/8 = 7/8 = 0.875
- P(¬rapat | Bukan Spam) = (12−8)/12 = 4/12 = 0.333

**Naive Bayes — hitung P(kelas | evidence):**

$$P(Spam | gratis, \neg rapat) \propto P(Spam) \times P(gratis|Spam) \times P(\neg rapat|Spam)$$
$$= 0.4 \times 0.75 \times 0.875 = 0.2625$$

$$P(Bukan Spam | gratis, \neg rapat) \propto P(Bukan Spam) \times P(gratis|Bukan Spam) \times P(\neg rapat|Bukan Spam)$$
$$= 0.6 \times 0.167 \times 0.333 = 0.0334$$

**Normalisasi:**
$$P(Spam | evidence) = \frac{0.2625}{0.2625 + 0.0334} = \frac{0.2625}{0.2959} = 0.887$$

$$P(Bukan Spam | evidence) = \frac{0.0334}{0.2959} = 0.113$$

**Jawaban:** Email diklasifikasikan sebagai **Spam** dengan probabilitas 88.7%.

---

#### Jawaban Soal 9 ⭐⭐

**Mengapa Laplace Smoothing diperlukan:**

Pada Naive Bayes, jika suatu fitur tidak pernah muncul bersama kelas tertentu di data training, maka P(fitur|kelas) = 0. Karena Naive Bayes mengalikan semua probabilitas, satu probabilitas nol menyebabkan seluruh hasil menjadi nol — terlepas dari probabilitas fitur lainnya.

**Contoh numerik tanpa Laplace Smoothing:**

Misalkan kita punya data 10 email spam. Kata "militer" tidak pernah muncul di email spam.
- P("militer" | Spam) = 0/10 = 0

Email baru mengandung kata "gratis" (P=0.8) DAN "militer":
$$P(Spam|email) \propto P(Spam) \times P("gratis"|Spam) \times P("militer"|Spam)$$
$$= 0.5 \times 0.8 \times 0 = 0$$

Meskipun "gratis" sangat mengindikasikan spam, satu kata "militer" membuat seluruh probabilitas nol.

**Dengan Laplace Smoothing (α = 1):**

$$P("militer"|Spam) = \frac{0 + 1}{10 + 2} = \frac{1}{12} = 0.083$$

Sekarang:
$$P(Spam|email) \propto 0.5 \times 0.8 \times 0.083 = 0.033$$

Hasilnya bukan nol lagi, dan fitur-fitur lain tetap dapat berkontribusi pada keputusan.

---

#### Jawaban Soal 10 ⭐⭐

**Data:**

| x | y | x² | xy |
|---|---|----|----|
| 2 | 55 | 4 | 110 |
| 4 | 62 | 16 | 248 |
| 6 | 70 | 36 | 420 |
| 8 | 78 | 64 | 624 |
| **Σ** | **Σx=20** | **Σy=265** | **Σx²=120** | **Σxy=1402** |

n = 4, $\bar{x}$ = 20/4 = 5, $\bar{y}$ = 265/4 = 66.25

**Hitung w₁ (slope):**

$$w_1 = \frac{n\sum xy - \sum x \sum y}{n\sum x^2 - (\sum x)^2}$$
$$w_1 = \frac{4(1402) - (20)(265)}{4(120) - (20)^2}$$
$$w_1 = \frac{5608 - 5300}{480 - 400} = \frac{308}{80} = 3.85$$

**Hitung w₀ (intercept):**

$$w_0 = \bar{y} - w_1 \bar{x} = 66.25 - 3.85 \times 5 = 66.25 - 19.25 = 47.0$$

**Model:** ŷ = 47.0 + 3.85x

**Prediksi untuk x = 10:**
$$\hat{y} = 47.0 + 3.85 \times 10 = 47.0 + 38.5 = 85.5$$

**Jawaban:** w₁ = 3.85, w₀ = 47.0. Prediksi akurasi tembakan untuk 10 jam latihan = 85.5%. Setiap tambahan 1 jam latihan meningkatkan akurasi sekitar 3.85%.

---

#### Jawaban Soal 11 ⭐⭐

**Dari confusion matrix:** TP = 42, FN = 8, FP = 5, TN = 145

**(a) Accuracy:**
$$Accuracy = \frac{TP + TN}{TP + TN + FP + FN} = \frac{42 + 145}{42 + 145 + 5 + 8} = \frac{187}{200} = 0.935 = 93.5\%$$

**(b) Precision:**
$$Precision = \frac{TP}{TP + FP} = \frac{42}{42 + 5} = \frac{42}{47} = 0.894 = 89.4\%$$

**(c) Recall:**
$$Recall = \frac{TP}{TP + FN} = \frac{42}{42 + 8} = \frac{42}{50} = 0.840 = 84.0\%$$

**(d) F1-Score:**
$$F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall} = 2 \times \frac{0.894 \times 0.840}{0.894 + 0.840} = 2 \times \frac{0.751}{1.734} = 0.866 = 86.6\%$$

**Interpretasi:** Sistem memiliki akurasi tinggi (93.5%), tetapi recall 84% berarti 8 dari 50 intrusi aktual tidak terdeteksi — ini berpotensi berbahaya dalam konteks keamanan siber militer. Peningkatan recall harus diprioritaskan.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Langkah-langkah Algoritma ID3:**

1. Hitung entropy seluruh dataset
2. Untuk setiap atribut, hitung Information Gain
3. Pilih atribut dengan IG tertinggi sebagai node
4. Bagi dataset berdasarkan nilai atribut terpilih
5. Ulangi secara rekursif untuk setiap subset
6. Berhenti jika semua data dalam subset satu kelas (leaf) atau tidak ada atribut tersisa

**Langkah 1: Entropy awal**

Dataset: 4 Ya, 4 Tidak → p(Ya)=0.5, p(Tidak)=0.5

$$H(S) = -0.5 \log_2(0.5) - 0.5 \log_2(0.5) = 1.0$$

**Langkah 2: IG untuk setiap atribut**

**Atribut Cuaca:**
- Cerah: {1,2,7} → 3 Ya, 0 Tidak → H = 0
- Mendung: {3,6} → 1 Ya, 1 Tidak → H = 1.0
- Hujan: {4,5,8} → 0 Ya, 3 Tidak → H = 0

$$H(S|Cuaca) = \frac{3}{8}(0) + \frac{2}{8}(1.0) + \frac{3}{8}(0) = 0.25$$

$$IG(S, Cuaca) = 1.0 - 0.25 = 0.75$$

**Atribut Angin:**
- Lemah: {1,3,4,7} → 3 Ya, 1 Tidak → H = −(3/4)log₂(3/4) − (1/4)log₂(1/4) = 0.811
- Kencang: {2,5,6} → 1 Ya, 2 Tidak → H = −(1/3)log₂(1/3) − (2/3)log₂(2/3) = 0.918

$$H(S|Angin) = \frac{4}{8}(0.811) + \frac{3}{8}(0.918) = 0.406 + 0.344 = 0.750 $$

$$ IG(S, Angin) = 1.0 - 0.750 = 0.250 $$

**Atribut Visibilitas:**
- Baik: {1,2,3,8} → 3 Ya, 1 Tidak → H = 0.811
- Buruk: {4,5,6,7} → 1 Ya, 3 Tidak → H = 0.811

$$H(S|Visibilitas) = \frac{4}{8}(0.811) + \frac{4}{8}(0.811) = 0.811$$

$$IG(S, Visibilitas) = 1.0 - 0.811 = 0.189$$

**Langkah 3: Pilih root node**

| Atribut | Information Gain |
|---------|-----------------|
| **Cuaca** | **0.75** ← Tertinggi |
| Angin | 0.250 |
| Visibilitas | 0.189 |

Root node = **Cuaca**

**Decision Tree hasil:**

```
          [Cuaca?]
         /    |    \
     Cerah  Mendung  Hujan
       |      |       |
     [Ya]  [Angin?] [Tidak]
           /     \
        Lemah  Kencang
          |      |
        [Ya]  [Tidak]
```

- Cuaca = Cerah → Misi Ya
- Cuaca = Hujan → Misi Tidak
- Cuaca = Mendung & Angin = Lemah → Misi Ya
- Cuaca = Mendung & Angin = Kencang → Misi Tidak

---

#### Jawaban Soal 13 ⭐⭐⭐

| Aspek | Decision Tree | Naive Bayes |
|-------|---------------|-------------|
| **(a) Asumsi** | Tidak ada asumsi tentang independensi fitur. Menangkap interaksi antar atribut secara alami. | Mengasumsikan semua fitur independen secara kondisional given kelas. Asumsi ini jarang benar di dunia nyata. |
| **(b) Atribut kontinu** | ID3 hanya menangani kategorik, tetapi C4.5 dan CART menangani kontinu dengan threshold splitting. | Menangani kontinu dengan asumsi distribusi (umumnya Gaussian) atau discretisasi. |
| **(c) Interpretabilitas** | Sangat interpretable — tree dapat divisualisasikan dan aturan mudah dipahami oleh non-technical user. | Cukup interpretable — probabilitas setiap fitur dapat dilihat, tetapi tidak seintuisif tree. |
| **(d) Dataset kecil** | Rentan overfitting pada dataset kecil jika tidak dilakukan pruning. | Bekerja cukup baik pada dataset kecil karena model probabilistik sederhana dan robust. |
| **(e) Kasus pertahanan** | Klasifikasi ancaman udara dengan aturan taktis yang harus bisa dijelaskan ke komandan (rules of engagement). | Filtering spam/ancaman siber dengan banyak fitur independen (kata-kata dalam email, signature malware). |

---

#### Jawaban Soal 14 ⭐⭐⭐

**Mengapa recall lebih penting untuk deteksi rudal:**

Recall = TP/(TP+FN) mengukur berapa persen rudal yang benar-benar terdeteksi. False Negative (FN) pada deteksi rudal berarti rudal lolos tanpa terdeteksi — konsekuensinya bisa berupa kerusakan fatal dan korban jiwa. Sebaliknya, False Positive (FP, alarm palsu) hanya menyebabkan pemborosan resources.

**Skenario (a): Precision tinggi, Recall rendah**

|                | Prediksi: Rudal | Prediksi: Bukan |
|----------------|:-:|:-:|
| **Aktual: Rudal** | 5 | 15 |
| **Aktual: Bukan** | 1 | 179 |

- Precision = 5/6 = 83.3% (prediksi rudal hampir selalu benar)
- Recall = 5/20 = 25% (75% rudal aktual TIDAK terdeteksi!)

**Konsekuensi:** 15 dari 20 rudal lolos tanpa terdeteksi. Sistem sangat presisi tapi melewatkan mayoritas ancaman — kegagalan fatal.

**Skenario (b): Recall tinggi, Precision sedang**

|                | Prediksi: Rudal | Prediksi: Bukan |
|----------------|:-:|:-:|
| **Aktual: Rudal** | 19 | 1 |
| **Aktual: Bukan** | 12 | 168 |

- Precision = 19/31 = 61.3% (beberapa alarm palsu)
- Recall = 19/20 = 95% (hampir semua rudal terdeteksi!)

**Konsekuensi:** Hanya 1 rudal yang lolos. Ada 12 alarm palsu yang membuang resources, tetapi ini jauh lebih baik daripada kehilangan target. Dalam pertahanan, 95% recall jauh lebih berharga dari 83% precision.

---

#### Jawaban Soal 15 ⭐⭐⭐

**K-Fold Cross-Validation:**

1. Bagi dataset menjadi K subset (fold) berukuran sama
2. Untuk setiap iterasi i (i = 1 hingga K):
   - Gunakan fold ke-i sebagai test set
   - Gabungkan K−1 fold lainnya sebagai training set
   - Latih model dan catat akurasi pada test set
3. Hitung rata-rata akurasi dari K iterasi

**Keunggulan dibanding single train/test split:**
- Setiap data menjadi test set tepat satu kali → evaluasi tidak bias
- Hasil lebih stabil dan reliable (rata-rata dari K percobaan)
- Memanfaatkan seluruh data untuk training DAN testing

**Kapan menggunakan Stratified K-Fold:**
Ketika distribusi kelas tidak seimbang. Stratified memastikan setiap fold memiliki proporsi kelas yang sama dengan dataset asli.

**Contoh dengan dataset radar (1000 sampel: 900 normal, 100 ancaman):**

Tanpa Stratified (random split menjadi 5 fold):
- Fold 1: mungkin 195 normal, 5 ancaman (sangat sedikit ancaman)
- Fold 2: mungkin 170 normal, 30 ancaman (terlalu banyak)
- Evaluasi menjadi tidak konsisten antar fold

Dengan Stratified 5-Fold:
- Setiap fold: 180 normal + 20 ancaman (proporsi 90:10 terjaga)
- Evaluasi konsisten dan representatif

Stratified penting karena fold tanpa sampel kelas minoritas tidak akan bisa menguji kemampuan model mendeteksi ancaman, menghasilkan evaluasi yang menyesatkan.

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Klasifikasi Ancaman Udara

**1a. Komponen T, P, E (10 poin)**

| Komponen | Spesifikasi |
|----------|-------------|
| **Task (T)** | Mengklasifikasikan objek udara yang terdeteksi radar ke dalam 4 kategori: Pesawat Sipil, Pesawat Militer Kawan, Pesawat Militer Asing, atau Drone/UAV Tidak Dikenal |
| **Performance (P)** | Akurasi klasifikasi keseluruhan, recall per kelas (terutama untuk kelas Pesawat Militer Asing dan Drone/UAV), F1-Score weighted, dan false alarm rate |
| **Experience (E)** | Database 500 catatan historis radar yang sudah dilabeli oleh operator terlatih, terdiri dari 6 atribut (Kecepatan, Altitude, RCS, Transponder, Pola Terbang, Zona) |

**1b. Masalah Distribusi Tidak Seimbang (15 poin)**

**Mengapa distribusi tidak seimbang bermasalah:**

Kelas Pesawat Sipil mendominasi (60%), sedangkan kelas kritis (Militer Asing dan Drone) masing-masing hanya 10%. Model yang selalu memprediksi "Pesawat Sipil" sudah mencapai accuracy 60% tanpa belajar apa pun. Model cenderung mengabaikan kelas minoritas.

**Metrik yang tepat:**
- **Accuracy saja TIDAK cukup** karena menyembunyikan kegagalan pada kelas minoritas
- **Recall per kelas** — terutama untuk Pesawat Militer Asing (tidak terdeteksi = fatal) dan Drone/UAV
- **F1-Score (weighted atau macro-averaged)** — menyeimbangkan precision dan recall
- **Confusion matrix detail** — melihat pola kesalahan antar kelas
- **Precision untuk kelas Sipil** — False Positive (objek non-sipil dianggap sipil) bisa fatal

**Rekomendasi tambahan:** Gunakan teknik class weighting atau oversampling kelas minoritas (SMOTE) saat training.

**1c. Decision Tree: Kelebihan, Kekurangan, dan Root Node (15 poin)**

**Kelebihan:**
- Interpretable — rules bisa dipahami operator (misal: "IF Transponder=Tidak Ada AND RCS<1m² THEN Drone")
- Tidak memerlukan asumsi distribusi data
- Menangkap interaksi antar atribut (misal: kombinasi kecepatan tinggi + altitude tinggi)
- Dapat menangani atribut campuran (numerik dan kategorik)

**Kekurangan:**
- Rentan overfitting dengan 500 sampel dan 6 atribut
- Kelas minoritas (Militer Asing, Drone) mungkin tidak terwakili cukup di beberapa split
- Sensitif terhadap noise pada data radar
- Keputusan boundary terlalu "kotak-kotak" (axis-aligned)

**Root node yang diprediksi:** Atribut **Transponder** kemungkinan memiliki IG tertinggi karena:
- Pesawat sipil dan militer kawan umumnya memiliki transponder aktif (IFF: Kawan)
- Pesawat militer asing: Netral atau Tidak Ada
- Drone: Tidak Ada
- Transponder langsung memisahkan "friendly" vs "potentially hostile" secara signifikan

**1d. Masalah Naive Bayes dan Independence (10 poin)**

**Masalah utama:** Asumsi conditional independence Naive Bayes dilanggar oleh beberapa pasangan atribut:

| Pasangan Atribut | Mengapa TIDAK Independen |
|------------------|--------------------------|
| Kecepatan & Altitude | Pesawat cepat biasanya terbang tinggi (jet vs helikopter) |
| Kecepatan & Pola Terbang | Objek berkecepatan tinggi biasanya terbang lurus, drone sering loiter |
| Transponder & Zona | Pesawat di ADIZ lebih wajib transponder aktif, di zona territorial bisa tanpa |
| RCS & Kecepatan | Pesawat besar (RCS besar) biasanya lebih lambat dari fighter (RCS kecil, kecepatan tinggi) |

Pelanggaran asumsi independence menyebabkan probabilitas posterior yang dihitung Naive Bayes kurang akurat, terutama untuk kasus borderline.

**1e. Stratified 10-Fold CV (15 poin)**

**Mengapa Stratified diperlukan:**
Distribusi kelas sangat tidak seimbang (60:20:10:10). Random fold bisa menghasilkan fold tanpa sampel kelas minoritas (Militer Asing atau Drone), membuat evaluasi untuk kelas tersebut tidak valid.

**Jumlah sampel per fold:**

Total 500 sampel, 10 fold → 50 sampel per fold

| Kelas | Total | Per Fold (Stratified) |
|-------|-------|----------------------|
| Pesawat Sipil | 300 | 30 |
| Militer Kawan | 100 | 10 |
| Militer Asing | 50 | 5 |
| Drone/UAV | 50 | 5 |
| **Total per fold** | **500** | **50** |

Setiap fold menjaga proporsi 60:20:10:10 sehingga model dilatih dan diuji pada distribusi yang representatif. Setiap kelas kritis (Militer Asing, Drone) tetap memiliki 5 sampel test di setiap fold.

---

#### Studi Kasus 2: Prediksi Kesiapan Tempur Unit Militer

**2a. Entropy dan Information Gain Personel (15 poin)**

**Entropy awal:**

p(Siap) = 130/200 = 0.65, p(Tidak) = 70/200 = 0.35

$$H(S) = -0.65 \log_2(0.65) - 0.35 \log_2(0.35)$$
$$= -0.65 \times (-0.621) - 0.35 \times (-1.515)$$
$$= 0.404 + 0.530 = 0.934$$

**IG atribut Personel (threshold ≥80%):**

Partisi:
- Personel ≥80%: 130 unit (110 Siap, 20 Tidak Siap)
- Personel <80%: 70 unit (20 Siap, 50 Tidak Siap)

Entropy masing-masing:

$$H(S_{\geq 80}) = -(110/130)\log_2(110/130) - (20/130)\log_2(20/130)$$
$$= -(0.846)\log_2(0.846) - (0.154)\log_2(0.154)$$
$$= -0.846 \times (-0.242) - 0.154 \times (-2.700)$$
$$= 0.205 + 0.416 = 0.621$$

$$H(S_{<80}) = -(20/70)\log_2(20/70) - (50/70)\log_2(50/70)$$
$$= -(0.286)\log_2(0.286) - (0.714)\log_2(0.714)$$
$$= -0.286 \times (-1.807) - 0.714 \times (-0.485)$$
$$= 0.517 + 0.346 = 0.863$$

Entropy setelah split:
$$H(S|Personel) = \frac{130}{200} \times 0.621 + \frac{70}{200} \times 0.863$$
$$= 0.65 \times 0.621 + 0.35 \times 0.863 = 0.404 + 0.302 = 0.706$$

Information Gain:
$$IG(S, Personel) = 0.934 - 0.706 = 0.228$$

**2b. Metrik Evaluasi (15 poin)**

**Dari confusion matrix:** TP = 22, FN = 4, FP = 3, TN = 11

(Positif = Siap, Negatif = Tidak Siap)

**(a) Accuracy:**
$$Accuracy = \frac{22 + 11}{22 + 11 + 3 + 4} = \frac{33}{40} = 0.825 = 82.5\%$$

**(b) Precision:**
$$Precision = \frac{22}{22 + 3} = \frac{22}{25} = 0.880 = 88.0\%$$

**(c) Recall:**
$$Recall = \frac{22}{22 + 4} = \frac{22}{26} = 0.846 = 84.6\%$$

**(d) F1-Score:**
$$F1 = 2 \times \frac{0.880 \times 0.846}{0.880 + 0.846} = 2 \times \frac{0.744}{1.726} = 0.863 = 86.3\%$$

**Interpretasi:** Model cukup baik secara keseluruhan (82.5%). Precision 88% berarti ketika model memprediksi unit "Siap", sebagian besar memang siap. Recall 84.6% berarti 4 unit yang sebenarnya siap diprediksi tidak siap (konservatif). Namun 3 unit tidak siap diprediksi siap — ini yang lebih berbahaya.

**2c. Analisis Risiko dan Rekomendasi (15 poin)**

**Metrik paling relevan: Precision pada kelas "Siap"**

Pernyataan "lebih berbahaya menilai unit TIDAK siap sebagai Siap" berarti False Positive (FP) adalah risiko utama. FP terjadi ketika unit tidak siap diprediksi siap — unit ini bisa dikirim ke operasi tanpa kesiapan memadai, membahayakan misi dan personel.

Precision = TP/(TP+FP) = 22/25 = 88%. Artinya 12% unit yang diprediksi "Siap" sebenarnya tidak siap — ini berpotensi berbahaya.

**Atau, dari perspektif kelas "Tidak Siap":**

Recall pada kelas "Tidak Siap" = TN/(TN+FP) = 11/(11+3) = 78.6%

Artinya 3 dari 14 unit tidak siap lolos sebagai "Siap" — 21.4% unit tidak siap tidak teridentifikasi.

**Rekomendasi perbaikan:**
1. **Adjust threshold** — turunkan threshold prediksi "Siap" agar lebih konservatif (bias ke prediksi "Tidak Siap" jika ragu)
2. **Class weighting** — berikan bobot lebih besar untuk kesalahan FP (unit tidak siap dinilai siap)
3. **Two-stage verification** — unit yang diprediksi "Siap" dengan confidence rendah harus melalui evaluasi manual tambahan

**2d. Regresi Linear untuk Prediksi Jam Latihan (10 poin)**

| x (Personel) | y (Latihan) | x² | xy |
|---|---|---|---|
| 60 | 120 | 3600 | 7200 |
| 70 | 100 | 4900 | 7000 |
| 80 | 80 | 6400 | 6400 |
| 90 | 60 | 8100 | 5400 |
| 95 | 50 | 9025 | 4750 |
| **Σ** | **395** | **410** | **32025** | **30750** |

n = 5, $\bar{x}$ = 395/5 = 79, $\bar{y}$ = 410/5 = 82

**Hitung w₁:**

$$w_1 = \frac{n\sum xy - \sum x \sum y}{n\sum x^2 - (\sum x)^2}$$
$$= \frac{5(30750) - (395)(410)}{5(32025) - (395)^2}$$
$$= \frac{153750 - 161950}{160125 - 156025} = \frac{-8200}{4100} = -2.0$$

**Hitung w₀:**

$$w_0 = \bar{y} - w_1 \bar{x} = 82 - (-2.0)(79) = 82 + 158 = 240$$

**Model:** ŷ = 240 − 2.0x

**Interpretasi slope:** Slope w₁ = −2.0 berarti setiap peningkatan 1% tingkat kesiapan personel, jam latihan optimal yang diperlukan berkurang 2 jam. Unit dengan personel lebih lengkap memerlukan latihan lebih sedikit untuk mencapai standar kesiapan, karena personel berpengalaman sudah memiliki kompetensi dasar.

**2e. 5-Fold CV dan Stabilitas Model (10 poin)**

**Langkah penerapan 5-Fold CV pada 200 unit:**

1. Bagi 200 unit menjadi 5 fold, masing-masing 40 unit
2. Gunakan **Stratified** agar setiap fold: ~26 Siap + ~14 Tidak Siap (proporsi 65:35 terjaga)
3. Iterasi 1: fold-1 sebagai test, fold 2-5 sebagai training (160 unit)
4. Ulangi hingga iterasi 5
5. Hitung rata-rata dan standar deviasi akurasi

**Hal yang harus diperhatikan:**
- Stratified split agar proporsi kelas terjaga
- Pastikan tidak ada data leakage (unit yang sama tidak boleh ada di train dan test)
- Normalisasi/scaling fitur numerik harus dilakukan DALAM setiap fold (fit pada train, transform pada test)

**Apakah model stabil?**

Rata-rata akurasi = 82%, standar deviasi = 5%

Rentang akurasi: 82% ± 5% → antara 77% dan 87%

Model **cukup stabil** tetapi bukan sangat stabil. Standar deviasi 5% menunjukkan ada variasi antar fold yang bisa disebabkan oleh:
- Dataset relatif kecil (200 unit, 40 per fold)
- Beberapa fold mungkin memiliki distribusi fitur yang berbeda

Untuk aplikasi militer kritis, sebaiknya standar deviasi di bawah 3%. Solusi: kumpulkan lebih banyak data, atau gunakan 10-fold CV yang umumnya lebih stabil.

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 125 poin

### Studi Kasus
- Studi Kasus 1: 65 poin
- Studi Kasus 2: 65 poin
- Total: 130 poin

### Total Keseluruhan: 295 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
