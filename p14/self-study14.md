# Panduan Belajar Mandiri Pertemuan 14: Pembelajaran Mesin - Unsupervised Learning dan Reinforcement Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 14  
**Topik:** Pembelajaran Mesin - Unsupervised Learning dan Reinforcement Learning  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan sesi belajar mandiri ini, Anda diharapkan mampu:

1. Menjelaskan perbedaan fundamental antara supervised, unsupervised, dan reinforcement learning
2. Mengimplementasikan dan menganalisis algoritma K-means clustering secara manual
3. Mengevaluasi kualitas clustering menggunakan silhouette score dan elbow method
4. Memahami konsep dasar Markov Decision Process (MDP) dan komponen-komponennya
5. Menjelaskan mekanisme Q-learning dan memperbarui Q-table secara manual
6. Mengidentifikasi aplikasi ketiga paradigma ML dalam konteks pertahanan

---

## 1. Review Konsep: Unsupervised Learning dan K-Means Clustering (45 menit)

### Ringkasan Materi

**Unsupervised Learning** adalah paradigma pembelajaran mesin di mana algoritma belajar dari data yang **tidak memiliki label**. Berbeda dengan supervised learning yang memiliki target output yang jelas, unsupervised learning mencoba menemukan **struktur tersembunyi** dalam data. Aplikasi utamanya meliputi clustering (pengelompokan), dimensionality reduction (pengurangan dimensi), dan anomaly detection (deteksi anomali).

**K-Means Clustering** adalah algoritma clustering partitional yang membagi n data point ke dalam K cluster, di mana setiap data point termasuk ke cluster dengan centroid terdekat. Algoritma ini bekerja secara iteratif:

1. **Inisialisasi**: Pilih K titik sebagai centroid awal secara acak
2. **Assignment**: Assign setiap data point ke centroid terdekat (menggunakan Euclidean distance)
3. **Update**: Hitung ulang centroid sebagai mean dari semua data point dalam cluster
4. **Konvergensi**: Ulangi langkah 2-3 hingga centroid tidak berubah signifikan

**Formula Euclidean Distance:**

$$d(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}$$

**Contoh Konteks Pertahanan:**
- Pengelompokan pola serangan cyber berdasarkan signature
- Klasifikasi perilaku kapal di wilayah maritim (kecepatan, rute, frekuensi)
- Segmentasi citra satelit untuk analisis terrain
- Pengelompokan sinyal komunikasi dalam SIGINT

![Proses K-Means Clustering](images/ss14-01-kmeans-clustering-process.png)

*Gambar 14.1: Proses iteratif algoritma K-means clustering*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Proses iterasi K-means clustering dari inisialisasi hingga konvergen, ditampilkan dalam 4 tahap
STYLE: Ilustrasi vektor flat yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
LAYOUT: Susunan horizontal menunjukkan 4 tahap sekuensial dengan panah antar tahap
COLORS: 
- Primer: #2563eb (biru) untuk cluster 1 dan centroid
- Sekunder: #10b981 (hijau) untuk cluster 2 dan centroid  
- Aksen: #f59e0b (oranye) untuk cluster 3 dan centroid
- Netral: #6b7280 (abu-abu) untuk data points belum ter-assign
- Latar: #ffffff (putih)
ELEMENTS:
1. Tahap 1 "Inisialisasi": Data points abu-abu tersebar, 3 centroid bintang ditempatkan acak
2. Tahap 2 "Assignment Pertama": Data points diwarnai sesuai centroid terdekat (biru, hijau, oranye)
3. Tahap 3 "Update Centroid": Centroid bergerak ke posisi mean cluster, panah menunjukkan perpindahan
4. Tahap 4 "Konvergen": Cluster stabil, centroid tidak berubah, garis batas cluster terlihat
LABELS: "Tahap 1: Inisialisasi", "Tahap 2: Assignment", "Tahap 3: Update", "Tahap 4: Konvergen", "Centroid", "Data Point"
SIZE: 1000x400 piksel
FORMAT: PNG, latar putih
NEGATIVE: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | StatQuest: K-means Clustering | StatQuest with Josh Starmer | 8:31 | https://www.youtube.com/watch?v=4b5d3muPQmA |
| 2 | K-Means Clustering Algorithm - Fully Explained | Normalized Nerd | 10:38 | https://www.youtube.com/watch?v=5w5iUbTlpMQ |
| 3 | Unsupervised Learning Explained | IBM Technology | 6:28 | https://www.youtube.com/watch?v=lEfrr0Yr684 |

### ✍️ Latihan Pemahaman

Setelah menonton video dan membaca ringkasan, jawab pertanyaan berikut:

1. Apa perbedaan fundamental antara supervised learning dan unsupervised learning dalam hal ketersediaan data?
2. Mengapa langkah inisialisasi centroid pada K-means bersifat kritis? Apa dampak pemilihan centroid awal yang buruk?
3. Bagaimana cara menentukan nilai K yang optimal pada K-means?
4. Berikan contoh penerapan K-means clustering untuk mengelompokkan pola lalu lintas maritim yang mencurigakan.

---

## 2. Review Konsep: Hierarchical Clustering dan Evaluasi Clustering (45 menit)

### Ringkasan Materi

**Hierarchical Clustering** adalah teknik clustering yang membangun hierarki cluster berbentuk **dendrogram**. Terdapat dua pendekatan:

**1. Agglomerative (Bottom-Up):**
- Dimulai dari setiap data point sebagai cluster individu
- Secara iteratif menggabungkan dua cluster terdekat
- Berakhir ketika semua data point dalam satu cluster

**2. Divisive (Top-Down):**
- Dimulai dari satu cluster besar berisi semua data
- Secara iteratif membagi cluster menjadi sub-cluster
- Berakhir ketika setiap data point merupakan cluster tersendiri

