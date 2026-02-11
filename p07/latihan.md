# Latihan Pertemuan 07: Review dan Latihan Komprehensif (Persiapan UTS)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 07  
**Topik:** Review dan Latihan Komprehensif (Pertemuan 1-6)  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Petunjuk Pengerjaan

1. Kerjakan semua soal secara mandiri
2. Waktu pengerjaan: 150 menit (simulasi UTS)
3. Untuk soal pilihan ganda, pilih satu jawaban yang paling tepat
4. Untuk soal uraian, jawab dengan lengkap dan sistematis
5. Studi kasus memerlukan analisis mendalam dan penerapan konsep terintegrasi
6. Latihan ini mencakup seluruh materi Pertemuan 1-6

---

## Bagian A: Soal Pilihan Ganda (20 Soal)

### Soal 1 (Pertemuan 1)
Pendekatan AI yang paling banyak digunakan dalam pengembangan sistem AI modern adalah:

A. Thinking Humanly - mensimulasikan proses kognitif manusia  
B. Thinking Rationally - menggunakan logika formal untuk penalaran  
C. Acting Humanly - membuat sistem yang lulus Turing Test  
D. Acting Rationally - membuat sistem yang bertindak optimal  
E. Learning Adaptively - membuat sistem yang belajar mandiri

---

### Soal 2 (Pertemuan 1)
Sebuah robot vacuum yang dapat mengingat area mana yang sudah dibersihkan memerlukan jenis agen minimal:

A. Simple Reflex Agent  
B. Model-Based Reflex Agent  
C. Goal-Based Agent  
D. Utility-Based Agent  
E. Learning Agent

---

### Soal 3 (Pertemuan 1)
Permainan poker termasuk lingkungan dengan karakteristik:

A. Fully Observable, Deterministic  
B. Partially Observable, Stochastic  
C. Fully Observable, Stochastic  
D. Partially Observable, Deterministic  
E. Partially Observable, Episodic

---

### Soal 4 (Pertemuan 2)
Algoritma pencarian uninformed yang menjamin menemukan solusi optimal untuk semua kasus (step cost berbeda) adalah:

A. Breadth-First Search (BFS)  
B. Depth-First Search (DFS)  
C. Uniform-Cost Search (UCS)  
D. Iterative Deepening DFS  
E. Bidirectional Search

---

### Soal 5 (Pertemuan 2)
Kompleksitas ruang (space complexity) DFS dengan branching factor b dan maximum depth m adalah:

A. O(b^m)  
B. O(b^d)  
C. O(bm)  
D. O(m)  
E. O(b)

---

### Soal 6 (Pertemuan 2)
Struktur data yang digunakan oleh BFS untuk menyimpan frontier adalah:

A. Stack (LIFO)  
B. Queue (FIFO)  
C. Priority Queue  
D. Hash Table  
E. Binary Tree

---

### Soal 7 (Pertemuan 3)
Dalam algoritma A*, fungsi evaluasi f(n) dihitung dengan:

A. f(n) = h(n)  
B. f(n) = g(n)  
C. f(n) = g(n) + h(n)  
D. f(n) = g(n) × h(n)  
E. f(n) = max(g(n), h(n))

---

### Soal 8 (Pertemuan 3)
Sebuah heuristik h(n) dikatakan admissible jika:

A. h(n) > h*(n) untuk semua n  
B. h(n) ≥ h*(n) untuk semua n  
C. h(n) ≤ h*(n) untuk semua n  
D. h(n) = h*(n) untuk semua n  
E. h(n) < 0 untuk semua n

---

### Soal 9 (Pertemuan 3)
Untuk 8-puzzle, heuristik mana yang lebih informatif (dominates)?

A. h = 0 (tidak ada heuristik)  
B. h₁ = jumlah tile yang salah posisi  
C. h₂ = total Manhattan distance  
D. h₁ dan h₂ sama informatifnya  
E. Tergantung konfigurasi puzzle

---

### Soal 10 (Pertemuan 4)
Algoritma pencarian lokal yang dapat "meloloskan diri" dari local optima dengan menerima gerakan ke state lebih buruk adalah:

A. Hill Climbing  
B. Steepest Ascent Hill Climbing  
C. Simulated Annealing  
D. First-Choice Hill Climbing  
E. Random Restart Hill Climbing

---

### Soal 11 (Pertemuan 4)
Dalam Simulated Annealing, probabilitas menerima gerakan ke state lebih buruk dipengaruhi oleh:

A. Hanya nilai ΔE  
B. Hanya nilai temperature T  
C. Nilai ΔE dan temperature T  
D. Branching factor b  
E. Depth of solution d

---

### Soal 12 (Pertemuan 4)
Komponen algoritma genetika yang mensimulasikan reproduksi dengan menggabungkan "gen" dari dua parent adalah:

A. Mutation  
B. Selection  
C. Crossover  
D. Fitness evaluation  
E. Initialization

---

### Soal 13 (Pertemuan 5)
Dalam game tree dengan nilai minimax, jika MAX bergerak lebih dulu, maka MAX akan memilih:

A. Nilai minimum dari semua child  
B. Nilai maksimum dari semua child  
C. Nilai rata-rata dari semua child  
D. Nilai acak dari child  
E. Nilai child paling kiri

