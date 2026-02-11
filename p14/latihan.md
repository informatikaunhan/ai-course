# Latihan Pertemuan 14: Unsupervised Learning dan Reinforcement Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 14  
**Topik:** Unsupervised Learning dan Reinforcement Learning  
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
Perbedaan utama antara supervised learning dan unsupervised learning adalah:

A. Supervised learning lebih cepat daripada unsupervised learning  
B. Unsupervised learning memerlukan data berlabel sedangkan supervised tidak  
C. Supervised learning menggunakan data berlabel sedangkan unsupervised learning tidak  
D. Unsupervised learning hanya dapat digunakan untuk klasifikasi  
E. Supervised learning tidak memerlukan data training

---

### Soal 2
Manakah yang termasuk tugas unsupervised learning?

A. Klasifikasi email sebagai spam atau bukan  
B. Prediksi harga saham  
C. Pengelompokan dokumen berdasarkan topik tanpa kategori yang ditentukan  
D. Pengenalan angka tulisan tangan  
E. Prediksi cuaca besok

---

### Soal 3
Pada algoritma K-Means, langkah "Assignment Step" berarti:

A. Memilih K centroid awal secara acak  
B. Menghitung rata-rata setiap klaster  
C. Menetapkan setiap data ke klaster dengan centroid terdekat  
D. Menentukan jumlah klaster optimal  
E. Menghapus outlier dari dataset

---

### Soal 4
Diberikan titik P(3, 4) dan centroid μ₁(1, 1) serta μ₂(5, 5). Titik P akan ditetapkan ke klaster:

A. Klaster 1 karena d(P, μ₁) = √13 < d(P, μ₂) = √5  
B. Klaster 2 karena d(P, μ₂) = √5 < d(P, μ₁) = √13  
C. Klaster 1 karena d(P, μ₁) = √5 < d(P, μ₂) = √13  
D. Klaster 2 karena keduanya sama jauh  
E. Tidak dapat ditentukan

---

### Soal 5
K-Means pasti konvergen ke:

A. Global optimum  
B. Local optimum  
C. Solusi optimal jika K dipilih dengan benar  
D. Solusi yang sama setiap kali dijalankan  
E. Hasil yang selalu identik dengan hierarchical clustering

---

### Soal 6
Pada Elbow Method, jumlah klaster optimal dipilih pada titik dimana:

A. WCSS bernilai nol  
B. WCSS bernilai maksimum  
C. Penurunan WCSS mulai melambat drastis (membentuk "siku")  
D. Silhouette score bernilai negatif  
E. Jumlah iterasi K-Means paling sedikit

---

### Soal 7
Silhouette score bernilai mendekati +1 menunjukkan:

A. Data berada di perbatasan antara dua klaster  
B. Data salah ditempatkan di klaster yang jauh  
C. Data berada tepat di centroid  
D. Data sangat cocok dengan klasternya dan jauh dari klaster lain  
E. Jumlah klaster terlalu banyak

---

### Soal 8
Pada hierarchical clustering dengan single linkage, jarak antar dua klaster dihitung berdasarkan:

A. Jarak maksimum antara anggota kedua klaster  
B. Jarak rata-rata antara anggota kedua klaster  
C. Jarak minimum antara anggota kedua klaster  
D. Jarak antar centroid kedua klaster  
E. Jarak median antara anggota kedua klaster

---

### Soal 9
Kelemahan utama single linkage dibandingkan complete linkage adalah:

A. Lebih lambat secara komputasi  
B. Rentan terhadap efek chaining  
C. Tidak dapat menangani data berdimensi tinggi  
D. Selalu menghasilkan klaster yang terlalu kecil  
E. Tidak deterministik

---

### Soal 10
Tujuan utama PCA (Principal Component Analysis) adalah:

A. Mengelompokkan data ke dalam klaster  
B. Memprediksi label data  
C. Mereduksi dimensi data sambil mempertahankan varians maksimum  
D. Menghitung jarak antar titik data  
E. Mendeteksi anomali dalam dataset

---

### Soal 11
Dalam reinforcement learning, agent belajar melalui:

A. Data berlabel yang diberikan oleh guru  
B. Interaksi dengan lingkungan dan menerima reward/penalty  
C. Menghitung jarak antar data point  
D. Menemukan pola tersembunyi dalam data tanpa label  
E. Membandingkan output dengan target yang diinginkan

---

### Soal 12
Komponen MDP (Markov Decision Process) yang BUKAN merupakan bagian dari tuple definisinya adalah:

A. Himpunan state (S)  
B. Himpunan action (A)  
C. Fungsi transisi T(s'|s, a)  
D. Learning rate (α)  
E. Discount factor (γ)

---

### Soal 13
Markov Property menyatakan bahwa:

A. Semua state memiliki probabilitas yang sama  
B. State masa depan hanya bergantung pada state saat ini, bukan sejarah lengkap  
C. Reward selalu positif  
D. Agent harus mengeksplorasi semua state sebelum exploitasi  
E. Setiap episode memiliki panjang yang sama

---

### Soal 14
Pada Q-Learning, jika Q(S2, R) = 5.0, α = 0.5, reward = 10, γ = 0.9, dan max Q(S3, ·) = 0 (terminal state), maka Q(S2, R) yang baru adalah:

A. 5.0  
B. 7.5  
C. 10.0  
D. 2.5  
E. 15.0

---

### Soal 15
Discount factor γ = 0 pada reinforcement learning berarti agent:

A. Tidak pernah belajar  
B. Hanya memperhitungkan reward segera (myopic)  
C. Selalu memilih aksi random  
D. Memberikan bobot sama untuk semua reward masa depan  
E. Tidak pernah mengeksplorasi

---

### Soal 16
Strategi ε-greedy dalam reinforcement learning berarti:

A. Selalu memilih aksi dengan Q-value tertinggi  
B. Selalu memilih aksi secara random  
C. Dengan probabilitas ε memilih aksi random, sisanya memilih Q-value terbaik  
D. Mengurangi learning rate setiap episode  
E. Memilih aksi berdasarkan suhu (temperature)

---

### Soal 17
Manakah perbandingan yang BENAR antara K-Means dan Hierarchical Clustering?

A. K-Means memerlukan K, Hierarchical tidak  
B. K-Means deterministik, Hierarchical tidak  
C. Hierarchical lebih efisien untuk data besar  
D. K-Means menghasilkan dendrogram  
E. Hierarchical hanya menghasilkan klaster spherical

---

### Soal 18
Dalam konteks pertahanan, clustering sinyal komunikasi musuh yang dicegat termasuk paradigma:

A. Supervised Learning  
B. Unsupervised Learning  
C. Reinforcement Learning  
D. Semi-supervised Learning  
E. Transfer Learning

---

### Soal 19
Manakah yang merupakan contoh aplikasi reinforcement learning dalam bidang pertahanan?

A. Klasifikasi citra satelit  
B. Pengelompokan pola serangan siber  
C. Optimalisasi strategi manuver drone otonom  
D. Reduksi dimensi data radar  
E. Prediksi jumlah personel yang dibutuhkan

---

### Soal 20
Arsitektur deep learning yang paling sesuai untuk pemrosesan citra adalah:

A. Recurrent Neural Network (RNN)  
B. Convolutional Neural Network (CNN)  
C. Transformer  
D. Autoencoder  
E. Generative Adversarial Network (GAN)

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara supervised learning, unsupervised learning, dan reinforcement learning dari segi data, feedback, dan tujuan! Berikan masing-masing satu contoh aplikasi!

---

### Soal 2 ⭐
Sebutkan dan jelaskan empat langkah utama dalam algoritma K-Means!

---

### Soal 3 ⭐
Hitung jarak Euclidean antara titik A(1, 5) dan B(4, 1)! Tunjukkan langkah perhitungannya!

---

### Soal 4 ⭐
Jelaskan mengapa K-Means sensitif terhadap inisialisasi centroid awal dan sebutkan satu solusi untuk mengatasinya!

---

### Soal 5 ⭐⭐
Lakukan satu iterasi K-Means (K=2) pada data berikut dengan centroid awal μ₁=(0, 0) dan μ₂=(6, 6)! Tunjukkan langkah assignment dan update centroid!

| Titik | x | y |
|-------|---|---|
| A | 1 | 2 |
| B | 2 | 3 |
| C | 5 | 6 |
| D | 6 | 5 |
| E | 3 | 4 |

---

### Soal 6 ⭐⭐
Diberikan hasil WCSS untuk berbagai nilai K berikut. Tentukan K optimal menggunakan Elbow Method dan jelaskan alasannya!

| K | WCSS |
|---|------|
| 1 | 500 |
| 2 | 300 |
| 3 | 150 |
| 4 | 130 |
| 5 | 120 |
| 6 | 115 |

---

### Soal 7 ⭐⭐
Lakukan agglomerative clustering (single linkage) pada data berikut! Tunjukkan matriks jarak dan urutan penggabungan!

| Titik | x | y |
|-------|---|---|
| A | 0 | 0 |
| B | 1 | 0 |
| C | 4 | 0 |
| D | 5 | 0 |

---

### Soal 8 ⭐⭐
Jelaskan perbedaan antara single linkage, complete linkage, dan average linkage pada hierarchical clustering! Kapan masing-masing metode lebih cocok digunakan?

---

### Soal 9 ⭐⭐
Sebuah robot patroli beroperasi di grid 1×4 dengan state {S1, S2, S3, S4}. S4 adalah base camp dengan reward +10. Setiap langkah mendapat reward -1. Actions: Left (L) dan Right (R). Formulasikan sebagai MDP!

---

### Soal 10 ⭐⭐
Jelaskan perbedaan antara exploration dan exploitation dalam reinforcement learning! Berikan contoh dilema exploration-exploitation pada drone pengintai militer!

---

### Soal 11 ⭐⭐⭐
Diberikan grid 1×3 dengan state {S1, S2, S3}. S3 adalah goal (reward +10), setiap langkah reward -1. Actions: Left (L) dan Right (R). Semua Q(s,a) awalnya 0. Dengan α=0.5 dan γ=0.9, lakukan Q-Learning untuk episode dengan path S1→R→S2→R→S3! Tunjukkan Q-table setelah episode!

---

### Soal 12 ⭐⭐⭐
Lanjutkan Soal 11 untuk episode kedua dengan path yang sama (S1→R→S2→R→S3). Tunjukkan perubahan Q-table dan analisis konvergensi!

---

### Soal 13 ⭐⭐⭐
Jelaskan pengaruh discount factor γ terhadap perilaku agent! Berikan contoh perhitungan V(S1) untuk grid S1→S2→S3 (reward -1 per langkah, +10 di S3) dengan γ=0 dan γ=0.9! Apa perbedaan perilaku agent?

---

### Soal 14 ⭐⭐⭐
Bandingkan K-Means dan Hierarchical Clustering dari segi: (a) kebutuhan input, (b) kompleksitas waktu, (c) bentuk klaster, (d) determinisme, dan (e) skalabilitas. Untuk setiap aspek, berikan skenario dimana masing-masing algoritma lebih unggul!

---

### Soal 15 ⭐⭐⭐
Jelaskan konsep PCA (Principal Component Analysis)! Apa tujuannya, bagaimana cara kerjanya secara umum, dan berikan contoh penerapannya dalam analisis data pertahanan!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Analisis Sinyal Intelijen dengan Clustering

**Latar Belakang:**

Unit Intelijen TNI bertugas menganalisis sinyal komunikasi yang dicegat dari berbagai sumber di wilayah perbatasan. Selama 30 hari operasi, sistem SIGINT (Signal Intelligence) berhasil mencegat 200 sinyal komunikasi. Setiap sinyal memiliki fitur-fitur berikut:
- Frekuensi (MHz)
- Durasi transmisi (detik)
- Kekuatan sinyal (dBm)
- Interval pengulangan (menit)

Data sampel dari 8 sinyal yang dicegat (sudah dinormalisasi 0-10):

| Sinyal | Frekuensi | Durasi | Kekuatan | Interval |
|--------|-----------|--------|----------|----------|
| S1 | 2 | 3 | 8 | 2 |
| S2 | 3 | 2 | 7 | 3 |
| S3 | 8 | 7 | 3 | 8 |
| S4 | 7 | 8 | 2 | 7 |
| S5 | 2 | 2 | 9 | 1 |
| S6 | 9 | 8 | 2 | 9 |
| S7 | 5 | 5 | 5 | 5 |
| S8 | 8 | 6 | 3 | 7 |

Tim intelijen mencurigai sinyal-sinyal ini berasal dari beberapa kelompok berbeda, namun tidak mengetahui berapa kelompok yang ada.

**Pertanyaan:**

**1a.** Jelaskan mengapa unsupervised learning (clustering) lebih sesuai daripada supervised learning untuk kasus ini! (10 poin)

**1b.** Lakukan satu iterasi K-Means (K=2) menggunakan sinyal S1 dan S3 sebagai centroid awal! Gunakan hanya fitur Frekuensi dan Durasi untuk penyederhanaan. Tunjukkan perhitungan jarak, assignment, dan update centroid! (20 poin)

**1c.** Berdasarkan data sampel, tentukan K optimal menggunakan analisis visual! Jika WCSS untuk K=2 adalah 120, K=3 adalah 45, K=4 adalah 38, dan K=5 adalah 35, berapa K yang Anda rekomendasikan? Jelaskan! (10 poin)

**1d.** Bandingkan penggunaan K-Means vs Hierarchical Clustering untuk kasus ini! Metode mana yang lebih sesuai? Pertimbangkan jumlah data (200 sinyal), kebutuhan akan jumlah klaster yang fleksibel, dan interpretabilitas hasil! (15 poin)

**1e.** Bagaimana PCA dapat membantu dalam analisis ini mengingat data memiliki 4 dimensi fitur? Jelaskan manfaat reduksi dimensi untuk visualisasi dan efisiensi clustering! (10 poin)

---

### Studi Kasus 2: Drone Otonom dengan Reinforcement Learning

**Latar Belakang:**

TNI Angkatan Udara mengembangkan drone otonom untuk misi pengintaian di wilayah perbatasan. Drone beroperasi pada grid 3×3 yang merepresentasikan area operasi:

```
┌────┬────┬────┐
│ S1 │ S2 │ S3 │
├────┼────┼────┤
│ S4 │ S5 │ S6 │
├────┼────┼────┤
│ S7 │ S8 │ S9 │
└────┴────┴────┘
```

**Spesifikasi:**
- S1 adalah posisi awal (home base)
- S9 adalah target pengintaian (goal) dengan reward **+20**
- S6 adalah zona anti-aircraft dengan reward **-15** (bahaya)
- Setiap langkah mendapat reward **-1** (biaya bahan bakar)
- Actions: Up (U), Down (D), Left (L), Right (R)
- Jika menabrak dinding, drone tetap di tempat (reward -1 tetap berlaku)
- Discount factor γ = 0.8
- Learning rate α = 0.5

**Pertanyaan:**

**2a.** Formulasikan masalah ini sebagai MDP! Definisikan S, A, dan berikan contoh transisi T untuk minimal 5 pasangan (state, action)! (15 poin)

**2b.** Mengingat S6 adalah zona bahaya, identifikasi dua kemungkinan rute optimal dari S1 ke S9 yang menghindari S6! Hitung total reward untuk masing-masing rute (tanpa discount)! (10 poin)

**2c.** Lakukan Q-Learning untuk satu episode dengan path S1→D→S4→D→S7→R→S8→R→S9! Semua Q(s,a) awalnya 0. Tunjukkan Q-table untuk state yang dikunjungi setelah episode! (20 poin)

**2d.** Jelaskan bagaimana strategi ε-greedy akan membantu drone menemukan rute optimal! Apa yang terjadi jika ε terlalu tinggi? Apa yang terjadi jika ε terlalu rendah? (10 poin)

**2e.** Rancang reward shaping yang lebih baik untuk misi ini! Pertimbangkan: jarak ke target, deteksi ancaman, tingkat stealth, dan efisiensi bahan bakar. Jelaskan bagaimana desain reward mempengaruhi perilaku agent! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | Supervised learning menggunakan data berlabel (x, y) untuk melatih model, sedangkan unsupervised learning bekerja dengan data tanpa label untuk menemukan pola tersembunyi |
| 2 | **C** | Pengelompokan dokumen berdasarkan topik tanpa kategori yang ditentukan sebelumnya adalah tugas clustering (unsupervised). Pilihan lain memerlukan label |
| 3 | **C** | Assignment Step menetapkan setiap data point ke klaster yang centroid-nya paling dekat berdasarkan jarak Euclidean |
| 4 | **B** | d(P, μ₁) = √((3-1)²+(4-1)²) = √(4+9) = √13 ≈ 3.61; d(P, μ₂) = √((3-5)²+(4-5)²) = √(4+1) = √5 ≈ 2.24. P lebih dekat ke μ₂ |
| 5 | **B** | K-Means menjamin konvergensi ke local optimum, bukan global optimum. Hasil bisa berbeda dengan inisialisasi berbeda |
| 6 | **C** | Elbow Method memilih K di titik "siku" dimana penurunan WCSS mulai melambat signifikan |
| 7 | **D** | Silhouette score mendekati +1 berarti data sangat cocok dengan klasternya (a(i) kecil) dan jauh dari klaster terdekat lainnya (b(i) besar) |
| 8 | **C** | Single linkage menggunakan jarak minimum antara anggota terdekat dari dua klaster |
| 9 | **B** | Single linkage rentan terhadap chaining effect, dimana dua klaster yang seharusnya terpisah terhubung melalui rantai titik-titik bridge |
| 10 | **C** | PCA bertujuan mereduksi dimensi data dengan memproyeksikan ke principal components yang mempertahankan varians maksimum |
| 11 | **B** | Dalam RL, agent belajar melalui trial-and-error berinteraksi dengan lingkungan, menerima reward untuk aksi baik dan penalty untuk aksi buruk |
| 12 | **D** | Learning rate (α) adalah parameter algoritma Q-Learning, bukan bagian dari definisi formal MDP yang terdiri dari (S, A, T, R, γ) |
| 13 | **B** | Markov Property: P(s_{t+1} | s_t, a_t) — state masa depan hanya bergantung pada state dan action saat ini, bukan seluruh sejarah |
| 14 | **B** | Q(S2,R) ← 5.0 + 0.5 × [10 + 0.9 × 0 - 5.0] = 5.0 + 0.5 × 5.0 = 7.5 |
| 15 | **B** | γ = 0 berarti agent hanya mempertimbangkan reward segera (immediate reward), mengabaikan semua reward masa depan |
| 16 | **C** | ε-greedy: dengan probabilitas ε pilih aksi random (exploration), dengan probabilitas (1-ε) pilih aksi dengan Q-value tertinggi (exploitation) |
| 17 | **A** | K-Means memerlukan K sebagai input, Hierarchical Clustering tidak memerlukan K di awal (K ditentukan dengan memotong dendrogram) |
| 18 | **B** | Clustering sinyal komunikasi tanpa label kategori yang diketahui sebelumnya adalah tugas unsupervised learning |
| 19 | **C** | Optimalisasi strategi manuver drone melalui trial-and-error dengan reward/penalty adalah RL. Opsi lain adalah supervised (A,E), unsupervised (B,D) |
| 20 | **B** | CNN dirancang khusus untuk pemrosesan data grid/citra dengan convolutional layers yang menangkap fitur spasial |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Perbandingan tiga paradigma ML:**

| Aspek | Supervised | Unsupervised | Reinforcement |
|-------|-----------|--------------|---------------|
| **Data** | Berlabel (x, y) | Tanpa label (x saja) | Interaksi (state, action, reward) |
| **Feedback** | Langsung dari label | Tidak ada feedback eksplisit | Delayed reward/penalty |
| **Tujuan** | Memprediksi label/nilai | Menemukan pola tersembunyi | Memaksimalkan cumulative reward |

**Contoh aplikasi:**
- **Supervised:** Klasifikasi citra satelit sebagai "pangkalan militer" atau "bukan pangkalan" menggunakan data berlabel
- **Unsupervised:** Pengelompokan pola komunikasi musuh yang dicegat untuk mengidentifikasi kelompok yang berbeda tanpa label
- **Reinforcement:** Drone otonom belajar strategi navigasi optimal melalui trial-and-error di medan perang

---

#### Jawaban Soal 2 ⭐

**Empat langkah utama K-Means:**

1. **Inisialisasi:** Pilih K centroid awal secara acak dari dataset atau posisi random. K harus ditentukan sebelumnya.

2. **Assignment Step:** Untuk setiap data point, hitung jarak ke semua centroid menggunakan jarak Euclidean, lalu tetapkan data ke klaster dengan centroid terdekat: c_i = arg min ‖x_i - μ_j‖².

3. **Update Step:** Perbarui centroid setiap klaster dengan menghitung rata-rata semua data point yang termasuk klaster tersebut: μ_j = (1/|C_j|) Σ x_i untuk semua x_i ∈ C_j.

4. **Convergence Check:** Ulangi langkah 2-3 hingga centroid tidak lagi berubah (atau perubahan di bawah threshold). Saat itu algoritma telah konvergen.

---

#### Jawaban Soal 3 ⭐

**Jarak Euclidean A(1, 5) dan B(4, 1):**

$$d(A, B) = \sqrt{(4-1)^2 + (1-5)^2}$$

$$d(A, B) = \sqrt{3^2 + (-4)^2} = \sqrt{9 + 16} = \sqrt{25} = 5$$

**Jawaban:** Jarak Euclidean antara A(1, 5) dan B(4, 1) adalah **5**.

---

#### Jawaban Soal 4 ⭐

**Mengapa K-Means sensitif terhadap inisialisasi:**

K-Means meminimalkan fungsi objektif WCSS (Within-Cluster Sum of Squares), tetapi hanya menjamin konvergensi ke **local minimum**, bukan global minimum. Centroid awal yang berbeda menghasilkan local minimum yang berbeda, sehingga hasil clustering bisa berbeda pula.

Contoh: Jika dua centroid awal kebetulan ditempatkan di klaster yang sama, satu klaster alami mungkin tidak terdeteksi.

**Solusi: K-Means++**
- Centroid pertama dipilih random dari data
- Centroid berikutnya dipilih dengan probabilitas proporsional terhadap jarak kuadrat ke centroid terdekat yang sudah dipilih
- Ini menjamin centroid awal tersebar dengan baik, mengurangi risiko konvergensi ke local minimum yang buruk

---

#### Jawaban Soal 5 ⭐⭐

**Iterasi 1 K-Means, μ₁=(0,0), μ₂=(6,6):**

*Step 1:* Hitung jarak ke setiap centroid

| Titik | d(titik, μ₁) | d(titik, μ₂) | Klaster |
|-------|-------------|-------------|---------|
| A(1,2) | √(1+4) = √5 = **2.24** | √(25+16) = √41 = **6.40** | C₁ |
| B(2,3) | √(4+9) = √13 = **3.61** | √(16+9) = √25 = **5.00** | C₁ |
| C(5,6) | √(25+36) = √61 = **7.81** | √(1+0) = √1 = **1.00** | C₂ |
| D(6,5) | √(36+25) = √61 = **7.81** | √(0+1) = √1 = **1.00** | C₂ |
| E(3,4) | √(9+16) = √25 = **5.00** | √(9+4) = √13 = **3.61** | C₂ |

*Step 2:* Anggota klaster
- C₁ = {A(1,2), B(2,3)}
- C₂ = {C(5,6), D(6,5), E(3,4)}

*Step 3:* Update centroid

$$\mu_1^{new} = \left(\frac{1+2}{2}, \frac{2+3}{2}\right) = (1.5, 2.5)$$

$$\mu_2^{new} = \left(\frac{5+6+3}{3}, \frac{6+5+4}{3}\right) = (4.67, 5.0)$$

**Jawaban:** Setelah iterasi 1: C₁ = {A, B} dengan centroid (1.5, 2.5); C₂ = {C, D, E} dengan centroid (4.67, 5.0).

---

#### Jawaban Soal 6 ⭐⭐

**Analisis Elbow Method:**

| K | WCSS | Penurunan | % Penurunan |
|---|------|-----------|-------------|
| 1 | 500 | — | — |
| 2 | 300 | 200 | 40% |
| 3 | 150 | 150 | 50% |
| 4 | 130 | 20 | 13% |
| 5 | 120 | 10 | 8% |
| 6 | 115 | 5 | 4% |

**Analisis:**
- K=1 → K=2: penurunan 200 (signifikan)
- K=2 → K=3: penurunan 150 (signifikan)
- K=3 → K=4: penurunan **hanya 20** (melambat drastis!)
- K=4 → K=5: penurunan 10 (minimal)
- K=5 → K=6: penurunan 5 (minimal)

**Jawaban:** K optimal = **3**. Titik "siku" jelas terlihat di K=3, dimana penurunan WCSS dari K=3 ke K=4 melambat drastis (dari 150 menjadi 20). Menambah klaster di atas 3 hanya memberikan perbaikan marginal yang tidak sebanding dengan kompleksitas tambahan.

---

#### Jawaban Soal 7 ⭐⭐

**Agglomerative Clustering (Single Linkage):**

*Step 1:* Matriks jarak awal (semua titik di sumbu x)

|   | A(0) | B(1) | C(4) | D(5) |
|---|------|------|------|------|
| A | 0 | 1 | 4 | 5 |
| B |   | 0 | 3 | 4 |
| C |   |   | 0 | 1 |
| D |   |   |   | 0 |

*Step 2:* Iterasi 1 — Jarak terkecil: d(A,B) = 1 dan d(C,D) = 1 (tie, pilih A,B)
- Gabungkan A dan B → {A,B}

Perbarui matriks (single linkage = minimum):
- d({A,B}, C) = min(4, 3) = 3
- d({A,B}, D) = min(5, 4) = 4

|   | {A,B} | C | D |
|---|-------|---|---|
| {A,B} | 0 | 3 | 4 |
| C |   | 0 | 1 |
| D |   |   | 0 |

*Step 3:* Iterasi 2 — Jarak terkecil: d(C,D) = 1
- Gabungkan C dan D → {C,D}

Perbarui matriks:
- d({A,B}, {C,D}) = min(3, 4) = 3

*Step 4:* Iterasi 3 — Gabungkan {A,B} dan {C,D} pada jarak 3

**Jawaban:** Urutan penggabungan:
1. A + B pada jarak 1
2. C + D pada jarak 1
3. {A,B} + {C,D} pada jarak 3

---

#### Jawaban Soal 8 ⭐⭐

**Perbandingan tiga metode linkage:**

| Aspek | Single Linkage | Complete Linkage | Average Linkage |
|-------|----------------|------------------|-----------------|
| **Formula** | min d(a,b) | max d(a,b) | mean d(a,b) |
| **Karakter klaster** | Memanjang (chain-like) | Bulat, kompak | Kompromi |
| **Kelemahan** | Efek chaining | Sensitif outlier | Lebih lambat |
| **Kekuatan** | Deteksi bentuk non-spherical | Klaster berukuran merata | Seimbang |

**Kapan masing-masing cocok:**

- **Single Linkage:** Cocok ketika klaster memiliki bentuk tidak beraturan atau memanjang, misalnya clustering aliran sungai atau jalur komunikasi pada peta.

- **Complete Linkage:** Cocok ketika menginginkan klaster yang compact dan berukuran relatif sama, misalnya mengelompokkan unit-unit militer berdasarkan kapabilitas.

- **Average Linkage:** Cocok sebagai pilihan default yang seimbang ketika tidak ada informasi a priori tentang bentuk klaster, misalnya analisis awal data sinyal intelijen.

---

#### Jawaban Soal 9 ⭐⭐

**Formulasi MDP Robot Patroli Grid 1×4:**

```
┌────┬────┬────┬────┐
│ S1 │ S2 │ S3 │ S4 │  ← base camp (goal)
└────┴────┴────┴────┘
```

**Komponen MDP:**

- **S** = {S1, S2, S3, S4}
- **A** = {L (Left), R (Right)}
- **T** (Fungsi Transisi — deterministik):

| State | Action | Next State | Keterangan |
|-------|--------|------------|------------|
| S1 | R | S2 | Bergerak kanan |
| S1 | L | S1 | Menabrak dinding |
| S2 | R | S3 | Bergerak kanan |
| S2 | L | S1 | Bergerak kiri |
| S3 | R | S4 | Menuju goal |
| S3 | L | S2 | Bergerak kiri |
| S4 | — | — | Terminal state |

- **R** (Fungsi Reward):
  - R = +10 saat mencapai S4 (base camp)
  - R = -1 untuk setiap langkah lainnya

- **γ** = misal 0.9 (discount factor)

---

#### Jawaban Soal 10 ⭐⭐

**Exploration vs Exploitation:**

| Aspek | Exploration | Exploitation |
|-------|-------------|--------------|
| **Definisi** | Mencoba aksi baru/belum pernah dicoba | Memilih aksi terbaik yang diketahui saat ini |
| **Tujuan** | Menemukan strategi/informasi baru | Memaksimalkan reward segera |
| **Risiko** | Reward jangka pendek rendah | Terjebak di solusi sub-optimal |

**Contoh pada drone pengintai:**

**Exploitation:** Drone selalu mengambil Rute A yang diketahui aman dan efisien berdasarkan pengalaman sebelumnya. Masalah: musuh bisa mempelajari pola dan menyiapkan pertahanan di sepanjang rute.

**Exploration:** Drone sesekali mencoba Rute B, C, atau D yang belum pernah digunakan. Mungkin menemukan rute lebih efisien atau mendeteksi posisi musuh baru. Risiko: bisa terbang ke area pertahanan udara musuh yang belum diketahui.

**Solusi: ε-greedy** — dengan probabilitas ε (misal 0.2) drone memilih rute random, sisanya (0.8) memilih rute terbaik yang diketahui. Nilai ε dikurangi seiring bertambahnya pengalaman.

---

#### Jawaban Soal 11 ⭐⭐⭐

**Q-Learning Episode 1: S1→R→S2→R→S3**

*Step 1:* Inisialisasi Q-table

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | 0 |
| S2 | 0 | 0 |

*Step 2:* Langkah 1: S1 → R → S2, reward = -1

$$Q(S1, R) \leftarrow 0 + 0.5 \times [-1 + 0.9 \times \max(Q(S2,L), Q(S2,R)) - 0]$$
$$Q(S1, R) \leftarrow 0 + 0.5 \times [-1 + 0.9 \times 0 - 0] = 0.5 \times (-1) = -0.5$$

*Step 3:* Langkah 2: S2 → R → S3 (terminal), reward = +10

$$Q(S2, R) \leftarrow 0 + 0.5 \times [10 + 0.9 \times 0 - 0]$$

S3 terminal, maka max Q(S3, ·) = 0:

$$Q(S2, R) \leftarrow 0 + 0.5 \times 10 = 5.0$$

*Step 4:* Q-table setelah episode 1

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | **-0.5** |
| S2 | 0 | **5.0** |

**Jawaban:** Setelah episode 1, Q(S1,R) = -0.5 dan Q(S2,R) = 5.0. Agent mulai belajar bahwa bergerak kanan dari S2 sangat menguntungkan (dekat goal), sedangkan Q(S1,R) masih negatif karena belum memperhitungkan reward masa depan secara penuh.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Q-Learning Episode 2: S1→R→S2→R→S3**

*Step 1:* Gunakan Q-table dari episode 1

| State | Q(s, L) | Q(s, R) |
|-------|---------|---------|
| S1 | 0 | -0.5 |
| S2 | 0 | 5.0 |

*Step 2:* Langkah 1: S1 → R → S2, reward = -1

$$Q(S1, R) \leftarrow -0.5 + 0.5 \times [-1 + 0.9 \times \max(0, 5.0) - (-0.5)]$$
$$Q(S1, R) \leftarrow -0.5 + 0.5 \times [-1 + 4.5 + 0.5]$$
$$Q(S1, R) \leftarrow -0.5 + 0.5 \times 4.0 = -0.5 + 2.0 = 1.5$$

*Step 3:* Langkah 2: S2 → R → S3 (terminal), reward = +10

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

**Nilai konvergen:**
- Q*(S2, R) = 10 (satu langkah ke goal, reward +10)
- Q*(S1, R) = -1 + 0.9 × 10 = 8.0 (reward -1 + discounted value dari S2)

**Jawaban:** Q-values meningkat menuju nilai konvergen. Q(S1,R) berubah dari -0.5 ke 1.5, mendekati nilai optimal 8.0. Ini menunjukkan reward masa depan dari S2 mulai terpropagasi ke S1. Setelah banyak episode, Q-table akan konvergen dan agent mengetahui bahwa bergerak ke kanan dari semua state adalah optimal.

---

#### Jawaban Soal 13 ⭐⭐⭐

**Pengaruh Discount Factor γ:**

**Skenario:** Grid S1→S2→S3, reward -1 per langkah, +10 di S3.

**Dengan γ = 0 (myopic):**

$$V(S1) = -1 + 0 \times V(S2) = -1$$

Agent hanya melihat reward segera (-1) dan tidak mempertimbangkan reward masa depan (+10 di S3). Agent tidak termotivasi untuk bergerak ke kanan menuju goal.

**Dengan γ = 0.9 (far-sighted):**

$$V(S2) = -1 + 0.9 \times 10 = 8.0$$
$$V(S1) = -1 + 0.9 \times V(S2) = -1 + 0.9 \times 8.0 = -1 + 7.2 = 6.2$$

Agent memperhitungkan reward masa depan, sehingga V(S1) = 6.2 > 0. Agent termotivasi bergerak menuju goal.

**Perbandingan perilaku:**

| Aspek | γ = 0 | γ = 0.9 |
|-------|-------|---------|
| V(S1) | -1 | 6.2 |
| V(S2) | -1 | 8.0 |
| Perilaku | Tidak peduli masa depan | Menuju goal |
| Karakter | Myopic, greedy | Far-sighted, strategic |

**Jawaban:** γ menentukan seberapa jauh agent "melihat ke depan". γ=0 membuat agent myopic (hanya reward segera), γ=0.9 membuat agent mempertimbangkan reward masa depan secara signifikan. Untuk misi militer yang memerlukan perencanaan strategis, γ tinggi lebih sesuai.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Perbandingan K-Means vs Hierarchical Clustering:**

| Aspek | K-Means | Hierarchical | Kapan unggul |
|-------|---------|--------------|-------------|
| **(a) Input** | Perlu K di awal | Tidak perlu K | **Hierarchical** jika K tidak diketahui; **K-Means** jika K sudah pasti |
| **(b) Kompleksitas** | O(n × K × t × d) | O(n³) atau O(n² log n) | **K-Means** untuk data besar (>10.000); **Hierarchical** untuk data kecil |
| **(c) Bentuk klaster** | Hanya spherical | Fleksibel | **Hierarchical** untuk klaster non-spherical; **K-Means** cukup jika klaster bulat |
| **(d) Determinisme** | Non-deterministik (random init) | Deterministik | **Hierarchical** jika perlu reproducibility; K-Means perlu multiple runs |
| **(e) Skalabilitas** | Baik | Kurang baik | **K-Means** untuk dataset besar; **Hierarchical** untuk dataset kecil-menengah |

**Skenario spesifik:**
- **K-Means lebih unggul:** Clustering 100.000 citra satelit ke dalam K=5 kategori terrain yang sudah ditentukan — efisien dan K diketahui
- **Hierarchical lebih unggul:** Analisis 200 sinyal intelijen untuk eksplorasi jumlah kelompok yang tidak diketahui — dendrogram membantu interpretasi

---

#### Jawaban Soal 15 ⭐⭐⭐

**PCA (Principal Component Analysis):**

**Tujuan:** Mereduksi dimensi data dari d dimensi menjadi k dimensi (k < d) sambil mempertahankan varians (informasi) sebanyak mungkin.

**Cara kerja umum:**
1. **Standarisasi data:** Normalisasi agar setiap fitur memiliki mean=0 dan variance=1
2. **Hitung matriks kovarians:** Mengukur hubungan antar fitur
3. **Hitung eigenvalue dan eigenvector:** Eigenvector menunjukkan arah varians terbesar (principal components)
4. **Pilih k eigenvector terbesar:** Ini menjadi principal components
5. **Proyeksikan data:** Transformasi data ke ruang berdimensi lebih rendah

**Contoh penerapan pertahanan:**

1. **Analisis sinyal radar:** Data radar memiliki puluhan fitur (frekuensi, amplitudo, phase, polarisasi, dll.). PCA mereduksi ke 2-3 dimensi untuk visualisasi, membantu operator mengidentifikasi klaster jenis ancaman pada plot 2D.

2. **Citra satelit:** Setiap piksel memiliki banyak band spektral. PCA mengekstrak komponen utama untuk mengurangi redundansi dan mempercepat analisis klasifikasi terrain.

3. **Cyber threat analysis:** Data log serangan memiliki ratusan fitur. PCA mereduksi dimensi sehingga clustering dan anomaly detection menjadi lebih efisien dan visualisasi pattern lebih mudah.

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Analisis Sinyal Intelijen dengan Clustering

**1a. Mengapa Unsupervised Learning (10 poin)**

Unsupervised learning lebih sesuai karena:

1. **Tidak ada label:** Tim intelijen tidak mengetahui berapa kelompok yang ada atau kelompok mana yang menghasilkan sinyal tertentu. Tidak ada ground truth labels.

2. **Exploratory analysis:** Tujuannya adalah menemukan pola tersembunyi dan mengelompokkan sinyal secara alami, bukan mengklasifikasikan ke kategori yang sudah ditentukan.

3. **Musuh baru:** Mungkin terdapat kelompok komunikasi yang belum pernah diidentifikasi sebelumnya, sehingga supervised learning (yang memerlukan contoh dari semua kelas) tidak memungkinkan.

4. **Adaptif:** Unsupervised learning dapat menemukan jumlah kelompok secara data-driven, tanpa asumsi a priori tentang struktur data.

**1b. Satu Iterasi K-Means (20 poin)**

Menggunakan hanya fitur Frekuensi (F) dan Durasi (D):

Centroid awal: μ₁ = S1(2, 3), μ₂ = S3(8, 7)

*Step 1:* Hitung jarak setiap sinyal ke kedua centroid

| Sinyal | (F, D) | d(S, μ₁) | d(S, μ₂) | Klaster |
|--------|--------|-----------|-----------|---------|
| S1 | (2, 3) | √(0+0) = **0** | √(36+16) = **7.21** | C₁ |
| S2 | (3, 2) | √(1+1) = **1.41** | √(25+25) = **7.07** | C₁ |
| S3 | (8, 7) | √(36+16) = **7.21** | √(0+0) = **0** | C₂ |
| S4 | (7, 8) | √(25+25) = **7.07** | √(1+1) = **1.41** | C₂ |
| S5 | (2, 2) | √(0+1) = **1.00** | √(36+25) = **7.81** | C₁ |
| S6 | (9, 8) | √(49+25) = **8.60** | √(1+1) = **1.41** | C₂ |
| S7 | (5, 5) | √(9+4) = **3.61** | √(9+4) = **3.61** | C₁ (tie) |
| S8 | (8, 6) | √(36+9) = **6.71** | √(0+1) = **1.00** | C₂ |

*Step 2:* Anggota klaster
- C₁ = {S1(2,3), S2(3,2), S5(2,2), S7(5,5)}
- C₂ = {S3(8,7), S4(7,8), S6(9,8), S8(8,6)}

*Step 3:* Update centroid

$$\mu_1^{new} = \left(\frac{2+3+2+5}{4}, \frac{3+2+2+5}{4}\right) = (3.0, 3.0)$$

$$\mu_2^{new} = \left(\frac{8+7+9+8}{4}, \frac{7+8+8+6}{4}\right) = (8.0, 7.25)$$

**Jawaban:** Setelah iterasi 1, dua klaster terbentuk: C₁ = {S1, S2, S5, S7} (sinyal frekuensi rendah, durasi pendek) dengan centroid (3.0, 3.0), dan C₂ = {S3, S4, S6, S8} (sinyal frekuensi tinggi, durasi panjang) dengan centroid (8.0, 7.25).

**1c. Penentuan K Optimal (10 poin)**

| K | WCSS | Penurunan |
|---|------|-----------|
| 2 | 120 | — |
| 3 | 45 | 75 (62.5%) |
| 4 | 38 | 7 (15.6%) |
| 5 | 35 | 3 (7.9%) |

**Jawaban:** K optimal = **3**. Penurunan WCSS dari K=2 ke K=3 sangat signifikan (75 poin, 62.5%), namun dari K=3 ke K=4 hanya 7 poin (15.6%) dan semakin kecil setelahnya. Titik "siku" jelas di K=3. Interpretasi: kemungkinan terdapat 3 kelompok komunikasi berbeda di wilayah perbatasan.

**1d. K-Means vs Hierarchical (15 poin)**

| Aspek | K-Means | Hierarchical | Relevansi Kasus |
|-------|---------|--------------|-----------------|
| **Jumlah data (200)** | Sangat efisien | Cukup efisien | Keduanya layak, 200 masih kecil |
| **K fleksibel** | Perlu ditentukan | Potong dendrogram | **Hierarchical lebih baik** — K tidak diketahui |
| **Interpretabilitas** | Klaster flat | Hierarki lengkap | **Hierarchical lebih baik** — bisa lihat sub-kelompok |
| **Reproducibility** | Non-deterministik | Deterministik | **Hierarchical lebih baik** — untuk intelijen perlu konsistensi |
| **Bentuk klaster** | Spherical | Fleksibel | **Hierarchical lebih baik** — pola sinyal mungkin non-spherical |

**Rekomendasi:** Hierarchical Clustering lebih sesuai untuk kasus ini karena:
1. Jumlah klaster belum diketahui — dendrogram membantu eksplorasi
2. 200 data masih dalam range efisien untuk hierarchical (O(200³) ≈ 8 juta operasi, masih cepat)
3. Dendrogram memberikan hierarki informasi yang berguna bagi analis — mungkin ada sub-kelompok dalam kelompok utama
4. Hasil deterministik penting untuk laporan intelijen yang reliable

**1e. Manfaat PCA (10 poin)**

Dengan 4 dimensi fitur (frekuensi, durasi, kekuatan, interval), PCA dapat membantu:

1. **Visualisasi:** Mereduksi 4D ke 2D sehingga analis dapat melihat klaster pada scatter plot. Tanpa PCA, tidak mungkin memvisualisasikan data 4D secara langsung.

2. **Menghilangkan redundansi:** Jika frekuensi dan interval berkorelasi tinggi (sinyal frekuensi tinggi cenderung interval panjang), PCA menangkap informasi ini dalam satu komponen, mengurangi redundansi.

3. **Efisiensi clustering:** K-Means pada 2 principal components lebih cepat dan sering menghasilkan klaster lebih baik daripada pada 4 fitur asli (mengurangi curse of dimensionality).

4. **Noise reduction:** Komponen dengan varians rendah sering merepresentasikan noise. PCA yang membuang komponen minor secara efektif menyaring noise.

---

#### Studi Kasus 2: Drone Otonom dengan Reinforcement Learning

**2a. Formulasi MDP (15 poin)**

**Komponen MDP:**

- **S** = {S1, S2, S3, S4, S5, S6, S7, S8, S9}
- **A** = {U (Up), D (Down), L (Left), R (Right)}
- **T** (Fungsi Transisi — deterministik):

| State | Action | Next State | Reward |
|-------|--------|------------|--------|
| S1 | R | S2 | -1 |
| S1 | D | S4 | -1 |
| S1 | L | S1 | -1 (dinding) |
| S1 | U | S1 | -1 (dinding) |
| S2 | R | S3 | -1 |
| S2 | D | S5 | -1 |
| S4 | D | S7 | -1 |
| S4 | R | S5 | -1 |
| S5 | R | S6 | **-15** (zona bahaya) |
| S6 | D | S9 | **+20** (goal) |
| S7 | R | S8 | -1 |
| S8 | R | S9 | **+20** (goal) |
| S8 | U | S5 | -1 |
| S3 | D | S6 | **-15** (zona bahaya) |

Terminal state: S9 (goal)

- **R**: +20 saat memasuki S9, -15 saat memasuki S6, -1 untuk langkah lainnya
- **γ** = 0.8

**2b. Dua Rute Optimal Menghindari S6 (10 poin)**

```
Grid dengan ancaman:
┌────┬────┬────┐
│ S1 │ S2 │ S3 │
├────┼────┼────┤
│ S4 │ S5 │ ⚠S6│
├────┼────┼────┤
│ S7 │ S8 │ S9 │
└────┴────┴────┘
```

**Rute 1 (bawah-bawah-kanan-kanan):** S1 → S4 → S7 → S8 → S9

| Langkah | Reward |
|---------|--------|
| S1 → S4 | -1 |
| S4 → S7 | -1 |
| S7 → S8 | -1 |
| S8 → S9 | +20 |
| **Total** | **+17** |

**Rute 2 (bawah-kanan-kanan-bawah):** S1 → S4 → S5 → S8 (via D from S5 — Wait, S5→D=S8)

Koreksi: pada grid 3×3, S5→D = S8.

S1 → S4 → S5 → S8 → S9

| Langkah | Reward |
|---------|--------|
| S1 → S4 | -1 |
| S4 → S5 | -1 |
| S5 → S8 (D) | -1 |
| S8 → S9 | +20 |
| **Total** | **+17** |

**Jawaban:** Kedua rute memiliki total reward +17 (4 langkah, 3 langkah × -1 + goal +20). Rute 1 melalui pinggir kiri-bawah, Rute 2 melalui tengah ke bawah. Keduanya optimal karena menghindari S6 (-15) dan mencapai goal dengan jumlah langkah minimum (4 langkah).

**2c. Q-Learning Episode: S1→D→S4→D→S7→R→S8→R→S9 (20 poin)**

Q-table awal: semua Q(s,a) = 0. α=0.5, γ=0.8.

**Langkah 1: S1 → D → S4, reward = -1**

$$Q(S1, D) \leftarrow 0 + 0.5 \times [-1 + 0.8 \times \max Q(S4, \cdot) - 0]$$
$$Q(S1, D) \leftarrow 0.5 \times [-1 + 0.8 \times 0] = 0.5 \times (-1) = -0.5$$

**Langkah 2: S4 → D → S7, reward = -1**

$$Q(S4, D) \leftarrow 0 + 0.5 \times [-1 + 0.8 \times \max Q(S7, \cdot) - 0]$$
$$Q(S4, D) \leftarrow 0.5 \times [-1 + 0] = -0.5$$

**Langkah 3: S7 → R → S8, reward = -1**

$$Q(S7, R) \leftarrow 0 + 0.5 \times [-1 + 0.8 \times \max Q(S8, \cdot) - 0]$$
$$Q(S7, R) \leftarrow 0.5 \times [-1 + 0] = -0.5$$

**Langkah 4: S8 → R → S9 (terminal), reward = +20**

$$Q(S8, R) \leftarrow 0 + 0.5 \times [20 + 0.8 \times 0 - 0]$$

S9 terminal, max Q(S9, ·) = 0:

$$Q(S8, R) \leftarrow 0.5 \times 20 = 10.0$$

**Q-table setelah episode 1:**

| State | Q(s, U) | Q(s, D) | Q(s, L) | Q(s, R) |
|-------|---------|---------|---------|---------|
| S1 | 0 | **-0.5** | 0 | 0 |
| S4 | 0 | **-0.5** | 0 | 0 |
| S7 | 0 | 0 | 0 | **-0.5** |
| S8 | 0 | 0 | 0 | **10.0** |

**Analisis:** Hanya Q(S8, R) = 10.0 yang positif, karena itu adalah langkah terakhir sebelum goal. Pada episode-episode berikutnya, reward positif akan terpropagasi mundur ke S7, S4, dan S1.

**2d. Strategi ε-greedy (10 poin)**

**Cara ε-greedy membantu:**
- Dengan probabilitas (1-ε): drone memilih aksi dengan Q-value tertinggi (exploitation)
- Dengan probabilitas ε: drone memilih aksi random (exploration)

**Jika ε terlalu tinggi (misal ε = 0.9):**
- Drone hampir selalu memilih aksi random
- Banyak langkah tidak efisien dan berbahaya (bisa masuk S6 berulang kali)
- Lambat menemukan rute optimal karena tidak memanfaatkan pengetahuan
- Reward kumulatif rendah selama training

**Jika ε terlalu rendah (misal ε = 0.01):**
- Drone hampir selalu memilih aksi terbaik yang diketahui
- Jika rute pertama yang ditemukan sub-optimal, drone akan terus menggunakannya
- Rute melalui S6 mungkin tidak pernah ditemukan berbahaya (karena tidak pernah dieksplorasi)
- Rute yang lebih baik mungkin tidak pernah ditemukan

**Strategi optimal:** Mulai dengan ε tinggi (misal 0.5) dan turunkan secara bertahap (ε-decay) hingga ε rendah (misal 0.05). Ini memastikan eksplorasi menyeluruh di awal dan eksploitasi efisien di akhir.

**2e. Reward Shaping (10 poin)**

**Desain reward yang lebih baik:**

$$R(s, a, s') = R_{goal} + R_{threat} + R_{stealth} + R_{fuel}$$

| Komponen | Formula | Contoh Nilai |
|----------|---------|-------------|
| **R_goal** | +20 × (1/jarak_ke_S9) | Semakin dekat ke target = reward lebih tinggi |
| **R_threat** | -15 jika masuk S6; -5 jika adjacent S6 | Penalty untuk zona bahaya dan proximity |
| **R_stealth** | +2 jika di pinggir grid (lebih tersembunyi) | Bonus untuk rute stealth |
| **R_fuel** | -1 per langkah, -2 jika melawan angin | Biaya bahan bakar realistis |

**Contoh implementasi:**

```
R(s, a, s') = 
  +20       jika s' = S9 (goal tercapai)
  -15       jika s' = S6 (zona bahaya)
  -3        jika s' adjacent S6 (proximity warning)
  +1        jika jarak ke S9 berkurang (progress reward)
  -1        biaya langkah dasar
```

**Pengaruh pada perilaku:**
- **Progress reward:** Mendorong drone menuju target, mengurangi wandering
- **Proximity warning:** Drone belajar menghindari area sekitar S6, bukan hanya S6 itu sendiri
- **Stealth bonus:** Mendorong rute yang lebih tersembunyi di pinggir area operasi
- **Tanpa reward shaping:** Agent mungkin memerlukan sangat banyak episode untuk belajar karena reward sparse (hanya di goal dan threat)

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