**Linkage Methods** menentukan bagaimana jarak antar cluster dihitung:
- **Single Linkage**: Jarak minimum antara anggota dua cluster
- **Complete Linkage**: Jarak maksimum antara anggota dua cluster
- **Average Linkage**: Rata-rata jarak antar semua pasangan anggota
- **Ward's Method**: Meminimalkan total within-cluster variance

**Evaluasi Kualitas Clustering:**

1. **Elbow Method**: Plot jumlah cluster (K) vs. total within-cluster sum of squares (WCSS). Titik "siku" menunjukkan K optimal.

2. **Silhouette Score**: Mengukur seberapa mirip data point dengan clusternya sendiri vs. cluster tetangga terdekat.

$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$

Di mana:
- $a(i)$ = rata-rata jarak ke data point lain dalam cluster yang sama
- $b(i)$ = rata-rata jarak ke data point di cluster tetangga terdekat
- Nilai: -1 (buruk) hingga +1 (baik)

![Dendrogram dan Evaluasi Clustering](images/ss14-02-hierarchical-clustering-dendrogram.png)

*Gambar 14.2: Dendrogram hierarchical clustering dan metode evaluasi*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Dendrogram hierarchical clustering dan perbandingan metode evaluasi clustering (Elbow dan Silhouette)
STYLE: Ilustrasi vektor flat yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
LAYOUT: Tiga panel horizontal: (1) dendrogram, (2) elbow plot, (3) silhouette plot
COLORS: 
- Primer: #2563eb (biru) untuk garis dendrogram dan kurva
- Sekunder: #10b981 (hijau) untuk titik optimal
- Aksen: #f59e0b (oranye) untuk anotasi
- Garis potong: #ef4444 (merah) putus-putus pada dendrogram
- Latar: #ffffff (putih)
ELEMENTS:
1. Panel kiri "Dendrogram": Tree diagram menunjukkan hierarki penggabungan 6 data points, garis potong merah horizontal membuat 3 cluster
2. Panel tengah "Metode Elbow": Kurva WCSS vs K (1-6), titik siku di K=3 ditandai hijau
3. Panel kanan "Silhouette Score": Bar chart skor silhouette untuk K=2,3,4,5, K=3 tertinggi ditandai hijau
LABELS: "Dendrogram", "Metode Elbow", "Silhouette Score", "Jumlah Cluster (K)", "WCSS", "Skor", "Garis Potong"
SIZE: 1000x400 piksel
FORMAT: PNG, latar putih
NEGATIVE: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | StatQuest: Hierarchical Clustering | StatQuest with Josh Starmer | 11:19 | https://www.youtube.com/watch?v=7xHsRkOdVwo |
| 2 | How to Determine the Optimal Number of Clusters (Elbow Method) | Visually Explained | 4:52 | https://www.youtube.com/watch?v=QXOkPvFM6NU |
| 3 | Silhouette Score Explained | DataCamp | 5:15 | https://www.youtube.com/watch?v=jhnKBGZjplM |

### ✍️ Latihan Pemahaman

Setelah menonton video dan membaca ringkasan, jawab pertanyaan berikut:

1. Apa perbedaan utama antara K-means clustering dan hierarchical clustering?
2. Kapan Anda akan memilih hierarchical clustering daripada K-means? Berikan contoh skenario pertahanan.
3. Diberikan silhouette score berikut: K=2 → 0.45, K=3 → 0.72, K=4 → 0.68, K=5 → 0.51. Berapa jumlah cluster optimal? Jelaskan!
4. Mengapa elbow method kadang sulit diinterpretasikan dan apa alternatifnya?

---

## 3. Review Konsep: Dimensionality Reduction - PCA (45 menit)

### Ringkasan Materi

**Principal Component Analysis (PCA)** adalah teknik dimensionality reduction yang mentransformasi data berdimensi tinggi ke dimensi yang lebih rendah sambil mempertahankan **varians maksimal**. PCA sangat berguna ketika:
- Dataset memiliki terlalu banyak fitur (curse of dimensionality)
- Perlu memvisualisasikan data berdimensi tinggi
- Ingin mengurangi noise dan redundansi dalam data

**Konsep Kunci PCA:**

1. **Standarisasi**: Normalisasi fitur agar memiliki mean = 0 dan standar deviasi = 1
2. **Matriks Kovarians**: Menghitung hubungan antar fitur
3. **Eigenvector dan Eigenvalue**: Eigenvector menentukan arah komponen utama, eigenvalue menentukan besaran varians yang ditangkap
4. **Proyeksi**: Memproyeksikan data ke eigenvector terpilih (komponen utama)

**Langkah-langkah PCA:**
1. Standarisasi data
2. Hitung matriks kovarians
3. Hitung eigenvector dan eigenvalue
4. Pilih K komponen utama dengan eigenvalue terbesar
5. Proyeksikan data ke K komponen tersebut

**Scree Plot** digunakan untuk menentukan berapa banyak komponen utama yang perlu dipertahankan. Umumnya, kita mempertahankan komponen yang menjelaskan ≥ 85-95% total varians.

**Contoh Konteks Pertahanan:**
- Reduksi dimensi pada data sensor radar (ratusan fitur per target)
- Kompresi citra satelit untuk transmisi bandwidth rendah
- Analisis pola komunikasi multidimensi dalam SIGINT
- Feature extraction dari data biometrik untuk identifikasi

![PCA Dimensionality Reduction](images/ss14-03-pca-dimensionality-reduction.png)