---

### Soal 14 (Pertemuan 5)
Alpha-beta pruning memotong cabang ketika:

A. α < β  
B. α = β  
C. α ≥ β  
D. α + β = 0  
E. α × β < 0

---

### Soal 15 (Pertemuan 5)
Dengan perfect ordering, alpha-beta pruning dapat mereduksi kompleksitas dari O(b^m) menjadi:

A. O(b^m)  
B. O(b^(m/2))  
C. O(m)  
D. O(b)  
E. O(log m)

---

### Soal 16 (Pertemuan 6)
Komponen yang BUKAN bagian dari definisi CSP adalah:

A. Variables  
B. Domains  
C. Constraints  
D. Heuristics  
E. Semua adalah komponen CSP

---

### Soal 17 (Pertemuan 6)
Algoritma AC-3 digunakan untuk:

A. Menemukan solusi optimal CSP  
B. Menjamin arc consistency  
C. Melakukan backtracking  
D. Menghitung heuristik  
E. Mengevaluasi fungsi utility

---

### Soal 18 (Pertemuan 6)
Heuristik MRV (Minimum Remaining Values) dalam backtracking CSP memilih variabel dengan:

A. Domain terbesar  
B. Domain terkecil  
C. Constraint terbanyak  
D. Constraint tersedikit  
E. Urutan alfabet pertama

---

### Soal 19 (Integrasi)
Untuk masalah scheduling mata kuliah dengan banyak constraint (ruang, waktu, dosen), algoritma yang paling sesuai adalah:

A. A* Search  
B. Minimax  
C. CSP dengan Backtracking  
D. Hill Climbing  
E. BFS

---

### Soal 20 (Integrasi)
Untuk membuat AI bermain tic-tac-toe secara optimal, algoritma yang paling sesuai adalah:

A. A* dengan Manhattan distance  
B. CSP dengan AC-3  
C. Simulated Annealing  
D. Minimax dengan alpha-beta pruning  
E. Genetic Algorithm

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐ (Pertemuan 1)
Sebuah sistem autopilot helikopter militer beroperasi dalam berbagai kondisi. Analisis karakteristik lingkungannya berdasarkan 6 dimensi!

---

### Soal 2 ⭐ (Pertemuan 1)
Jelaskan perbedaan antara Goal-Based Agent dan Utility-Based Agent! Berikan contoh skenario dimana Utility-Based Agent diperlukan sedangkan Goal-Based Agent tidak cukup!

---

### Soal 3 ⭐ (Pertemuan 2)
Diberikan graph berikut dengan S sebagai start dan G sebagai goal. Tentukan urutan node yang diekspansi oleh BFS!

```
    S
   /|\
  A B C
  |   |
  D   E
   \ /
    G
```

---

### Soal 4 ⭐ (Pertemuan 2)
Jelaskan mengapa DFS tidak menjamin menemukan solusi optimal! Berikan contoh ilustrasi!

---

### Soal 5 ⭐⭐ (Pertemuan 2)
Diberikan graph berbobot berikut. Gunakan UCS untuk menemukan jalur terpendek dari S ke G! Tunjukkan state priority queue di setiap langkah!

```
    S --3-- A --2-- G
    |       |
    5       1
    |       |
    B --4-- C --1-- G
```

---

### Soal 6 ⭐⭐ (Pertemuan 3)
Jelaskan perbedaan antara Greedy Best-First Search dan A*! Mengapa A* dijamin optimal sedangkan Greedy tidak?

---

### Soal 7 ⭐⭐ (Pertemuan 3)
Diberikan graph dengan heuristik berikut. Gunakan A* untuk menemukan jalur dari S ke G!

```
S --2-- A --4-- G
|       |
3       2
|       |
B --1-- C --2-- G

h(S)=5, h(A)=3, h(B)=4, h(C)=2, h(G)=0
```

---

### Soal 8 ⭐⭐ (Pertemuan 3)
Untuk grid pathfinding, jelaskan mengapa Euclidean distance adalah heuristik yang admissible! Apakah 2 × Euclidean distance juga admissible? Jelaskan!

---

### Soal 9 ⭐⭐ (Pertemuan 4)
Jelaskan tiga masalah yang dapat menyebabkan Hill Climbing gagal menemukan solusi optimal! Bagaimana Simulated Annealing mengatasi masalah-masalah ini?

---

### Soal 10 ⭐⭐ (Pertemuan 4)
Implementasikan 3 iterasi Hill Climbing untuk minimasi f(x) = (x-3)² dengan step size 1, starting dari x = 7!

---

### Soal 11 ⭐⭐ (Pertemuan 5)
Diberikan game tree berikut. Hitung nilai minimax dan tentukan langkah optimal untuk MAX!

```
            MAX
         /       \
       MIN       MIN
      / | \     / | \
     4  6  5   3  8  7
```

---

### Soal 12 ⭐⭐⭐ (Pertemuan 5)
Terapkan alpha-beta pruning pada game tree berikut (evaluasi kiri ke kanan). Identifikasi semua node yang di-prune!

```
              MAX
           /       \
         MIN       MIN
        / | \     / | \
       5  3  9   2  8  ?
```

---

### Soal 13 ⭐⭐ (Pertemuan 6)
Formulasikan masalah Sudoku 4×4 sebagai CSP! Sebutkan variables, domains, dan constraints-nya!

---

### Soal 14 ⭐⭐⭐ (Pertemuan 6)
Diberikan CSP berikut:
- Variables: A, B, C
- Domains: D(A) = {1,2,3}, D(B) = {1,2}, D(C) = {2,3}
- Constraints: A ≠ B, B < C

Terapkan AC-3 untuk mereduksi domain! Tunjukkan setiap langkah!

---

### Soal 15 ⭐⭐⭐ (Integrasi)
Sebuah robot SAR (Search and Rescue) harus menemukan korban di gedung yang runtuh. Robot memiliki sensor LIDAR dengan jangkauan terbatas, baterai terbatas, dan harus menghindari area berbahaya.

a) Buat analisis PEAS lengkap
b) Tentukan karakteristik lingkungan (6 dimensi)
c) Pilih jenis agen yang sesuai dengan justifikasi
d) Pilih algoritma pencarian yang sesuai dengan justifikasi

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Command and Control (C2) Pertahanan Udara

**Latar Belakang:**

TNI Angkatan Udara mengembangkan sistem Command and Control (C2) terintegrasi untuk pertahanan udara nasional. Sistem ini harus:

1. Mengintegrasikan data dari 10 stasiun radar yang tersebar di seluruh Indonesia
2. Mendeteksi, melacak, dan mengklasifikasikan objek udara (pesawat sipil, militer, drone, rudal)
3. Menentukan tingkat ancaman setiap objek terdeteksi
4. Mengalokasikan aset pertahanan (SAM, interceptor) secara optimal
5. Memberikan rekomendasi engagement kepada komandan
6. Belajar dari data historis untuk meningkatkan akurasi klasifikasi

**Data Operasional:**
- Rata-rata 500 objek udara terdeteksi per jam di seluruh coverage area
- Waktu respons maksimal untuk keputusan: 30 detik
- Aset pertahanan: 5 battery SAM, 2 skuadron interceptor
- False alarm rate harus < 1%

**Pertanyaan:**

**1a.** Lakukan analisis PEAS lengkap untuk sistem C2 ini! (15 poin)

**1b.** Analisis karakteristik lingkungan berdasarkan 6 dimensi! Berikan justifikasi untuk setiap dimensi! (15 poin)

**1c.** Sistem harus memprioritaskan target berdasarkan beberapa faktor. Rancang utility function yang mempertimbangkan: (20 poin)
- Military value target (0-100)
- Jarak ke aset vital (km)
- Kecepatan mendekati target (km/jam)
- Probabilitas identifikasi (0-1)
- Collateral damage risk (0-1)

Berikan bobot yang wajar dan contoh perhitungan untuk 2 skenario berbeda!

**1d.** Untuk fitur #3 (menentukan tingkat ancaman), algoritma AI mana yang paling sesuai? Pilih dan jelaskan antara: (15 poin)
- Rule-based Expert System
- Decision Tree
- Neural Network
- Bayesian Network

---

### Studi Kasus 2: Autonomous Patrol Boat untuk Keamanan Maritim

**Latar Belakang:**

TNI Angkatan Laut mengembangkan Autonomous Patrol Boat (APB) untuk mengamankan perairan perbatasan. APB bertugas:

1. Melakukan patroli rutin di area yang ditentukan
2. Mendeteksi dan mengidentifikasi kapal mencurigakan
3. Melakukan intercept dan memberi peringatan
4. Mengumpulkan bukti (foto, video, data AIS)
5. Menavigasi menghindari obstacle (karang, kapal lain)
6. Kembali ke pangkalan jika bahan bakar rendah

**Batasan Operasional:**
- Area patroli: 100 km × 50 km
- Kecepatan maksimal: 40 knot
- Endurance: 12 jam dengan bahan bakar penuh
- Sensor: Radar, kamera visible/thermal, sonar, AIS receiver
- Komunikasi: Radio HF/VHF dengan range terbatas

**Pertanyaan:**

**2a.** Buat analisis PEAS lengkap untuk APB! Identifikasi semua sensor dan aktuator yang diperlukan! (15 poin)

**2b.** Analisis karakteristik lingkungan APB berdasarkan 6 dimensi! (15 poin)

**2c.** APB harus merencanakan rute patroli yang memaksimalkan coverage sambil mempertimbangkan bahan bakar. Formulasikan sebagai: (20 poin)
- Masalah pencarian (state space, actions, goal, cost)
- CSP (variables, domains, constraints)

Pilih mana yang lebih sesuai dan jelaskan!