*Gambar 14.3: Ilustrasi PCA mereduksi data 2D ke 1D*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Ilustrasi Principal Component Analysis mereduksi data dari 2 dimensi ke 1 dimensi
STYLE: Ilustrasi vektor flat yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
LAYOUT: Dua panel: panel kiri data asli 2D, panel kanan data setelah proyeksi ke PC1
COLORS: 
- Primer: #2563eb (biru) untuk data points
- Sekunder: #10b981 (hijau) untuk PC1 (komponen utama pertama)
- Aksen: #f59e0b (oranye) untuk PC2 (komponen utama kedua)
- Proyeksi: #ef4444 (merah) putus-putus untuk garis proyeksi
- Latar: #ffffff (putih)
ELEMENTS:
1. Panel kiri "Data Asli 2D": Scatter plot dengan data points biru membentuk elips, dua panah menunjukkan arah PC1 (hijau, panjang) dan PC2 (oranye, pendek)
2. Garis proyeksi merah putus-putus dari data points ke garis PC1
3. Panel kanan "Proyeksi ke PC1": Data points diproyeksikan ke garis 1D, menunjukkan preserved variance
4. Scree plot kecil di pojok menunjukkan eigenvalue PC1 >> PC2
LABELS: "Data Asli (2D)", "Proyeksi ke PC1 (1D)", "PC1 (Varians Besar)", "PC2 (Varians Kecil)", "Komponen Utama Pertama", "Komponen Utama Kedua"
SIZE: 900x450 piksel
FORMAT: PNG, latar putih
NEGATIVE: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | StatQuest: PCA Step-by-Step | StatQuest with Josh Starmer | 21:57 | https://www.youtube.com/watch?v=FgakZw6K1QQ |
| 2 | Principal Component Analysis (PCA) Clearly Explained | Visually Explained | 5:22 | https://www.youtube.com/watch?v=g-Hb26agBFg |
| 3 | PCA - Main Ideas in Only 5 Minutes | StatQuest with Josh Starmer | 5:26 | https://www.youtube.com/watch?v=HMOI_lkzW08 |

### ✍️ Latihan Pemahaman

Setelah menonton video dan membaca ringkasan, jawab pertanyaan berikut:

1. Apa tujuan utama PCA dan mengapa teknik ini termasuk unsupervised learning?
2. Jelaskan hubungan antara eigenvector, eigenvalue, dan komponen utama dalam PCA!
3. Jika scree plot menunjukkan PC1 menjelaskan 60% varians, PC2 menjelaskan 25%, dan PC3 menjelaskan 10%, berapa komponen yang sebaiknya dipertahankan? Jelaskan!
4. Mengapa standarisasi data penting sebelum melakukan PCA?

---

## 4. Review Konsep: Reinforcement Learning dan Markov Decision Process (45 menit)

### Ringkasan Materi

**Reinforcement Learning (RL)** adalah paradigma pembelajaran mesin di mana **agen** belajar membuat keputusan melalui interaksi dengan **lingkungan**. Agen menerima **reward** atau **penalty** berdasarkan tindakannya, dan tujuannya adalah memaksimalkan total reward kumulatif jangka panjang.

**Komponen Utama RL:**
- **Agent**: Entitas pembuat keputusan (learner)
- **Environment**: Dunia tempat agen berinteraksi
- **State (S)**: Representasi situasi saat ini
- **Action (A)**: Pilihan yang tersedia bagi agen
- **Reward (R)**: Feedback numerik dari lingkungan
- **Policy (π)**: Strategi yang memetakan state ke action

**Markov Decision Process (MDP)** adalah framework matematika untuk memformulasikan masalah RL. MDP didefinisikan oleh tuple *(S, A, T, R, γ)*:
- **S**: Himpunan semua state
- **A**: Himpunan semua action
- **T(s'|s,a)**: Transition function — probabilitas berpindah ke state s' setelah melakukan action a di state s
- **R(s,a,s')**: Reward function — reward yang diterima
- **γ (gamma)**: Discount factor (0 ≤ γ ≤ 1) — menentukan seberapa penting reward masa depan

**Markov Property**: State saat ini berisi semua informasi yang diperlukan untuk memprediksi state berikutnya. Masa depan hanya bergantung pada state saat ini, bukan pada history.

**Value Function dan Policy:**
- **V(s)**: State-value function — expected return mulai dari state s
- **Q(s,a)**: Action-value function — expected return dari state s setelah melakukan action a
- **Optimal Policy π***: Policy yang memaksimalkan expected cumulative reward

**Contoh Konteks Pertahanan:**
- UAV otonom belajar navigasi optimal di medan perang
- Robot EOD belajar prosedur penjinakan bom yang aman
- Sistem alokasi resource pertahanan secara dinamis
- Agen simulasi pelatihan taktis adaptif

![Komponen Reinforcement Learning](images/ss14-04-reinforcement-learning-components.png)

*Gambar 14.4: Komponen utama Reinforcement Learning dan siklus interaksi agen-lingkungan*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Siklus interaksi Reinforcement Learning antara agen dan lingkungan dengan komponen MDP
STYLE: Ilustrasi vektor flat yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
LAYOUT: Diagram siklus dengan agen di kiri dan lingkungan di kanan, panah membentuk loop
COLORS: 
- Primer: #2563eb (biru) untuk agen dan komponen agent
- Sekunder: #10b981 (hijau) untuk reward positif
- Aksen: #f59e0b (oranye) untuk lingkungan
- Warning: #ef4444 (merah) untuk reward negatif/penalty
- Netral: #6b7280 (abu-abu) untuk state
- Latar: #ffffff (putih)
ELEMENTS:
1. Kiri: Kotak biru "AGEN" dengan ikon robot dan label "Policy π(s)"
2. Kanan: Kotak oranye "LINGKUNGAN" dengan ikon globe
3. Panah atas dari agen ke lingkungan: "Action (aₜ)" berwarna biru
4. Panah bawah kiri dari lingkungan ke agen: "State (sₜ₊₁)" berwarna abu-abu
5. Panah bawah kanan dari lingkungan ke agen: "Reward (rₜ₊₁)" berwarna hijau/merah
6. Kotak kecil di bawah: "MDP = (S, A, T, R, γ)" dengan penjelasan singkat tiap komponen
LABELS: "Agen", "Lingkungan", "Aksi (aₜ)", "State (sₜ₊₁)", "Reward (rₜ₊₁)", "Policy π: S → A", "MDP = (S, A, T, R, γ)"
SIZE: 800x500 piksel
FORMAT: PNG, latar putih
NEGATIVE: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Reinforcement Learning: Crash Course AI #9 | CrashCourse | 11:28 | https://www.youtube.com/watch?v=nIgIv4IfJ6s |
| 2 | Introduction to Reinforcement Learning | Mutual Information | 17:45 | https://www.youtube.com/watch?v=TCCjZe0y4Qc |
| 3 | Markov Decision Process (MDP) Explained | Steve Brunton | 15:47 | https://www.youtube.com/watch?v=my207WNoeyA |

### ✍️ Latihan Pemahaman

Setelah menonton video dan membaca ringkasan, jawab pertanyaan berikut:

1. Apa perbedaan fundamental antara reinforcement learning dengan supervised learning dan unsupervised learning?
2. Sebutkan dan jelaskan lima komponen MDP! Berikan contoh untuk masing-masing dalam skenario UAV patroli.
3. Apa arti dari Markov Property? Mengapa properti ini penting dalam formulasi MDP?
4. Jelaskan peran discount factor (γ). Apa dampaknya jika γ = 0 vs γ = 1?

---

## 5. Review Konsep: Q-Learning dan Perbandingan Paradigma ML (45 menit)

### Ringkasan Materi

**Q-Learning** adalah algoritma reinforcement learning yang bersifat **model-free** dan **off-policy**. Algoritma ini mempelajari Q-value untuk setiap pasangan (state, action) yang merepresentasikan expected cumulative reward.

**Formula Update Q-Learning:**

$$Q(s, a) \leftarrow Q(s, a) + \alpha \Big[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \Big]$$

Di mana:
- $\alpha$ (learning rate): Seberapa cepat agen belajar (0 < α ≤ 1)
- $\gamma$ (discount factor): Pentingnya reward masa depan (0 ≤ γ < 1)
- $r$: Reward yang diterima
- $s'$: State berikutnya
- $\max_{a'} Q(s', a')$: Estimasi reward maksimal dari state berikutnya

**Langkah-langkah Q-Learning:**
1. Inisialisasi Q-table dengan nol
2. Pilih action menggunakan strategi **ε-greedy** (explorasi vs eksploitasi)
3. Lakukan action, terima reward, observasi state baru
4. Update Q-value menggunakan formula di atas
5. Ulangi hingga konvergen

**Exploration vs Exploitation (ε-greedy):**
- **Exploration**: Dengan probabilitas ε, pilih action secara acak (mencoba hal baru)
- **Exploitation**: Dengan probabilitas (1-ε), pilih action dengan Q-value tertinggi (memanfaatkan pengetahuan)

**Perbandingan Tiga Paradigma ML:**

| Aspek | Supervised | Unsupervised | Reinforcement |
|-------|-----------|-------------|---------------|
| **Data** | Berlabel | Tidak berlabel | Reward signal |
| **Tujuan** | Prediksi | Temukan pola | Maksimalkan reward |
| **Feedback** | Langsung (label) | Tidak ada | Delayed (reward) |
| **Contoh** | Klasifikasi, Regresi | Clustering, PCA | Game, Robotika |

![Q-Learning Process](images/ss14-05-qlearning-update-process.png)

*Gambar 14.5: Proses update Q-table dalam Q-Learning*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Proses Q-Learning ditampilkan sebagai grid world sederhana 4x4 dengan Q-table update
STYLE: Ilustrasi vektor flat yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
LAYOUT: Dua bagian: (1) grid world di kiri, (2) Q-table di kanan dengan proses update
COLORS: 
- Primer: #2563eb (biru) untuk agen
- Sekunder: #10b981 (hijau) untuk goal state dan reward positif
- Aksen: #f59e0b (oranye) untuk Q-values yang diperbarui
- Warning: #ef4444 (merah) untuk obstacle/penalty
- Netral: #6b7280 (abu-abu) untuk sel grid kosong
- Latar: #ffffff (putih)
ELEMENTS:
1. Kiri: Grid 4x4 dengan agen (biru) di (0,0), goal (hijau) di (3,3), obstacle (merah) di (1,2)
2. Panah menunjukkan aksi yang dipilih agen (kanan)
3. Kanan: Tabel Q-values parsial menunjukkan Q(s,a) untuk beberapa state-action pairs
4. Formula update di bawah: Q(s,a) ← Q(s,a) + α[r + γ max Q(s',a') - Q(s,a)]
5. Sorotan oranye pada nilai Q yang baru saja diperbarui
LABELS: "Grid World", "Q-Table", "Agen", "Goal (+10)", "Obstacle (-5)", "Aksi: Kanan", "Update Q-Value"
SIZE: 900x500 piksel
FORMAT: PNG, latar putih
NEGATIVE: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Q-Learning Explained - A Reinforcement Learning Technique | Edureka | 12:47 | https://www.youtube.com/watch?v=qhRNvCVVJaA |
| 2 | Reinforcement Learning in 5 Minutes | Jordan Boyd-Graber | 5:56 | https://www.youtube.com/watch?v=Mut_u40Sqz4 |
| 3 | But what is Q-Learning? | CodeEmporium | 15:32 | https://www.youtube.com/watch?v=AhyznRSDjw8 |

### ✍️ Latihan Pemahaman

Setelah menonton video dan membaca ringkasan, jawab pertanyaan berikut:

1. Jelaskan mengapa Q-learning disebut algoritma "model-free"! Apa keuntungannya?
2. Apa trade-off antara exploration dan exploitation dalam ε-greedy? Bagaimana sebaiknya nilai ε diatur selama training?
3. Diberikan Q(s₁, kanan) = 5, α = 0.1, γ = 0.9, reward = 2, dan max Q(s₂, a') = 8. Hitung Q-value baru!
4. Berikan contoh masalah nyata di bidang pertahanan untuk masing-masing paradigma ML (supervised, unsupervised, reinforcement)!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| No | Tool/Platform | Deskripsi | Link |
|----|---------------|-----------|------|
| 1 | K-Means Visualization (Naftali Harris) | Visualisasi interaktif algoritma K-means step-by-step | https://www.naftaliharris.com/blog/visualizing-k-means-clustering/ |
| 2 | Setosa.io PCA Visualization | Visualisasi interaktif Principal Component Analysis | https://setosa.io/ev/principal-component-analysis/ |
| 3 | Clustering Playground (Scikit-learn) | Eksplorasi berbagai algoritma clustering | https://scikit-learn.org/stable/auto_examples/cluster/plot_cluster_comparison.html |
| 4 | RL Gridworld Demo | Simulasi reinforcement learning pada grid world | https://cs.stanford.edu/people/karpathy/reinforcejs/gridworld_dp.html |
| 5 | OpenAI Gym Documentation | Framework standar untuk eksperimen RL | https://gymnasium.farama.org/ |

### 📋 Tugas Eksplorasi

**Tugas 1: Eksplorasi K-Means (20 menit)**
1. Buka Naftali Harris K-Means Visualization
2. Coba dataset "Gaussian Mixture" dengan K=2, K=3, dan K=5
3. Amati bagaimana perubahan K mempengaruhi hasil clustering
4. Catat observasi: Apa yang terjadi jika K terlalu besar atau terlalu kecil?

**Tugas 2: Eksplorasi PCA (20 menit)**
1. Buka Setosa.io PCA Visualization
2. Drag data points untuk membuat distribusi berbeda (linear, circular, random)
3. Amati bagaimana PC1 dan PC2 berubah arah
4. Catat: Kapan PC1 menjelaskan hampir seluruh varians? Kapan tidak?

**Tugas 3: Eksplorasi RL Grid World (20 menit)**
1. Buka RL Gridworld Demo (Karpathy)
2. Amati bagaimana value function berubah selama iterasi
3. Ubah posisi reward dan obstacle
4. Catat: Bagaimana perubahan posisi reward mempengaruhi optimal policy?

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Playlist Video Lanjutan

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Unsupervised Machine Learning - Full Course | freeCodeCamp | 1:00:27 | https://www.youtube.com/watch?v=yQsOFWqpjkE |
| 2 | Reinforcement Learning Course - Full Machine Learning Tutorial | freeCodeCamp | 1:05:44 | https://www.youtube.com/watch?v=ELE2_Mftqocy |
| 3 | Clustering with DBSCAN, Clearly Explained | StatQuest with Josh Starmer | 9:34 | https://www.youtube.com/watch?v=RDZUdRSDOok |
| 4 | t-SNE, Clearly Explained | StatQuest with Josh Starmer | 11:47 | https://www.youtube.com/watch?v=NEaUSP4YerM |
| 5 | Deep Reinforcement Learning in 20 Minutes | Arxiv Insights | 19:12 | https://www.youtube.com/watch?v=SgC6AZss478 |

### 📖 Bacaan Tambahan

| No | Judul | Sumber | Link |
|----|-------|--------|------|
| 1 | An Introduction to K-Means Clustering | DataCamp Tutorial | https://www.datacamp.com/tutorial/k-means-clustering-python |
| 2 | Reinforcement Q-Learning from Scratch in Python | LearnDataSci | https://www.learndatasci.com/tutorials/reinforcement-q-learning-scratch-python-openai-gym/ |
| 3 | PCA Explained Simply | biostatsquid.com | https://biostatsquid.com/pca-simply-explained/ |
| 4 | Russell & Norvig, AIMA Chapter 19-22 | Textbook | Perpustakaan |

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| Kaggle Learn | Intro to Machine Learning | https://www.kaggle.com/learn/intro-to-machine-learning |
| Google Machine Learning Crash Course | Clustering | https://developers.google.com/machine-learning/clustering |
| HackerRank | AI Domain - ML | https://www.hackerrank.com/domains/ai |

### Section 8

#### Soal 1: K-Means Clustering Manual (★★)

Dataset posisi kapal mencurigakan di perairan (koordinat x, y):

| Data Point | x | y |
|------------|---|---|
| P1 | 1 | 2 |
| P2 | 2 | 1 |
| P3 | 4 | 5 |
| P4 | 5 | 4 |
| P5 | 8 | 8 |
| P6 | 9 | 7 |

Lakukan K-means clustering dengan K=3 dan centroid awal: C1=(1,2), C2=(4,5), C3=(9,7).

a) Hitung jarak Euclidean dari setiap data point ke setiap centroid  
b) Lakukan assignment ke cluster terdekat  
c) Hitung centroid baru  
d) Apakah algoritma sudah konvergen? Jika belum, lakukan iterasi berikutnya