**2d.** Ketika APB mendeteksi kapal mencurigakan dan harus memutuskan untuk intercept atau melanjutkan patroli, desain decision tree sederhana untuk keputusan ini! Pertimbangkan faktor: (15 poin)
- Jarak ke target
- Level ancaman (berdasarkan klasifikasi)
- Sisa bahan bakar
- Jarak ke kapal kawan terdekat

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **D** | Acting Rationally adalah pendekatan dominan dalam AI modern. Fokus pada tindakan optimal, bukan meniru manusia atau menggunakan logika formal semata. |
| 2 | **B** | Model-Based Reflex Agent memiliki internal state untuk mengingat informasi. Simple Reflex tidak punya memori, Goal-Based perlu goal eksplisit. |
| 3 | **B** | Poker: Partially Observable (kartu lawan tersembunyi), Stochastic (elemen acak dari kartu yang dibagikan). |
| 4 | **C** | UCS menjamin optimalitas untuk semua kasus dengan step cost berbeda. BFS hanya optimal untuk unit cost. |
| 5 | **C** | DFS space complexity O(bm) karena hanya menyimpan satu path dari root ke node saat ini (depth m dengan branching b per level). |
| 6 | **B** | BFS menggunakan Queue (FIFO) - node yang ditemukan lebih dulu dieksplorasi lebih dulu. |
| 7 | **C** | A* evaluation function: f(n) = g(n) + h(n), kombinasi actual cost dan heuristic. |
| 8 | **C** | Admissible: h(n) ≤ h*(n), tidak pernah overestimate actual cost ke goal. |
| 9 | **C** | Manhattan distance (h₂) mendominasi misplaced tiles (h₁) karena h₂(n) ≥ h₁(n) untuk semua n. |
| 10 | **C** | Simulated Annealing menerima gerakan ke state lebih buruk dengan probabilitas P = e^(ΔE/T). |
| 11 | **C** | Probabilitas SA: P = e^(ΔE/T) dipengaruhi oleh ΔE (perbedaan nilai) dan T (temperature). |
| 12 | **C** | Crossover menggabungkan "gen" dari dua parent untuk menghasilkan offspring baru. |
| 13 | **B** | MAX player memilih nilai maksimum dari semua child untuk memaksimalkan utility. |
| 14 | **C** | Alpha-beta pruning: cut-off ketika α ≥ β karena path tersebut tidak akan dipilih. |
| 15 | **B** | Dengan perfect ordering, alpha-beta mereduksi O(b^m) menjadi O(b^(m/2)). |
| 16 | **D** | CSP terdiri dari Variables, Domains, dan Constraints. Heuristics bukan bagian definisi CSP (digunakan untuk solving). |
| 17 | **B** | AC-3 menjamin arc consistency dengan mereduksi domain berdasarkan binary constraints. |
| 18 | **B** | MRV memilih variabel dengan domain terkecil untuk fail-fast detection. |
| 19 | **C** | Scheduling dengan banyak constraint adalah masalah CSP klasik. |
| 20 | **D** | Tic-tac-toe adalah adversarial game, paling sesuai dengan Minimax + alpha-beta. |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Karakteristik Lingkungan Autopilot Helikopter Militer:**

| Dimensi | Nilai | Justifikasi |
|---------|-------|-------------|
| **Observable** | Partially Observable | Sensor tidak dapat melihat semua (radar terbatas, blind spots, cuaca buruk) |
| **Deterministic** | Stochastic | Cuaca berubah, angin tidak pasti, ancaman unpredictable |
| **Episodic** | Sequential | Keputusan penerbangan mempengaruhi posisi dan opsi selanjutnya |
| **Static** | Dynamic | Lingkungan berubah terus (cuaca, lalu lintas udara, ancaman) |
| **Discrete** | Continuous | Posisi, altitude, kecepatan dalam ruang kontinu |
| **Agents** | Multi-Agent | Helikopter lain (cooperative), musuh (competitive) |

---

#### Jawaban Soal 2 ⭐

**Perbedaan Goal-Based vs Utility-Based Agent:**

| Aspek | Goal-Based | Utility-Based |
|-------|------------|---------------|
| **Decision** | Binary (goal achieved/not) | Continuous (degree of satisfaction) |
| **Multiple Goals** | Tidak dapat menyeimbangkan | Dapat menyeimbangkan dengan utility |
| **Uncertainty** | Tidak handle probabilitas | Dapat compute expected utility |

**Contoh yang memerlukan Utility-Based:**
Self-driving car harus menyeimbangkan:
- Kecepatan (sampai cepat)
- Keamanan (menghindari kecelakaan)
- Kenyamanan (tidak ngerem mendadak)
- Efisiensi bahan bakar

Goal-Based hanya bisa "sampai tujuan atau tidak", tidak dapat menyeimbangkan trade-off ini.

---

#### Jawaban Soal 3 ⭐

**BFS Traversal:**

```
Iterasi 1: Expand S → Queue: [A, B, C]
Iterasi 2: Expand A → Queue: [B, C, D]
Iterasi 3: Expand B → Queue: [C, D]
Iterasi 4: Expand C → Queue: [D, E]
Iterasi 5: Expand D → Queue: [E, G]
Iterasi 6: Expand E → Queue: [G] (G sudah di-queue dari D)
Iterasi 7: Expand G → GOAL!
```

**Urutan ekspansi:** S → A → B → C → D → E → G

---

#### Jawaban Soal 4 ⭐

**Mengapa DFS tidak optimal:**

DFS mengeksplorasi depth-first tanpa mempertimbangkan path cost. DFS mengembalikan solusi **pertama** yang ditemukan, bukan yang **terbaik**.

**Ilustrasi:**
```
    S (start)
   / \
  A   B
  |   |
  G   G
cost:5  cost:2
```