---

#### Soal 2: Evaluasi Clustering (★★)

Diberikan hasil clustering dengan silhouette score berikut:

| K | Silhouette Score | WCSS |
|---|-----------------|------|
| 2 | 0.52 | 450 |
| 3 | 0.78 | 180 |
| 4 | 0.71 | 120 |
| 5 | 0.45 | 95 |
| 6 | 0.38 | 80 |

a) Berdasarkan silhouette score, berapa K optimal?  
b) Gambarkan sketsa elbow plot dan tentukan K optimal berdasarkan elbow method  
c) Apakah kedua metode memberikan rekomendasi yang sama? Jelaskan!

---

#### Soal 3: Q-Learning Manual (★★★)

Seorang agen robot patroli berada di grid 3x3 berikut:

```
┌─────┬─────┬─────┐
│  S  │     │  -5 │
├─────┼─────┼─────┤
│     │  X  │     │
├─────┼─────┼─────┤
│     │     │ +10 │
└─────┴─────┴─────┘
```

- S = Start (0,0), X = Obstacle (1,1), +10 = Goal (2,2), -5 = Penalty (0,2)
- Actions: Atas, Bawah, Kiri, Kanan
- α = 0.5, γ = 0.9, semua Q-values awal = 0

a) Dari state (0,0), agen memilih action "Kanan" dan berpindah ke (0,1) dengan reward = -1. Hitung Q(S₀₀, Kanan) yang baru!

b) Dari state (0,1), agen memilih action "Bawah" dan berpindah ke (1,1) yang merupakan obstacle dan kembali ke (0,1) dengan reward = -5. Hitung Q(S₀₁, Bawah) yang baru!

c) Jelaskan mengapa agen perlu melakukan eksplorasi meskipun sudah menemukan path ke goal!

---

#### Soal 4: Perbandingan Paradigma ML (★★)

Untuk setiap skenario pertahanan berikut, tentukan paradigma ML (supervised, unsupervised, reinforcement) yang paling sesuai dan jelaskan alasannya:

a) Mendeteksi malware baru dari pola traffic jaringan tanpa signature yang diketahui  
b) Mengklasifikasikan pesawat asing sebagai sipil atau militer berdasarkan profil radar yang sudah dilabeli  
c) Melatih drone otonom untuk navigasi melalui medan yang belum dikenal  
d) Mengelompokkan titik-titik konsentrasi pasukan musuh dari data IMINT  
e) Memprediksi waktu kegagalan peralatan berdasarkan data sensor historis

---

#### Soal 5: PCA Konseptual (★★)

Dataset sensor radar memiliki 50 fitur per target. Setelah PCA, diperoleh:

| Komponen | Eigenvalue | Kumulatif Varians (%) |
|----------|------------|----------------------|
| PC1 | 12.5 | 45% |
| PC2 | 6.8 | 69% |
| PC3 | 3.2 | 81% |
| PC4 | 1.9 | 88% |
| PC5 | 1.1 | 92% |
| PC6 | 0.7 | 95% |

a) Berapa komponen yang direkomendasikan jika threshold varians = 90%?  
b) Berapa rasio reduksi dimensi yang dicapai?  
c) Jelaskan keuntungan dan kerugian dari reduksi ini dalam konteks klasifikasi target radar!

---

## 9. Refleksi dan Diskusi (60 menit)

### 💭 Pertanyaan Refleksi

Renungkan dan jawab pertanyaan berikut secara tertulis:

1. **Pemahaman Konseptual**: Mengapa unsupervised learning penting meskipun tidak memiliki "jawaban benar" dalam data? Berikan analogi dari kehidupan sehari-hari.

2. **Aplikasi Pertahanan**: Bayangkan Anda ditugaskan merancang sistem surveillance maritim otonom. Paradigma ML mana yang akan Anda gunakan untuk setiap komponen berikut, dan mengapa?
   - Deteksi kapal mencurigakan dari radar
   - Pengelompokan pola navigasi
   - Pengambilan keputusan intercept

3. **Etika dan Tantangan**: Apa tantangan etis dari penggunaan reinforcement learning dalam sistem senjata otonom? Siapa yang bertanggung jawab jika agen RL membuat keputusan yang salah di medan perang?

4. **Koneksi Antar Materi**: Bagaimana konsep agen cerdas (Pertemuan 1) dan pencarian (Pertemuan 2-4) terhubung dengan reinforcement learning? Apakah RL agent termasuk jenis agen tertentu?

5. **Eksplorasi Mandiri**: Setelah mempelajari tiga paradigma ML, menurut Anda paradigma mana yang paling berpotensi untuk aplikasi pertahanan Indonesia? Jelaskan dengan contoh konkret.

### 🗣️ Forum Diskusi

Diskusikan topik berikut dengan rekan mahasiswa:

- **Topik 1**: "Apakah K-means clustering selalu merupakan pilihan terbaik untuk clustering? Kapan DBSCAN atau hierarchical clustering lebih unggul?"
- **Topik 2**: "Bagaimana reinforcement learning dapat digunakan untuk melatih agen dalam wargame simulation untuk pelatihan perwira?"
- **Topik 3**: "Apa perbedaan praktis antara menggunakan PCA dan teknik dimensionality reduction lain seperti t-SNE?"

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Unsupervised Learning dan K-Means selesai
- [ ] Section 2: Review Hierarchical Clustering dan Evaluasi selesai
- [ ] Section 3: Review PCA dan Dimensionality Reduction selesai
- [ ] Section 4: Review Reinforcement Learning dan MDP selesai
- [ ] Section 5: Review Q-Learning dan Perbandingan Paradigma selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 📚 Buku Referensi
| No | Judul | Bab |
|----|-------|-----|
| 1 | Russell & Norvig - AIMA (4th Ed.) | Chapter 19-22 |
| 2 | Mitchell - Machine Learning | Chapter 13 |
| 3 | Bishop - Pattern Recognition and Machine Learning | Chapter 9 |
| 4 | Sutton & Barto - Reinforcement Learning: An Introduction | Chapter 1-6 |

### 🌐 Kursus Online Gratis
| No | Kursus | Platform | Link |
|----|--------|----------|------|
| 1 | Machine Learning Crash Course | Google | https://developers.google.com/machine-learning/crash-course |
| 2 | Deep RL Course | Hugging Face | https://huggingface.co/learn/deep-rl-course |
| 3 | Intro to Machine Learning | Kaggle | https://www.kaggle.com/learn/intro-to-machine-learning |

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