Jika DFS explore kiri dulu:
- DFS menemukan S→A→G dengan cost 5
- Mengembalikan solusi tanpa explore S→B→G (cost 2)

**Solusi optimal** adalah S→B→G (cost 2), tapi DFS return S→A→G (cost 5).

---

#### Jawaban Soal 5 ⭐⭐

**UCS dari S ke G:**

| Step | Expand | g(n) | Priority Queue (node, g) |
|------|--------|------|--------------------------|
| 0 | - | - | [(S, 0)] |
| 1 | S | 0 | [(A, 3), (B, 5)] |
| 2 | A | 3 | [(C, 4), (B, 5), (G, 5)] |
| 3 | C | 4 | [(B, 5), (G, 5), (G, 5)] |
| 4 | B | 5 | [(G, 5), (G, 5), (G, 8)] |
| 5 | G | 5 | GOAL! |

**Jalur optimal:** S → A → G atau S → A → C → G dengan cost **5**

---

#### Jawaban Soal 6 ⭐⭐

**Perbedaan Greedy Best-First vs A*:**

| Aspek | Greedy | A* |
|-------|--------|-----|
| **Evaluasi** | f(n) = h(n) | f(n) = g(n) + h(n) |
| **Fokus** | Hanya estimasi ke goal | Path cost + estimasi |
| **Optimal** | Tidak | Ya (jika h admissible) |
| **Complete** | Tidak | Ya |

**Mengapa A* optimal:**
A* mempertimbangkan g(n) (actual cost dari start). Jika h(n) admissible, maka f(n) tidak pernah overestimate total cost. A* mengekspansi node dengan f(n) terkecil, sehingga ketika goal diekspansi, dijamin memiliki cost optimal.

Greedy hanya melihat h(n), bisa tertipu oleh heuristik yang mengarah ke jalan lebih panjang.

---

#### Jawaban Soal 7 ⭐⭐

**A* dari S ke G:**

| Step | Expand | g | h | f=g+h | Open List |
|------|--------|---|---|-------|-----------|
| 1 | S | 0 | 5 | 5 | [(A,2,3,5), (B,3,4,7)] |
| 2 | A | 2 | 3 | 5 | [(C,4,2,6), (B,3,4,7), (G,6,0,6)] |
| 3 | C | 4 | 2 | 6 | [(G,6,0,6), (B,3,4,7), (G,6,0,6)] |
| 4 | G | 6 | 0 | 6 | GOAL! |

**Jalur:** S → A → C → G dengan cost **6**

Alternatif S → A → G juga cost 6.

---

#### Jawaban Soal 8 ⭐⭐

**Euclidean Distance sebagai Admissible Heuristic:**

Euclidean distance adalah jarak garis lurus antara dua titik:
$$h(n) = \sqrt{(x_n - x_g)^2 + (y_n - y_g)^2}$$

**Admissible karena:**
- Jarak garis lurus adalah jarak **minimum** yang mungkin
- Tidak ada path yang lebih pendek dari garis lurus
- h(n) ≤ h*(n) selalu terpenuhi karena actual path ≥ straight line

**2 × Euclidean TIDAK admissible:**
- Jika actual path = 5 dan Euclidean = 4
- h = 2 × 4 = 8 > 5 = h*
- Overestimate! Melanggar admissibility.

---

#### Jawaban Soal 9 ⭐⭐

**Tiga masalah Hill Climbing:**

1. **Local Maxima:** Puncak lokal yang bukan global. Semua neighbor lebih buruk tapi bukan solusi optimal.

2. **Plateau:** Area datar dimana semua neighbor memiliki nilai sama. Tidak ada arah untuk improve.

3. **Ridge:** Sequence of local maxima yang sulit dinavigasi. Setiap langkah turun sebelum bisa naik lagi.

**Simulated Annealing mengatasi ini dengan:**
- Menerima gerakan ke state **lebih buruk** dengan probabilitas P = e^(ΔE/T)
- Temperature tinggi → lebih mungkin escape local optima
- Temperature menurun → konvergen ke solusi
- Dapat "melompat" keluar dari local maxima dan plateau

---

#### Jawaban Soal 10 ⭐⭐

**Hill Climbing untuk f(x) = (x-3)², minimasi, start x=7:**

Minimum di x=3 dengan f(3) = 0.

**Iterasi 1:** x = 7
- f(7) = (7-3)² = 16
- f(6) = (6-3)² = 9 ✓ (lebih kecil)
- f(8) = (8-3)² = 25
- Move ke x = 6

**Iterasi 2:** x = 6
- f(6) = 9
- f(5) = (5-3)² = 4 ✓
- f(7) = 16
- Move ke x = 5

**Iterasi 3:** x = 5
- f(5) = 4
- f(4) = (4-3)² = 1 ✓
- f(6) = 9
- Move ke x = 4

| Iterasi | x | f(x) | Next x |
|---------|---|------|--------|
| 1 | 7 | 16 | 6 |
| 2 | 6 | 9 | 5 |
| 3 | 5 | 4 | 4 |

---

#### Jawaban Soal 11 ⭐⭐

**Minimax pada game tree:**

```
            MAX
         /       \
       MIN       MIN
      / | \     / | \
     4  6  5   3  8  7
```