**1.** Pada supervised learning, data memiliki label/target yang diketahui (misal: email berlabel spam/bukan spam). Pada unsupervised learning, data tidak memiliki label — algoritma harus menemukan struktur tersembunyi sendiri tanpa diberitahu jawaban yang benar.

**2.** Pemilihan centroid awal kritis karena K-means bisa terjebak di **local optimum**. Centroid awal yang buruk dapat menghasilkan cluster yang tidak optimal. Solusi: gunakan teknik K-means++ yang memilih centroid awal secara strategis (centroid berikutnya dipilih dengan probabilitas proporsional terhadap jarak dari centroid yang sudah ada).

**3.** Nilai K optimal ditentukan menggunakan **Elbow Method** (mencari titik "siku" pada plot K vs WCSS) atau **Silhouette Score** (memilih K dengan skor silhouette tertinggi). Bisa juga menggunakan domain knowledge.

**4.** Contoh: Menggunakan K-means pada fitur (kecepatan rata-rata, frekuensi kunjungan, durasi berlabuh, pola waktu) dari data AIS kapal. Cluster 1: kapal nelayan (kecepatan rendah, pola reguler), Cluster 2: kapal kargo (rute tetap, kecepatan sedang), Cluster 3: kapal mencurigakan (pola tidak reguler, sering berlabuh di lokasi tidak biasa).

### Section 2

**1.** Perbedaan utama: (a) K-means memerlukan K ditentukan di awal, hierarchical tidak; (b) K-means menghasilkan flat partition, hierarchical menghasilkan hierarki (dendrogram); (c) K-means lebih efisien untuk dataset besar O(nKt), hierarchical O(n²log n); (d) Hierarchical tidak bergantung pada inisialisasi random.

**2.** Pilih hierarchical ketika: jumlah cluster belum diketahui, hubungan hierarki penting, dataset relatif kecil. Contoh pertahanan: Mengelompokkan ancaman berdasarkan hierarki — level 1 (jenis: udara/laut/darat), level 2 (subtipe: pesawat tempur/bomber/drone), level 3 (model spesifik).

**3.** K optimal = **3** karena memiliki silhouette score tertinggi (0.78). Skor ini menunjukkan bahwa data points sangat cocok dengan clusternya sendiri dan terpisah baik dari cluster lain.

**4.** Elbow method sulit diinterpretasikan ketika tidak ada "siku" yang jelas pada kurva (kurva menurun secara bertahap). Alternatif: Silhouette Score, Gap Statistic, atau informasi domain expert.

### Section 3

**1.** Tujuan utama PCA adalah mereduksi dimensi data sambil mempertahankan varians maksimal. Termasuk unsupervised karena tidak memerlukan label — PCA hanya menganalisis struktur dan distribusi data untuk menemukan arah varians terbesar.

**2.** **Eigenvector** menentukan **arah** komponen utama (direction of maximum variance). **Eigenvalue** menentukan **besaran varians** yang ditangkap oleh komponen tersebut. **Komponen utama** adalah hasil proyeksi data ke eigenvector, diurutkan berdasarkan eigenvalue dari terbesar ke terkecil.

**3.** Jika threshold 85-90%: pertahankan **PC1 + PC2 + PC3** (kumulatif 81%, mendekati threshold) atau **PC1-PC4** (88%, memenuhi threshold 85%). Jika threshold ketat 90%, perlu PC1-PC5 (92%). Pilihan bergantung pada keseimbangan antara simplicity dan information preservation.

**4.** Standarisasi penting karena PCA sensitif terhadap **skala** fitur. Fitur dengan range besar akan mendominasi komponen utama. Misal, jika satu fitur berkisar 0-1000 dan fitur lain 0-1, PCA akan memilih arah fitur pertama meskipun belum tentu paling informatif.

### Section 4

**1.** Perbedaan fundamental: Supervised belajar dari data berlabel, unsupervised mencari pola tanpa label, RL belajar dari **interaksi** dengan lingkungan melalui trial-and-error. RL unik karena feedback berupa reward yang mungkin **delayed** (tidak langsung), dan agen harus menyeimbangkan exploration vs exploitation.

**2.** Lima komponen MDP untuk UAV patroli:
- **S (States)**: Posisi UAV, level baterai, lokasi target terdeteksi, kondisi cuaca
- **A (Actions)**: Terbang ke arah tertentu, hover, scan, kembali ke base, naik/turun altitude
- **T (Transition)**: P(posisi baru | posisi saat ini, action) — misalnya angin mempengaruhi perpindahan
- **R (Reward)**: +10 untuk deteksi target, -1 per langkah (efisiensi), -100 jika kehabisan baterai
- **γ (Discount)**: 0.9 — mementingkan reward masa depan tapi tetap memperhatikan efisiensi saat ini

**3.** Markov Property menyatakan bahwa state saat ini berisi **semua informasi** yang diperlukan untuk memprediksi masa depan — tidak perlu mengetahui history. Properti ini penting karena menyederhanakan komputasi: keputusan hanya bergantung pada state saat ini, bukan seluruh trajectory.

**4.** Jika **γ = 0**: Agen hanya peduli pada reward **langsung** (myopic/serakah), mengabaikan konsekuensi jangka panjang. Jika **γ = 1**: Agen menilai reward masa depan **sama pentingnya** dengan reward saat ini, bisa menyebabkan infinite sum pada episodic tasks. Biasanya γ dipilih antara 0.9-0.99.

### Section 5

**1.** Q-learning disebut "model-free" karena tidak memerlukan model eksplisit dari lingkungan (transition probability dan reward function). Agen belajar langsung dari pengalaman berinteraksi dengan lingkungan. Keuntungan: dapat diterapkan tanpa pengetahuan lengkap tentang dinamika lingkungan, lebih fleksibel.