**Evaluasi bottom-up:**
- MIN kiri: min(4, 6, 5) = **4**
- MIN kanan: min(3, 8, 7) = **3**
- MAX: max(4, 3) = **4**

**Nilai minimax = 4**
**Langkah optimal MAX: Cabang kiri**

---

#### Jawaban Soal 12 ⭐⭐⭐

**Alpha-Beta Pruning:**

```
              MAX (α=-∞, β=+∞)
           /       \
         MIN       MIN
        / | \     / | \
       5  3  9   2  8  ?
```

**Evaluasi kiri ke kanan:**

1. **Evaluate 5:** MIN-kiri mendapat 5, β=5
2. **Evaluate 3:** MIN-kiri mendapat min(5,3)=3, β=3
3. **Evaluate 9:** MIN-kiri mendapat min(3,9)=3
4. MIN-kiri selesai dengan nilai **3**
5. MAX update α = max(-∞, 3) = **3**

6. Masuk MIN-kanan dengan α=3, β=+∞
7. **Evaluate 2:** MIN-kanan mendapat 2
8. Check: α(3) ≥ nilai(2)? 3 ≥ 2 → **YES! PRUNE!**

**Node yang di-prune:** Node dengan nilai 8 dan node dengan nilai ?

**Nilai minimax:** max(3, 2) = **3**

---

#### Jawaban Soal 13 ⭐⭐

**Sudoku 4×4 sebagai CSP:**

**Variables:** 16 cell, X_{ij} untuk baris i, kolom j (i,j ∈ {0,1,2,3})

**Domains:** D(X_{ij}) = {1, 2, 3, 4} untuk cell kosong, atau singleton untuk given values

**Constraints:**
1. **Row constraints:** AllDiff(X_{i0}, X_{i1}, X_{i2}, X_{i3}) untuk setiap i
2. **Column constraints:** AllDiff(X_{0j}, X_{1j}, X_{2j}, X_{3j}) untuk setiap j
3. **Box constraints:** AllDiff untuk setiap kotak 2×2
   - Box 1: AllDiff(X_{00}, X_{01}, X_{10}, X_{11})
   - Box 2: AllDiff(X_{02}, X_{03}, X_{12}, X_{13})
   - Box 3: AllDiff(X_{20}, X_{21}, X_{30}, X_{31})
   - Box 4: AllDiff(X_{22}, X_{23}, X_{32}, X_{33})

---

#### Jawaban Soal 14 ⭐⭐⭐

**AC-3 pada CSP:**

Variables: A, B, C
Domains: D(A)={1,2,3}, D(B)={1,2}, D(C)={2,3}
Constraints: A≠B, B<C

**Step 1:** Initialize queue dengan semua arc
Queue = [(A,B), (B,A), (B,C), (C,B)]

**Step 2:** Process arc (A,B) - constraint A≠B
- A=1: Ada B∈{1,2} dimana 1≠B? B=2 → Yes, keep 1
- A=2: Ada B∈{1,2} dimana 2≠B? B=1 → Yes, keep 2
- A=3: Ada B∈{1,2} dimana 3≠B? B=1,2 → Yes, keep 3
- D(A) tidak berubah

**Step 3:** Process arc (B,A) - constraint B≠A
- B=1: Ada A∈{1,2,3} dimana A≠1? A=2,3 → Yes, keep 1
- B=2: Ada A∈{1,2,3} dimana A≠2? A=1,3 → Yes, keep 2
- D(B) tidak berubah

**Step 4:** Process arc (B,C) - constraint B<C
- B=1: Ada C∈{2,3} dimana 1<C? C=2,3 → Yes, keep 1
- B=2: Ada C∈{2,3} dimana 2<C? C=3 → Yes, keep 2
- D(B) tidak berubah

**Step 5:** Process arc (C,B) - constraint B<C (equivalent: C>B)
- C=2: Ada B∈{1,2} dimana B<2? B=1 → Yes, keep 2
- C=3: Ada B∈{1,2} dimana B<3? B=1,2 → Yes, keep 3
- D(C) tidak berubah

**Hasil akhir:**
- D(A) = {1, 2, 3}
- D(B) = {1, 2}
- D(C) = {2, 3}

Domain tidak berubah setelah AC-3 (sudah arc consistent).

---

#### Jawaban Soal 15 ⭐⭐⭐

**a) PEAS Robot SAR:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Jumlah korban ditemukan, waktu pencarian, area coverage, survival rate robot |
| **Environment** | Gedung runtuh, puing, korban, area berbahaya, debu, gelap |
| **Actuators** | Motor penggerak, gripper, speaker (panggil korban), beacon |
| **Sensors** | LIDAR, thermal camera, audio sensor, CO2 sensor, accelerometer |

**b) Karakteristik Lingkungan:**

| Dimensi | Nilai | Justifikasi |
|---------|-------|-------------|
| Observable | Partially | LIDAR jangkauan terbatas, debu menghalangi |
| Deterministic | Stochastic | Puing bisa runtuh, korban bisa bergerak |
| Episodic | Sequential | Path yang diambil mempengaruhi opsi selanjutnya |
| Static | Dynamic | Gedung bisa runtuh lebih lanjut |
| Discrete | Continuous | Posisi dan navigasi dalam ruang 3D |
| Agents | Single | Satu robot (bisa Multi jika tim) |

**c) Jenis Agen:** **Utility-Based Agent**

Justifikasi:
- Perlu menyeimbangkan: menemukan korban vs menghindari bahaya vs menghemat baterai
- Goal-Based tidak cukup karena banyak trade-off
- Learning Agent bagus tapi tidak essential untuk misi pertama

**d) Algoritma Pencarian:** **A*** dengan heuristik jarak ke area yang belum dieksplorasi

Justifikasi:
- Perlu path optimal (baterai terbatas)
- Heuristik tersedia (jarak straight-line)
- Lebih efisien dari UCS karena guided search

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem C2 Pertahanan Udara

**1a. PEAS Analysis (15 poin)**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Detection rate (>99%), false alarm rate (<1%), response time (<30s), successful engagement rate, friendly asset survival, minimal collateral damage |
| **Environment** | Airspace Indonesia, 500+ objects/hour, friendly aircraft, civilian aircraft, enemy aircraft/missiles/drones, weather, electronic warfare |
| **Actuators** | Display systems, alert notifications, SAM targeting commands, interceptor tasking, communication broadcasts, report generation |
| **Sensors** | 10 radar stations (surveillance + tracking), IFF transponders, ADS-B receivers, ESM/ELINT, weather data, satellite feeds, intelligence reports |

**1b. Karakteristik Lingkungan (15 poin)**

| Dimensi | Nilai | Justifikasi |
|---------|-------|-------------|
| **Observable** | Partially Observable | Radar coverage gaps, stealth technology, jamming |
| **Deterministic** | Stochastic | Enemy behavior unpredictable, sensor noise, false returns |
| **Episodic** | Sequential | Resource allocation affects future capability, tracking continuity |
| **Static** | Dynamic | Objects moving at high speed, situation changes in seconds |
| **Discrete** | Continuous | Positions and velocities in 3D continuous space |
| **Agents** | Multi-Agent | Friendly assets (cooperative), enemy (competitive) |

**1c. Utility Function (20 poin)**

$$U(target) = w_1 \cdot V_{mil} + w_2 \cdot P_{prox} + w_3 \cdot V_{approach} + w_4 \cdot P_{id} - w_5 \cdot R_{collateral}$$

Dimana:
- V_mil = Military value (0-100), normalized
- P_prox = 1 - (distance_to_vital_asset / max_range), normalized 0-1
- V_approach = approach_speed / max_speed, normalized 0-1
- P_id = probability of correct identification (0-1)
- R_collateral = collateral damage risk (0-1)

**Bobot:** w₁=0.25, w₂=0.25, w₃=0.20, w₄=0.15, w₅=0.15

**Skenario 1: Bomber mendekati pangkalan**
| Faktor | Nilai |
|--------|-------|
| V_mil | 90/100 = 0.90 |
| P_prox | 1 - (50/200) = 0.75 |
| V_approach | 800/1000 = 0.80 |
| P_id | 0.95 |
| R_collateral | 0.10 |

$$U_1 = 0.25(0.90) + 0.25(0.75) + 0.20(0.80) + 0.15(0.95) - 0.15(0.10)$$
$$U_1 = 0.225 + 0.188 + 0.160 + 0.143 - 0.015 = 0.701$$

**Skenario 2: Drone kecil dekat kota**
| Faktor | Nilai |
|--------|-------|
| V_mil | 30/100 = 0.30 |
| P_prox | 1 - (20/200) = 0.90 |
| V_approach | 100/1000 = 0.10 |
| P_id | 0.70 |
| R_collateral | 0.60 |

$$U_2 = 0.25(0.30) + 0.25(0.90) + 0.20(0.10) + 0.15(0.70) - 0.15(0.60)$$
$$U_2 = 0.075 + 0.225 + 0.020 + 0.105 - 0.090 = 0.335$$

**Kesimpulan:** Target 1 (bomber) diprioritaskan (U=0.701 > 0.335)

**1d. Algoritma untuk Threat Classification (15 poin)**

**Pilihan: Bayesian Network**

Justifikasi:
1. **Handles uncertainty:** Sensor data noisy, tidak 100% akurat
2. **Probabilistic reasoning:** Menghasilkan probability of threat level, bukan binary
3. **Explainable:** Dapat menjelaskan reasoning ke komandan (berbeda dengan Neural Network)
4. **Incorporates prior knowledge:** Dapat encode domain expertise
5. **Updates incrementally:** Dapat update belief saat data baru masuk

**Struktur Bayesian Network:**
- Nodes: Radar signature, Speed, Altitude, Flight pattern, IFF response, Historical data
- Output: P(Threat = High | Evidence)

Rule-based terlalu rigid, Decision Tree tidak handle uncertainty well, Neural Network tidak explainable untuk keputusan kritis militer.

---

#### Studi Kasus 2: Autonomous Patrol Boat

**2a. PEAS Analysis (15 poin)**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Area coverage rate, detection rate, fuel efficiency, intercept success rate, evidence quality, collision avoidance rate |
| **Environment** | Sea area 100×50 km, target vessels, fishing boats, cargo ships, islands, reefs, weather, waves, other patrol boats |
| **Actuators** | Propulsion system (40 knot max), rudder, horn/siren, spotlight, camera gimbal, radio transmitter, data recorder |
| **Sensors** | Radar, visible camera, thermal camera, sonar, AIS receiver, GPS, compass, fuel gauge, wave sensor, anemometer |