**2.** Trade-off: Exploration membantu menemukan strategi baru yang mungkin lebih baik, tapi membuang waktu pada action suboptimal. Exploitation memanfaatkan pengetahuan terbaik saat ini, tapi bisa terjebak di local optimum. Biasanya ε dimulai tinggi (misal 1.0) dan **menurun secara bertahap** (decay) ke nilai kecil (misal 0.01) — awalnya banyak eksplorasi, kemudian lebih banyak eksploitasi.

**3.** Perhitungan:
$$Q_{baru}(s_1, kanan) = 5 + 0.1 \times [2 + 0.9 \times 8 - 5]$$
$$= 5 + 0.1 \times [2 + 7.2 - 5]$$
$$= 5 + 0.1 \times 4.2$$
$$= 5 + 0.42 = 5.42$$

**4.** Contoh pertahanan:
- **Supervised**: Klasifikasi citra satelit (pesawat militer vs sipil) menggunakan data latih yang sudah dilabeli ahli intelijen
- **Unsupervised**: Clustering pola aktivitas jaringan untuk mendeteksi anomali cyber yang belum memiliki signature
- **Reinforcement**: Melatih drone otonom untuk navigasi dan penghindar ancaman di lingkungan yang dinamis dan belum dipetakan

### Section 8

#### Jawaban Soal 1: K-Means Clustering Manual

**a) Jarak Euclidean:**

| Data Point | Ke C1(1,2) | Ke C2(4,5) | Ke C3(9,7) |
|------------|-----------|-----------|-----------|
| P1(1,2) | 0.00 | 4.24 | 9.43 |
| P2(2,1) | 1.41 | 4.47 | 9.22 |
| P3(4,5) | 4.24 | 0.00 | 5.39 |
| P4(5,4) | 4.47 | 1.41 | 5.00 |
| P5(8,8) | 9.22 | 5.00 | 1.41 |
| P6(9,7) | 9.43 | 5.39 | 0.00 |

**b) Assignment:**
- Cluster 1: {P1(1,2), P2(2,1)}
- Cluster 2: {P3(4,5), P4(5,4)}
- Cluster 3: {P5(8,8), P6(9,7)}

**c) Centroid baru:**
- C1 = ((1+2)/2, (2+1)/2) = (1.5, 1.5)
- C2 = ((4+5)/2, (5+4)/2) = (4.5, 4.5)
- C3 = ((8+9)/2, (8+7)/2) = (8.5, 7.5)

**d)** Perlu iterasi berikutnya karena centroid berubah. Namun, dengan menghitung ulang jarak, assignment tidak berubah → **konvergen setelah iterasi ke-2**.

#### Jawaban Soal 2: Evaluasi Clustering

**a)** K optimal berdasarkan silhouette score = **3** (skor 0.78, tertinggi).

**b)** Elbow plot menunjukkan penurunan WCSS tajam dari K=2 ke K=3 (450→180), kemudian melambat. Titik siku terletak di **K=3**.

**c)** Ya, kedua metode merekomendasikan **K=3**. Ini memberikan konfirmasi kuat bahwa 3 cluster adalah jumlah optimal untuk dataset ini.

#### Jawaban Soal 3: Q-Learning Manual

**a)** Q(S₀₀, Kanan):
$$Q(S_{00}, Kanan) = 0 + 0.5 \times [-1 + 0.9 \times \max(Q(S_{01}, a')) - 0]$$
$$= 0 + 0.5 \times [-1 + 0.9 \times 0 - 0]$$
$$= 0 + 0.5 \times (-1) = -0.5$$

**b)** Q(S₀₁, Bawah) — agen mencoba masuk obstacle, kembali ke (0,1):
$$Q(S_{01}, Bawah) = 0 + 0.5 \times [-5 + 0.9 \times \max(Q(S_{01}, a')) - 0]$$
$$= 0 + 0.5 \times [-5 + 0.9 \times 0 - 0]$$
$$= 0 + 0.5 \times (-5) = -2.5$$

**c)** Eksplorasi diperlukan karena: (1) Path yang ditemukan pertama kali belum tentu optimal — mungkin ada path yang lebih pendek atau reward lebih besar; (2) Tanpa eksplorasi, agen terjebak di **local optimum**; (3) Lingkungan bisa berubah, sehingga eksplorasi membantu agen menemukan strategi adaptif baru.

#### Jawaban Soal 4: Perbandingan Paradigma

**a)** **Unsupervised** — Tanpa signature yang diketahui, perlu menemukan pola anomali dari data tanpa label (anomaly detection/clustering).

**b)** **Supervised** — Sudah memiliki data berlabel (profil radar + klasifikasi), gunakan classifier seperti decision tree atau neural network.

**c)** **Reinforcement Learning** — Drone belajar melalui trial-and-error di lingkungan yang belum dipetakan, menerima reward untuk navigasi berhasil dan penalty untuk tabrakan.

**d)** **Unsupervised** — Clustering titik-titik konsentrasi dari data citra tanpa label untuk menemukan pola pengelompokan.

**e)** **Supervised** — Data historis sensor sudah memiliki label (waktu kegagalan aktual), gunakan regression untuk prediksi.

#### Jawaban Soal 5: PCA Konseptual

**a)** Untuk threshold 90%: dibutuhkan **PC1 hingga PC5** (kumulatif 92% ≥ 90%).

**b)** Rasio reduksi = 5/50 = **10%** dimensi asli dipertahankan, atau reduksi **90%** dimensi.

**c)** Keuntungan: komputasi klasifikasi jauh lebih cepat (5 fitur vs 50), mengurangi noise dan overfitting, memori lebih efisien. Kerugian: kehilangan 8% informasi yang mungkin mengandung detail penting untuk membedakan target tertentu (misal target stealth yang memiliki signature subtil pada fitur minor).

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