**2b. Karakteristik Lingkungan (15 poin)**

| Dimensi | Nilai | Justifikasi |
|---------|-------|-------------|
| **Observable** | Partially Observable | Radar range terbatas, komunikasi HF/VHF terbatas |
| **Deterministic** | Stochastic | Cuaca berubah, target bergerak unpredictable |
| **Episodic** | Sequential | Konsumsi bahan bakar kumulatif, posisi mempengaruhi opsi |
| **Static** | Dynamic | Kapal lain bergerak, cuaca berubah |
| **Discrete** | Continuous | Posisi, heading, kecepatan dalam ruang kontinu |
| **Agents** | Multi-Agent | Target (competitive), patrol boats lain (cooperative) |

**2c. Formulasi Masalah (20 poin)**

**Sebagai Masalah Pencarian:**
- **State:** (posisi_APB, visited_waypoints, fuel_remaining, time)
- **Initial State:** (posisi_pangkalan, {}, fuel_full, t=0)
- **Actions:** Move to waypoint W_i
- **Transition Model:** Update posisi, kurangi fuel berdasarkan jarak
- **Goal Test:** Semua waypoints visited AND APB di pangkalan AND fuel > 0
- **Path Cost:** Negative coverage (maximize coverage = minimize negative)

**Sebagai CSP:**
- **Variables:** {W₁, W₂, ..., Wₙ} = urutan kunjungan waypoints
- **Domains:** Setiap variabel = slot waktu atau urutan
- **Constraints:**
  - Total distance ≤ fuel capacity
  - Kembali ke pangkalan sebelum fuel habis
  - Coverage harus merata (temporal constraint)

**Pilihan: Masalah Pencarian lebih sesuai** karena:
1. Path/sequence penting (bukan hanya assignment)
2. Optimisasi coverage dan fuel secara bersamaan
3. A* atau variant dapat digunakan dengan heuristik coverage

**2d. Decision Tree untuk Intercept (15 poin)**

```
                    [Fuel Level?]
                   /            \
              <20%              ≥20%
               |                  |
         [Return to Base]    [Threat Level?]
                             /      |      \
                          Low    Medium    High
                           |        |        |
                    [Continue]  [Distance?] [Distance?]
                               /    \      /     \
                            >10km  ≤10km  >15km  ≤15km
                              |      |      |      |
                         [Continue] [Intercept] [Follow] [Intercept]
                                        |               |
                                 [Backup nearby?]  [Call Backup]
                                    /      \
                                  Yes      No
                                   |        |
                              [Intercept] [Follow & Report]
```

**Logika:**
1. **Safety first:** Jika fuel <20%, kembali ke pangkalan
2. **Low threat:** Lanjutkan patroli (not worth deviating)
3. **Medium threat:** Intercept jika dekat (≤10km), ada backup
4. **High threat:** Intercept jika dalam range (≤15km), selalu call backup

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 10 poin
- Soal ⭐⭐⭐: maksimal 15 poin
- Total: 135 poin

### Studi Kasus
- Studi Kasus 1: 65 poin
- Studi Kasus 2: 65 poin
- Total: 130 poin

### Total Keseluruhan: 305 poin

---

## Checklist Persiapan UTS

Gunakan checklist ini untuk memastikan kesiapan menghadapi UTS:

### Pertemuan 1: Pengantar AI & Agen Cerdas
- [ ] Dapat menjelaskan 4 pendekatan AI
- [ ] Dapat membedakan 5 jenis agen
- [ ] Dapat menganalisis PEAS untuk sistem apapun
- [ ] Dapat menentukan 6 karakteristik lingkungan

### Pertemuan 2: Uninformed Search
- [ ] Dapat melakukan tracing BFS step-by-step
- [ ] Dapat melakukan tracing DFS step-by-step
- [ ] Dapat melakukan tracing UCS dengan priority queue
- [ ] Memahami kompleksitas masing-masing algoritma

### Pertemuan 3: Informed Search
- [ ] Dapat menghitung f(n) = g(n) + h(n)
- [ ] Memahami admissibility dan consistency
- [ ] Dapat melakukan tracing A*
- [ ] Dapat merancang heuristik admissible

### Pertemuan 4: Local Search
- [ ] Memahami konsep local optima, plateau, ridge
- [ ] Dapat melakukan iterasi Hill Climbing
- [ ] Memahami formula SA: P = e^(ΔE/T)
- [ ] Memahami komponen Genetic Algorithm

### Pertemuan 5: Game Playing
- [ ] Dapat menghitung nilai minimax
- [ ] Dapat menerapkan alpha-beta pruning
- [ ] Memahami kapan terjadi cut-off (α ≥ β)
- [ ] Dapat mengidentifikasi node yang di-prune

### Pertemuan 6: CSP
- [ ] Dapat memformulasikan masalah sebagai CSP
- [ ] Dapat menerapkan AC-3 step-by-step
- [ ] Memahami MRV dan LCV heuristics
- [ ] Dapat melakukan backtracking dengan forward checking

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
