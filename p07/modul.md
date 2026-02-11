# Modul 07: Review dan Latihan Komprehensif (Persiapan UTS)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 07  
**Topik:** Review dan Latihan Komprehensif (Pertemuan 1-6)  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Mengintegrasikan konsep-konsep kecerdasan artifisial yang telah dipelajari pada Pertemuan 1-6
2. Menjelaskan hubungan antar konsep: agen cerdas, pencarian, dan pemecahan masalah
3. Memilih algoritma pencarian yang tepat untuk berbagai karakteristik masalah
4. Menyelesaikan soal-soal komprehensif yang mengkombinasikan berbagai topik
5. Mengidentifikasi pola soal dan strategi penyelesaian untuk UTS
6. Menerapkan pengetahuan secara terintegrasi dalam konteks aplikasi nyata

---

## 1. Ringkasan Materi Pertemuan 1-6

### 1.1 Peta Konsep Materi UTS

![Peta Konsep Materi UTS](images/p07-01-peta-konsep-uts.png)

*Gambar 7.1: Peta konsep materi UTS Kecerdasan Artifisial*

### 1.2 Matriks Hubungan Antar Topik

| Topik | Konsep Kunci | Algoritma/Teknik | Aplikasi |
|-------|--------------|------------------|----------|
| **Agen Cerdas (P1)** | PEAS, karakteristik lingkungan | - | Analisis sistem AI |
| **Uninformed Search (P2)** | Completeness, optimality | BFS, DFS, UCS | Pathfinding sederhana |
| **Informed Search (P3)** | Heuristik, admissibility | Greedy, A* | Navigasi optimal |
| **Local Search (P4)** | Landscape, local optima | Hill Climbing, SA, GA | Optimisasi |
| **Game Playing (P5)** | Zero-sum, minimax value | Minimax, Alpha-Beta | AI permainan |
| **CSP (P6)** | Constraint propagation | AC-3, Backtracking | Scheduling, puzzle |

---

## 2. Review: Pengantar AI dan Agen Cerdas (Pertemuan 1)

### 2.1 Empat Pendekatan AI

> **Empat Pendekatan AI** menurut Russell & Norvig:
> 1. **Thinking Humanly** - Mensimulasikan proses kognitif manusia
> 2. **Thinking Rationally** - Menggunakan logika formal
> 3. **Acting Humanly** - Lulus Turing Test
> 4. **Acting Rationally** - Bertindak untuk hasil optimal (pendekatan dominan)

### 2.2 Lima Jenis Agen Cerdas

| Jenis Agen | Internal State | Goal | Utility | Learning |
|------------|:--------------:|:----:|:-------:|:--------:|
| Simple Reflex | ✗ | ✗ | ✗ | ✗ |
| Model-Based Reflex | ✓ | ✗ | ✗ | ✗ |
| Goal-Based | ✓ | ✓ | ✗ | ✗ |
| Utility-Based | ✓ | ✓ | ✓ | ✗ |
| Learning | ✓ | ✓ | ✓ | ✓ |

### 2.3 Enam Karakteristik Lingkungan

> **Karakteristik Lingkungan Tugas:**
> 1. **Observable**: Fully vs Partially
> 2. **Deterministic**: Deterministic vs Stochastic
> 3. **Episodic**: Episodic vs Sequential
> 4. **Static**: Static vs Dynamic
> 5. **Discrete**: Discrete vs Continuous
> 6. **Agents**: Single vs Multi-Agent

### 2.4 Kerangka PEAS

> **PEAS** adalah kerangka untuk menspesifikasikan lingkungan tugas:
> - **P**erformance measure - Kriteria kesuksesan
> - **E**nvironment - Objek dan kondisi di lingkungan
> - **A**ctuators - Tindakan yang dapat dilakukan
> - **S**ensors - Input yang dapat dipersepsi

#### Solved Problem 1 ⭐

**Soal:** Sebuah robot penjaga gudang militer harus mendeteksi penyusup dan melaporkan ke pusat komando. Identifikasi komponen PEAS-nya!

**Penyelesaian:**

*Step 1:* Identifikasi Performance measure
- Detection rate (persentase penyusup terdeteksi)
- False alarm rate (alarm palsu minimal)
- Response time (waktu deteksi hingga laporan)
- Coverage area (area yang dipantau)

*Step 2:* Identifikasi Environment
- Gudang (lorong, rak, pintu masuk)
- Penyusup potensial
- Personel yang sah
- Kondisi pencahayaan
- Objek bergerak (forklift, dll)

*Step 3:* Identifikasi Actuators
- Motor penggerak (roda/track)
- Alarm speaker
- Transmitter komunikasi
- Lampu sorot

*Step 4:* Identifikasi Sensors
- Kamera (visible, thermal)
- Motion detector
- Audio sensor
- LIDAR untuk navigasi
- GPS indoor positioning

**Jawaban:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Detection rate, false alarm rate, response time, coverage |
| **Environment** | Gudang, penyusup, personel sah, pencahayaan, objek |
| **Actuators** | Motor, alarm, transmitter, lampu sorot |
| **Sensors** | Kamera, motion detector, audio, LIDAR, positioning |

---

#### Solved Problem 2 ⭐

**Soal:** Tentukan karakteristik lingkungan untuk permainan catur online dengan timer!

**Penyelesaian:**

| Karakteristik | Nilai | Alasan |
|---------------|-------|--------|
| Observable | **Fully** | Semua bidak terlihat di papan |
| Deterministic | **Deterministic** | Tidak ada elemen acak |
| Episodic | **Sequential** | Setiap langkah mempengaruhi langkah berikutnya |
| Static | **Semi-dynamic** | Papan tidak berubah, tapi waktu berkurang |
| Discrete | **Discrete** | Posisi dan langkah terbatas |
| Agents | **Multi-agent** | Dua pemain (competitive) |

**Jawaban:** Catur online dengan timer bersifat Fully Observable, Deterministic, Sequential, Semi-dynamic (karena timer), Discrete, dan Multi-agent competitive.

---

## 3. Review: Algoritma Pencarian Uninformed (Pertemuan 2)

### 3.1 Formulasi Masalah Pencarian

> **Komponen Masalah Pencarian:**
> - **State Space**: Himpunan semua state yang mungkin
> - **Initial State**: State awal
> - **Actions**: Tindakan yang tersedia di setiap state
> - **Transition Model**: Hasil dari setiap action
> - **Goal Test**: Apakah state adalah goal
> - **Path Cost**: Biaya akumulatif dari initial ke state tertentu

### 3.2 Perbandingan Algoritma Uninformed Search

| Kriteria | BFS | DFS | UCS |
|----------|-----|-----|-----|
| **Complete?** | Ya (jika b finite) | Tidak (jika infinite) | Ya (jika step cost > 0) |
| **Optimal?** | Ya (unit cost) | Tidak | Ya |
| **Time** | O(b^d) | O(b^m) | O(b^(1+⌊C*/ε⌋)) |
| **Space** | O(b^d) | O(bm) | O(b^(1+⌊C*/ε⌋)) |
| **Data Structure** | Queue (FIFO) | Stack (LIFO) | Priority Queue |

Dimana: b = branching factor, d = depth of solution, m = maximum depth, C* = optimal cost, ε = minimum step cost

### 3.3 Visualisasi Urutan Ekspansi

![Perbandingan BFS dan DFS](images/p07-02-bfs-dfs-comparison.png)

*Gambar 7.2: Perbandingan urutan ekspansi BFS dan DFS*

#### Solved Problem 3 ⭐

**Soal:** Diberikan graph berikut dengan initial state S dan goal state G. Tentukan urutan node yang diekspansi oleh BFS!

![Graf untuk BFS](images/p07-03-bfs-graph.png)

*Gambar 7.3: Graf dengan initial state S dan goal state G*

**Penyelesaian:**

*Step 1:* Inisialisasi
- Queue: [S]
- Visited: {}

*Step 2:* Iterasi BFS
```
Iterasi 1: Expand S → Queue: [A, B, C], Visited: {S}
Iterasi 2: Expand A → Queue: [B, C, D], Visited: {S, A}
Iterasi 3: Expand B → Queue: [C, D], Visited: {S, A, B}
Iterasi 4: Expand C → Queue: [D, E], Visited: {S, A, B, C}
Iterasi 5: Expand D → Queue: [E, G], Visited: {S, A, B, C, D}
Iterasi 6: Expand E → Queue: [G], Visited: {S, A, B, C, D, E}
Iterasi 7: Expand G → GOAL FOUND!
```

**Jawaban:** Urutan ekspansi BFS: **S → A → B → C → D → E → G**

---

#### Solved Problem 4 ⭐⭐

**Soal:** Diberikan graph berbobot berikut. Gunakan UCS untuk menemukan jalur terpendek dari S ke G!

![Graf Berbobot untuk UCS](images/p07-04-ucs-weighted-graph.png)

*Gambar 7.4: Graf berbobot untuk demonstrasi UCS*

**Penyelesaian:**

*Step 1:* Inisialisasi
- Priority Queue: [(S, 0)]
- Visited: {}

*Step 2:* Iterasi UCS

| Iterasi | Expand | g(n) | Add to PQ | PQ setelah update |
|---------|--------|------|-----------|-------------------|
| 1 | S | 0 | (A,2), (B,4) | [(A,2), (B,4)] |
| 2 | A | 2 | (G,5), (C,3) | [(C,3), (B,4), (G,5)] |
| 3 | C | 3 | (B,5) | [(B,4), (G,5)] |
| 4 | B | 4 | (C,6) skip | [(G,5)] |
| 5 | G | 5 | GOAL! | - |

*Step 3:* Rekonstruksi jalur
- G ← A ← S
- Total cost: 2 + 3 = 5

**Jawaban:** 
- Jalur optimal: **S → A → G**
- Total cost: **5**
- Urutan ekspansi: S, A, C, B, G

---

## 4. Review: Algoritma Pencarian Informed (Pertemuan 3)

### 4.1 Konsep Heuristik

> **Heuristik h(n)** adalah estimasi biaya dari node n ke goal.
> 
> **Admissible Heuristic**: h(n) ≤ h*(n) untuk semua n, dimana h*(n) adalah biaya aktual.
> 
> **Consistent Heuristic**: h(n) ≤ c(n,a,n') + h(n') untuk setiap successor n'.

### 4.2 Algoritma A*

> **Fungsi Evaluasi A*:**
> $$f(n) = g(n) + h(n)$$
> 
> dimana:
> - g(n) = biaya aktual dari start ke n
> - h(n) = estimasi biaya dari n ke goal
> - f(n) = estimasi total cost melalui n

### 4.3 Perbandingan Greedy vs A*

| Aspek | Greedy Best-First | A* |
|-------|-------------------|-----|
| **Evaluasi** | f(n) = h(n) | f(n) = g(n) + h(n) |
| **Complete?** | Tidak | Ya |
| **Optimal?** | Tidak | Ya (jika h admissible) |
| **Fokus** | Serakah ke goal | Seimbang path cost + heuristic |

#### Solved Problem 5 ⭐⭐

**Soal:** Diberikan graph dengan heuristik h(n) sebagai berikut. Gunakan algoritma A* untuk menemukan jalur dari S ke G!

```
Graph:
S --1-- A --4-- G
|       |
3       2
|       |
B --1-- C --3-- G

Heuristik:
h(S)=5, h(A)=3, h(B)=4, h(C)=2, h(G)=0
```

**Penyelesaian:**

*Step 1:* Inisialisasi
- Open: [(S, f=0+5=5)]
- Closed: {}

*Step 2:* Iterasi A*

| Iter | Expand | g | h | f=g+h | Add to Open |
|------|--------|---|---|-------|-------------|
| 1 | S | 0 | 5 | 5 | (A,1,3,4), (B,3,4,7) |
| 2 | A | 1 | 3 | 4 | (G,5,0,5), (C,3,2,5) |
| 3 | C | 3 | 2 | 5 | (G,6,0,6), (B,4,4,8) |
| 4 | G | 5 | 0 | 5 | GOAL! |

*Step 3:* Pilih node dengan f minimum
- Setelah iter 2: Open = [(A,4), (B,7)] → expand A
- Setelah iter 3: Open = [(G,5), (C,5), (B,7)] → expand C (atau G, sama f)
- Expand G dengan f=5

*Step 4:* Rekonstruksi jalur
- G ← A ← S
- Cost: 1 + 4 = 5

**Jawaban:**
- Jalur optimal: **S → A → G**
- Total cost: **5**
- f(goal) = 5

---

#### Solved Problem 6 ⭐⭐

**Soal:** Untuk 8-puzzle, jelaskan dua heuristik yang umum digunakan dan buktikan bahwa keduanya admissible!

**Penyelesaian:**

**Heuristik 1: Misplaced Tiles (h₁)**
- Menghitung jumlah tile yang tidak pada posisi goal

*Contoh:*
```
Current:        Goal:
1 2 3           1 2 3
4 _ 5    →      4 5 6
7 8 6           7 8 _
```
h₁ = 3 (tile 5, 6, dan blank tidak pada posisi)

*Admissibility:* Setiap tile yang salah posisi memerlukan **minimal 1 gerakan** untuk kembali ke posisi yang benar. Jadi h₁(n) ≤ h*(n). ✓

**Heuristik 2: Manhattan Distance (h₂)**
- Jumlah jarak Manhattan setiap tile ke posisi goalnya

*Contoh yang sama:*
- Tile 5: posisi (1,2) → goal (1,1) = |2-1| = 1
- Tile 6: posisi (2,2) → goal (1,2) = |2-1| = 1
- Blank: posisi (1,1) → goal (2,2) = |1-2|+|1-2| = 2

h₂ = 1 + 1 + 2 = 4

*Admissibility:* Setiap tile harus bergerak **minimal** sejarak Manhattan distance-nya (tidak ada shortcut). Jadi h₂(n) ≤ h*(n). ✓

**Jawaban:**
- **h₁ (Misplaced Tiles)**: Admissible karena setiap tile minimal perlu 1 move
- **h₂ (Manhattan Distance)**: Admissible karena tile tidak bisa "melompat"
- h₂ lebih informatif (h₂ ≥ h₁) sehingga A* dengan h₂ lebih efisien

---

## 5. Review: Pencarian Lokal dan Optimisasi (Pertemuan 4)

### 5.1 Konsep Pencarian Lokal

> **Pencarian Lokal** hanya menyimpan state saat ini (bukan path) dan bergerak ke state tetangga yang lebih baik. Cocok untuk masalah optimisasi dimana path tidak penting.

### 5.2 Hill Climbing

> **Hill Climbing** selalu bergerak ke neighbor dengan nilai terbaik. Dapat terjebak di:
> - **Local maxima**: Puncak lokal yang bukan global
> - **Plateau**: Area datar tanpa peningkatan
> - **Ridge**: Urutan puncak lokal yang sulit dinavigasi

### 5.3 Simulated Annealing

> **Simulated Annealing** menerima gerakan ke state yang lebih buruk dengan probabilitas:
> $$P = e^{\Delta E / T}$$
> dimana ΔE = f(next) - f(current) dan T = temperature

### 5.4 Perbandingan Algoritma Pencarian Lokal

| Algoritma | Kelebihan | Kekurangan |
|-----------|-----------|------------|
| **Hill Climbing** | Sederhana, cepat | Terjebak local optima |
| **Random Restart HC** | Mengurangi stuck | Perlu banyak restart |
| **Simulated Annealing** | Dapat escape local optima | Perlu tuning temperature |
| **Genetic Algorithm** | Eksplorasi luas, parallel | Kompleks, perlu tuning |

#### Solved Problem 7 ⭐

**Soal:** Dalam masalah N-Queens, jelaskan bagaimana hill climbing dapat terjebak di local minimum!

**Penyelesaian:**

*Step 1:* Definisi objective function
- Objective: Minimasi jumlah pasangan queen yang saling menyerang
- Goal: h = 0 (tidak ada queen yang saling serang)

*Step 2:* Ilustrasi local minimum
```
Konfigurasi dengan h=1 (1 pasangan menyerang):
. Q . .
. . . Q
Q . . .
. . Q .

Semua gerakan (pindah queen dalam kolom) menghasilkan h ≥ 1
→ Local minimum! Tidak bisa improve tapi bukan solusi.
```

*Step 3:* Analisis
- Hill climbing akan berhenti di konfigurasi ini
- Perlu "sideways move" atau restart untuk escape

**Jawaban:** Hill climbing terjebak ketika semua neighbor memiliki nilai objective sama atau lebih buruk, padahal state saat ini bukan goal. Pada 8-Queens, ini terjadi pada sekitar 86% random initial states.

---

#### Solved Problem 8 ⭐⭐

**Soal:** Implementasikan satu iterasi simulated annealing untuk fungsi f(x) = -x² dengan current x=3, neighbor x=4, dan T=10. Apakah move diterima?

**Penyelesaian:**

*Step 1:* Hitung nilai fungsi (maximize f)
- f(current) = f(3) = -(3)² = -9
- f(next) = f(4) = -(4)² = -16

*Step 2:* Hitung ΔE
- ΔE = f(next) - f(current) = -16 - (-9) = -7

*Step 3:* Karena ΔE < 0 (move ke state lebih buruk), hitung probabilitas
$$P = e^{\Delta E / T} = e^{-7/10} = e^{-0.7} \approx 0.497$$

*Step 4:* Tentukan apakah diterima
- Generate random number r ∈ [0,1]
- Jika r < 0.497 → Accept move
- Jika r ≥ 0.497 → Reject move

**Jawaban:** Move dari x=3 ke x=4 memiliki probabilitas **49.7%** untuk diterima meskipun menghasilkan nilai lebih buruk. Pada temperature tinggi (T=10), algoritma masih mau mengeksplorasi.

---

## 6. Review: Pencarian Adversarial (Pertemuan 5)

### 6.1 Konsep Game Playing

> **Zero-Sum Game**: Total utility kedua pemain = 0. Keuntungan satu pemain = kerugian pemain lain.
> 
> **Minimax Value**: Utility optimal yang dapat dicapai pemain MAX jika lawan MIN bermain optimal.

### 6.2 Algoritma Minimax

> **Minimax** menghitung nilai optimal dengan asumsi kedua pemain bermain sempurna:
> - MAX memilih aksi dengan nilai tertinggi
> - MIN memilih aksi dengan nilai terendah

Kompleksitas: O(b^m) dimana b = branching factor, m = maximum depth

### 6.3 Alpha-Beta Pruning

> **Alpha-Beta Pruning** memotong cabang yang tidak perlu dieksplorasi:
> - **α (alpha)**: Nilai terbaik yang sudah ditemukan MAX (di sepanjang path)
> - **β (beta)**: Nilai terbaik yang sudah ditemukan MIN (di sepanjang path)
> - **Pruning**: Jika α ≥ β, potong sisa cabang

![Minimax dengan Alpha-Beta Pruning](images/p07-03-alpha-beta-pruning.png)

*Gambar 7.5: Ilustrasi Alpha-Beta Pruning*

#### Solved Problem 9 ⭐⭐

**Soal:** Diberikan game tree berikut. Hitung nilai minimax dan tentukan aksi optimal untuk MAX!

```
        MAX(?)
       /      \
    MIN(?)   MIN(?)
    /   \    /   \
   3     5  2     9
```

**Penyelesaian:**

*Step 1:* Evaluasi level MIN (dari bawah ke atas)
- MIN kiri: min(3, 5) = 3
- MIN kanan: min(2, 9) = 2

*Step 2:* Evaluasi level MAX (root)
- MAX: max(3, 2) = 3

*Step 3:* Tentukan aksi optimal
- MAX memilih cabang kiri (nilai 3)

```
        MAX(3)
       /      \
    MIN(3)   MIN(2)
    /   \    /   \
   3     5  2     9
```

**Jawaban:**
- Nilai minimax: **3**
- Aksi optimal untuk MAX: **Cabang kiri**

---

#### Solved Problem 10 ⭐⭐⭐

**Soal:** Terapkan alpha-beta pruning pada game tree berikut. Identifikasi node yang di-prune!

```
            MAX
         /       \
       MIN       MIN
      / | \     / | \
     3  5  6   2  1  ?
```
Evaluasi dari kiri ke kanan.

**Penyelesaian:**

*Step 1:* Inisialisasi
- α = -∞, β = +∞

*Step 2:* Evaluasi subtree kiri (MIN pertama)
```
Evaluate 3: MIN-kiri mendapat 3
Evaluate 5: MIN-kiri mendapat min(3,5) = 3
Evaluate 6: MIN-kiri mendapat min(3,6) = 3
MIN-kiri selesai dengan nilai 3
MAX update α = max(-∞, 3) = 3
```

*Step 3:* Evaluasi subtree kanan (MIN kedua)
```
Masuk ke MIN-kanan dengan α=3, β=+∞
Evaluate 2: MIN-kanan mendapat 2
  Check: α(3) ≥ nilai(2)? → Belum, continue
Evaluate 1: MIN-kanan mendapat min(2,1) = 1
  Check: α(3) ≥ nilai(1)? 3 ≥ 1 → YES! PRUNE!
  
Node terakhir (?) tidak perlu dievaluasi!
```

*Step 4:* Nilai final
```
MIN-kanan = 1
MAX = max(3, 1) = 3
```

**Jawaban:**
- Nilai minimax: **3**
- Node yang di-prune: **Node terakhir dengan nilai ?**
- Alasan: Setelah MIN-kanan mendapat nilai 1, dan α=3, maka α ≥ 1, sehingga sisa node di subtree MIN-kanan tidak perlu dievaluasi karena MAX tidak akan memilih jalur ini.

---

## 7. Review: Constraint Satisfaction Problems (Pertemuan 6)

### 7.1 Definisi CSP

> **Constraint Satisfaction Problem (CSP)** didefinisikan oleh:
> - **Variables**: X = {X₁, X₂, ..., Xₙ}
> - **Domains**: D = {D₁, D₂, ..., Dₙ}
> - **Constraints**: C = himpunan constraint yang membatasi nilai variabel

### 7.2 Teknik Penyelesaian CSP

| Teknik | Deskripsi |
|--------|-----------|
| **Node Consistency** | Setiap nilai dalam domain memenuhi unary constraint |
| **Arc Consistency (AC-3)** | Untuk setiap arc (Xi, Xj), setiap nilai di Di memiliki support di Dj |
| **Backtracking** | DFS dengan assignment satu variabel per level |
| **Forward Checking** | Hapus nilai inkonsisten dari domain saat assignment |
| **MRV Heuristic** | Pilih variabel dengan domain terkecil |
| **LCV Heuristic** | Pilih nilai yang paling sedikit membatasi variabel lain |

### 7.3 Algoritma AC-3

> **AC-3** memastikan arc consistency dengan:
> 1. Inisialisasi queue dengan semua arc
> 2. Untuk setiap arc (Xi, Xj), hapus nilai di Di yang tidak memiliki support di Dj
> 3. Jika Di berubah, tambahkan semua arc (Xk, Xi) ke queue
> 4. Ulangi sampai queue kosong

#### Solved Problem 11 ⭐

**Soal:** Formulasikan masalah pewarnaan peta 3 wilayah (A, B, C) yang bertetangga satu sama lain sebagai CSP!

**Penyelesaian:**

*Step 1:* Identifikasi variables
- X = {A, B, C}

*Step 2:* Identifikasi domains
- DA = DB = DC = {Merah, Hijau, Biru}

*Step 3:* Identifikasi constraints
- A ≠ B (A dan B bertetangga)
- A ≠ C (A dan C bertetangga)
- B ≠ C (B dan C bertetangga)

**Jawaban:**
```
Variables: X = {A, B, C}
Domains: Di = {Merah, Hijau, Biru} untuk semua i
Constraints: 
  - A ≠ B
  - A ≠ C
  - B ≠ C
```

Ini adalah masalah graph coloring dengan 3 warna.

---

#### Solved Problem 12 ⭐⭐

**Soal:** Diberikan CSP sederhana:
- Variables: X, Y
- Domains: Dx = {1, 2, 3}, Dy = {1, 2}
- Constraint: X > Y

Terapkan AC-3 untuk mereduksi domain!

**Penyelesaian:**

*Step 1:* Inisialisasi queue
- Queue = [(X, Y), (Y, X)]

*Step 2:* Proses arc (X, Y)
- Untuk setiap nilai di Dx, cek apakah ada support di Dy:
  - X=1: Apakah ada Y di Dy dimana 1 > Y? Y=? → Tidak ada! Hapus 1 dari Dx
  - X=2: Apakah ada Y di Dy dimana 2 > Y? Y=1 → Ada! Keep 2
  - X=3: Apakah ada Y di Dy dimana 3 > Y? Y=1,2 → Ada! Keep 3
- Dx berubah dari {1,2,3} menjadi {2,3}
- Tambahkan (Y, X) ke queue (sudah ada, skip)

*Step 3:* Proses arc (Y, X)
- Untuk setiap nilai di Dy, cek apakah ada support di Dx:
  - Y=1: Apakah ada X di Dx dimana X > 1? X=2,3 → Ada! Keep 1
  - Y=2: Apakah ada X di Dx dimana X > 2? X=3 → Ada! Keep 2
- Dy tidak berubah

*Step 4:* Queue kosong, selesai

**Jawaban:**
- Domain setelah AC-3:
  - Dx = {2, 3} (nilai 1 dihapus)
  - Dy = {1, 2} (tidak berubah)

---

#### Solved Problem 13 ⭐⭐⭐

**Soal:** Selesaikan Sudoku 4×4 mini berikut menggunakan backtracking dengan MRV heuristic!

![Sudoku 4×4 Mini - Puzzle Awal](images/p07-13-sudoku-4x4-initial.png)

*Gambar 7.6: Sudoku 4×4 mini (puzzle awal)*

**Penyelesaian:**

*Step 1:* Formulasi CSP
- Variables: Setiap cell kosong (6 variabel)
- Domains: {1, 2, 3, 4} dikurangi berdasarkan constraint
- Constraints: AllDiff per baris, kolom, dan kotak 2×2

*Step 2:* Hitung domain awal setiap cell kosong

| Cell | Domain (setelah constraint propagation) |
|------|----------------------------------------|
| (0,1) | {2, 3} - tidak boleh 1,4 (baris), 1,4 (kolom) → {2,3} |
| (0,2) | {2, 3} |
| (1,0) | {2, 3} |
| (1,1) | {2, 3, 4} |
| (1,3) | {3} ← Domain terkecil setelah propagasi |
| ... | ... |

*Step 3:* MRV memilih (1,3) karena domain = {3}
- Assign (1,3) = 3

*Step 4:* Propagate dan lanjutkan

![Sudoku 4×4 Mini - Solusi](images/p07-13-sudoku-4x4-solution.png)

*Gambar 7.7: Sudoku 4×4 mini (solusi)*

**Jawaban:**

![Sudoku 4×4 Mini - Solusi](images/p07-13-sudoku-4x4-solution.png)

MRV heuristic memilih variabel dengan domain terkecil, mempercepat pencarian dengan mendeteksi failure lebih awal.

---

## 8. Integrasi Konsep dan Pemilihan Algoritma

### 8.1 Panduan Pemilihan Algoritma

![Flowchart Pemilihan Algoritma](images/p07-04-algorithm-selection-flowchart.png)

*Gambar 7.8: Panduan pemilihan algoritma pencarian*

### 8.2 Tabel Keputusan Pemilihan Algoritma

| Karakteristik Masalah | Algoritma yang Sesuai |
|----------------------|----------------------|
| Adversarial, zero-sum game | Minimax, Alpha-Beta |
| Constraint satisfaction | CSP + AC-3 + Backtracking |
| Optimisasi tanpa path | Hill Climbing, SA, GA |
| Path finding dengan heuristik | A*, Greedy Best-First |
| Path finding tanpa heuristik, perlu optimal | UCS |
| Path finding tanpa heuristik, perlu complete | BFS |
| Memori terbatas | DFS, IDDFS |

#### Solved Problem 14 ⭐⭐

**Soal:** Untuk setiap skenario berikut, tentukan algoritma yang paling sesuai!

a) Menemukan rute terpendek di peta kota (dengan koordinat)
b) Menentukan jadwal mata kuliah tanpa konflik
c) Bermain tic-tac-toe
d) Menentukan konfigurasi optimal antena radar

**Penyelesaian:**

**(a) Rute terpendek di peta kota:**
- Memiliki heuristik natural (jarak Euclidean/Manhattan)
- Perlu path optimal
- **Algoritma: A*** dengan heuristik jarak ke tujuan

**(b) Jadwal mata kuliah:**
- Banyak constraint (ruang, waktu, dosen)
- Masalah assignment, bukan path
- **Algoritma: CSP dengan Backtracking + AC-3**

**(c) Tic-tac-toe:**
- Adversarial (2 pemain)
- Zero-sum game
- **Algoritma: Minimax** (atau Alpha-Beta untuk efisiensi)

**(d) Konfigurasi optimal antena:**
- Optimisasi posisi dalam ruang kontinu
- Hanya perlu solusi, bukan path
- Banyak local optima
- **Algoritma: Simulated Annealing** atau Genetic Algorithm

**Jawaban:**
| Skenario | Algoritma |
|----------|-----------|
| Rute di peta | A* |
| Jadwal kuliah | CSP + Backtracking |
| Tic-tac-toe | Minimax |
| Konfigurasi antena | Simulated Annealing / GA |

---

## 9. Latihan Soal Komprehensif

### 9.1 Soal Tipe Analisis

#### Solved Problem 15 ⭐

**Soal:** Sebuah drone delivery harus mengirim paket dari warehouse ke 5 lokasi berbeda dengan baterai terbatas. Formulasikan sebagai masalah pencarian dan tentukan karakteristik lingkungannya!

**Penyelesaian:**

*Step 1:* Formulasi masalah pencarian
- **State**: (lokasi_drone, {lokasi_belum_dikunjungi}, baterai_sisa)
- **Initial State**: (warehouse, {L1,L2,L3,L4,L5}, baterai_penuh)
- **Actions**: Terbang ke lokasi berikutnya
- **Transition Model**: Update posisi, kurangi baterai, hapus dari set
- **Goal Test**: Semua lokasi dikunjungi DAN drone di warehouse
- **Path Cost**: Total jarak atau waktu tempuh

*Step 2:* Analisis karakteristik lingkungan

| Karakteristik | Nilai | Alasan |
|---------------|-------|--------|
| Observable | Fully (GPS) | Posisi diketahui pasti |
| Deterministic | Stochastic | Cuaca mempengaruhi baterai |
| Episodic | Sequential | Pilihan lokasi mempengaruhi sisa perjalanan |
| Static | Dynamic | Lalu lintas udara berubah |
| Discrete | Continuous | Posisi dalam koordinat |
| Agents | Single | Satu drone |

**Jawaban:** 
- Masalah ini mirip Traveling Salesman Problem (TSP)
- Karakteristik: Partially Observable (cuaca), Stochastic, Sequential, Dynamic, Continuous, Single Agent
- Algoritma yang sesuai: A* dengan heuristik MST, atau Simulated Annealing untuk optimisasi

---

#### Solved Problem 16 ⭐⭐

**Soal:** Bandingkan kompleksitas BFS, A*, dan Minimax untuk masalah dengan branching factor b=10 dan depth d=6!

**Penyelesaian:**

*Step 1:* Hitung kompleksitas masing-masing

**BFS:**
- Time: O(b^d) = O(10^6) = 1,000,000 nodes
- Space: O(b^d) = 1,000,000 nodes

**A* (dengan heuristic mendekati h*):**
- Best case: O(d) jika h = h*
- Typical: O(b^(εd)) dimana ε = (h* - h)/h*
- Worst case (h=0): O(b^d) = 1,000,000 nodes

**Minimax:**
- Time: O(b^m) dimana m = max depth
- Untuk d=6: O(10^6) = 1,000,000 nodes
- Dengan Alpha-Beta: O(b^(d/2)) = O(10^3) = 1,000 nodes (best case)

*Step 2:* Perbandingan

| Algoritma | Time Complexity | Space Complexity |
|-----------|-----------------|------------------|
| BFS | 10^6 | 10^6 |
| A* (good h) | 10^2 - 10^4 | Varies |
| Minimax | 10^6 | 10^1 (linear) |
| Alpha-Beta | 10^3 (best) | 10^1 |

**Jawaban:** 
- BFS paling boros (1 juta nodes)
- A* dengan heuristik baik paling efisien untuk pathfinding
- Alpha-Beta optimal untuk game (1000 nodes best case)

---

#### Solved Problem 17 ⭐⭐

**Soal:** Jelaskan mengapa heuristik h = 2 × Manhattan distance TIDAK admissible untuk 8-puzzle!

**Penyelesaian:**

*Step 1:* Review definisi admissible
- h(n) ≤ h*(n) untuk semua n
- h tidak boleh overestimate actual cost

*Step 2:* Analisis h = 2 × Manhattan

Contoh kasus:
```
Current:        Goal:
1 2 3           1 2 3
4 _ 5    →      4 5 6
7 8 6           7 8 _
```

- Manhattan distance untuk tile 5: |1-1| + |2-1| = 1
- Manhattan distance untuk tile 6: |2-2| + |1-2| = 1
- Manhattan distance untuk blank: |1-2| + |1-2| = 2

Total Manhattan = 1 + 1 + 2 = 4
h = 2 × 4 = **8**

*Step 3:* Hitung actual cost (h*)
- Actual moves needed: 5 → geser 1, 6 → geser 1, dst
- h* ≈ 4-5 moves

*Step 4:* Bandingkan
- h = 8 > h* ≈ 5
- h **overestimates** actual cost
- **TIDAK admissible!**

**Jawaban:** h = 2 × Manhattan distance tidak admissible karena menghasilkan estimasi yang lebih besar dari actual cost. Contohnya, untuk konfigurasi tertentu, h=8 padahal h*≈5. A* dengan heuristik ini tidak dijamin menemukan solusi optimal.

---

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Sebuah sistem radar pertahanan udara harus meng-assign 4 radar (R1-R4) untuk memantau 4 sektor (S1-S4). Setiap radar hanya bisa memantau sektor tertentu:
- R1: S1, S2
- R2: S2, S3
- R3: S3, S4
- R4: S1, S4

Formulasikan sebagai CSP dan selesaikan!

**Penyelesaian:**

*Step 1:* Formulasi CSP
- **Variables**: {R1, R2, R3, R4}
- **Domains**:
  - D(R1) = {S1, S2}
  - D(R2) = {S2, S3}
  - D(R3) = {S3, S4}
  - D(R4) = {S1, S4}
- **Constraints**: AllDiff (setiap sektor hanya dipantau satu radar)

*Step 2:* Terapkan AC-3

Arc (R1, R2):
- R1=S1: Ada S2,S3 di D(R2) yang ≠ S1? Yes → Keep S1
- R1=S2: Ada S3 di D(R2) yang ≠ S2? Yes → Keep S2
- D(R1) tidak berubah

Arc (R1, R4):
- R1=S1: Ada S4 di D(R4) yang ≠ S1? Yes → Keep S1
- R1=S2: Ada S1,S4 di D(R4) yang ≠ S2? Yes → Keep S2
- D(R1) tidak berubah

(Lanjutkan untuk semua arc...)

*Step 3:* Backtracking dengan MRV

MRV: Semua domain berukuran 2, pilih R1
- Assign R1 = S1
- Forward checking: Hapus S1 dari D(R4) → D(R4) = {S4}
- MRV memilih R4 (domain size 1)
- Assign R4 = S4
- Forward checking: Hapus S4 dari D(R3) → D(R3) = {S3}
- Assign R3 = S3
- Forward checking: Hapus S3 dari D(R2) → D(R2) = {S2}
- Assign R2 = S2

*Step 4:* Solusi ditemukan

**Jawaban:**
```
R1 → S1
R2 → S2
R3 → S3
R4 → S4
```

Setiap radar memantau sektor yang berbeda, memenuhi semua constraint.

---

### 9.2 Soal Tipe Komputasi

#### Solved Problem 19 ⭐

**Soal:** Hitung jumlah node yang dieksplorasi oleh BFS dan DFS untuk tree dengan branching factor 3 dan depth 4 (goal di level 4)!

**Penyelesaian:**

*Step 1:* Hitung jumlah node per level
```
Level 0: 1 node (root)
Level 1: 3 nodes
Level 2: 9 nodes
Level 3: 27 nodes
Level 4: 81 nodes (termasuk goal)
```

*Step 2:* BFS (worst case - goal di node terakhir)
- BFS memeriksa semua node level by level
- Total = 1 + 3 + 9 + 27 + 81 = **121 nodes**

*Step 3:* DFS (best case - goal di leftmost path)
- DFS langsung ke depth 4 di cabang paling kiri
- Best case: 1 + 1 + 1 + 1 + 1 = **5 nodes**

*Step 3b:* DFS (worst case - goal di rightmost leaf)
- DFS menelusuri semua node
- Worst case: **121 nodes**

**Jawaban:**
- BFS: 121 nodes (selalu)
- DFS: 5 nodes (best) hingga 121 nodes (worst)

---

#### Solved Problem 20 ⭐⭐

**Soal:** Untuk game tree dengan b=3 dan d=4, berapa banyak evaluasi yang dihemat oleh alpha-beta pruning dalam kondisi optimal (perfect ordering)?

**Penyelesaian:**

*Step 1:* Hitung evaluasi tanpa pruning (Minimax)
- Total leaf nodes = b^d = 3^4 = **81 evaluations**

*Step 2:* Hitung evaluasi dengan alpha-beta (perfect ordering)
- Formula: O(b^(d/2)) untuk perfect ordering
- Evaluations ≈ 2 × b^(d/2) - 1
- = 2 × 3^2 - 1 = 2 × 9 - 1 = **17 evaluations**

*Step 3:* Hitung penghematan
- Tanpa pruning: 81
- Dengan pruning: 17
- Penghematan: 81 - 17 = **64 evaluations (79%)**

**Jawaban:** Alpha-beta pruning dengan perfect ordering menghemat sekitar **79%** evaluasi (dari 81 menjadi 17 evaluasi).

---

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Sebuah robot harus bergerak dalam grid 5×5 dari (0,0) ke (4,4). Ada obstacle di (2,2), (2,3), dan (3,2). Hitung f(n) untuk node (2,1) menggunakan A* dengan Manhattan distance!

**Penyelesaian:**

*Step 1:* Visualisasi grid
```
  0 1 2 3 4
0 S . . . .
1 . . N . .
2 . . X X .
3 . . X . .
4 . . . . G

S = Start (0,0)
N = Node (2,1) yang dihitung
X = Obstacle
G = Goal (4,4)
```

*Step 2:* Hitung g(n) - actual cost dari start ke (2,1)
- Path optimal ke (2,1): (0,0) → (1,0) → (2,0) → (2,1)
- g(2,1) = 3 steps

*Step 3:* Hitung h(n) - Manhattan distance ke goal
- h(2,1) = |2-4| + |1-4| = 2 + 3 = 5

*Step 4:* Hitung f(n)
- f(2,1) = g(2,1) + h(2,1) = 3 + 5 = **8**

*Step 5:* Verifikasi admissibility
- Actual optimal path dari (2,1) ke (4,4):
  (2,1) → (1,1) → (1,2) → (1,3) → (1,4) → (2,4) → (3,4) → (4,4)
- Actual cost ≥ 6 (karena harus menghindari obstacle)
- h(2,1) = 5 ≤ 6 ✓ Admissible

**Jawaban:** f(2,1) = g(2,1) + h(2,1) = 3 + 5 = **8**

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Implementasikan hill climbing untuk minimasi f(x) = x² + 2x + 1 dengan step size 0.5, starting dari x=3. Lakukan 4 iterasi!

**Penyelesaian:**

*Step 1:* Analisis fungsi
- f(x) = x² + 2x + 1 = (x+1)²
- Minimum global di x = -1, f(-1) = 0
- Gradient: f'(x) = 2x + 2

*Step 2:* Hill Climbing (steepest descent untuk minimasi)
- Neighbors: x - 0.5 dan x + 0.5
- Pilih neighbor dengan f lebih kecil

**Iterasi 1:** x = 3
- f(3) = 9 + 6 + 1 = 16
- f(2.5) = 6.25 + 5 + 1 = 12.25 ✓ (lebih kecil)
- f(3.5) = 12.25 + 7 + 1 = 20.25
- Move ke x = 2.5

**Iterasi 2:** x = 2.5
- f(2.5) = 12.25
- f(2.0) = 4 + 4 + 1 = 9 ✓
- f(3.0) = 16
- Move ke x = 2.0

**Iterasi 3:** x = 2.0
- f(2.0) = 9
- f(1.5) = 2.25 + 3 + 1 = 6.25 ✓
- f(2.5) = 12.25
- Move ke x = 1.5

**Iterasi 4:** x = 1.5
- f(1.5) = 6.25
- f(1.0) = 1 + 2 + 1 = 4 ✓
- f(2.0) = 9
- Move ke x = 1.0

**Jawaban:**

| Iterasi | x | f(x) | Next x |
|---------|---|------|--------|
| 1 | 3.0 | 16.00 | 2.5 |
| 2 | 2.5 | 12.25 | 2.0 |
| 3 | 2.0 | 9.00 | 1.5 |
| 4 | 1.5 | 6.25 | 1.0 |

Setelah 4 iterasi: x = 1.0, f(x) = 4. (Konvergen menuju x* = -1)

---

## 10. Tips Mengerjakan UTS

### 10.1 Distribusi Topik dalam Soal

| Topik | Perkiraan Bobot | Tipe Soal |
|-------|-----------------|-----------|
| Agen & PEAS (P1) | 15-20% | Analisis, identifikasi |
| Uninformed Search (P2) | 15-20% | Tracing algoritma |
| Informed Search (P3) | 20-25% | Perhitungan A*, desain heuristik |
| Local Search (P4) | 10-15% | Konseptual, iterasi |
| Game Playing (P5) | 15-20% | Minimax tree, alpha-beta |
| CSP (P6) | 15-20% | Formulasi, AC-3, backtracking |

### 10.2 Checklist Persiapan UTS

**Konsep yang harus dikuasai:**
- [ ] Empat pendekatan AI dan perbedaannya
- [ ] Lima jenis agen dan kapan menggunakan masing-masing
- [ ] Enam karakteristik lingkungan
- [ ] Kerangka PEAS
- [ ] Formulasi masalah pencarian
- [ ] BFS, DFS, UCS - kompleksitas dan tracing
- [ ] A* dan Greedy - perbedaan dan tracing
- [ ] Admissibility dan consistency heuristik
- [ ] Hill climbing dan simulated annealing
- [ ] Minimax dan alpha-beta pruning
- [ ] Formulasi dan penyelesaian CSP
- [ ] AC-3 dan backtracking

### 10.3 Kesalahan Umum yang Harus Dihindari

1. **Lupa update visited set** pada BFS/DFS
2. **Menggunakan h(n) saja** di A* (seharusnya f(n) = g(n) + h(n))
3. **Urutan evaluasi salah** pada alpha-beta
4. **Tidak memperhatikan arah arc** pada AC-3
5. **Menghitung Manhattan distance salah** (absolute value!)
6. **Tidak mempropagasi perubahan** setelah assignment di CSP

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Apa perbedaan utama antara BFS dan UCS dalam hal optimalitas?

**Jawaban:** BFS optimal jika semua step cost sama (unit cost). UCS optimal untuk step cost yang berbeda-beda karena menggunakan priority queue berdasarkan g(n).

---

### Problem S2 ⭐⭐
**Soal:** Mengapa alpha-beta pruning tidak mengubah hasil akhir minimax?

**Jawaban:** Alpha-beta hanya memotong cabang yang **tidak mungkin** mempengaruhi keputusan final. Nilai yang dipotong dijamin tidak akan dipilih oleh MAX (jika ≤ α saat ini) atau MIN (jika ≥ β saat ini).

---

### Problem S3 ⭐⭐
**Soal:** Kapan Simulated Annealing lebih baik dari Hill Climbing?

**Jawaban:** SA lebih baik ketika landscape memiliki banyak local optima. SA dapat "meloloskan diri" dari local optima dengan menerima langkah yang lebih buruk dengan probabilitas tertentu, terutama saat temperature tinggi.

---

### Problem S4 ⭐⭐
**Soal:** Jelaskan hubungan antara admissibility dan optimality pada A*!

**Jawaban:** Jika h(n) admissible (tidak pernah overestimate h*(n)), maka A* dijamin menemukan solusi optimal. Ini karena node dengan path cost aktual lebih rendah akan selalu diekspansi sebelum goal dengan path cost lebih tinggi.

---

### Problem S5 ⭐⭐⭐
**Soal:** Sebutkan tiga cara untuk meningkatkan efisiensi backtracking pada CSP!

**Jawaban:**
1. **MRV (Minimum Remaining Values)**: Pilih variabel dengan domain terkecil untuk mendeteksi failure lebih awal
2. **LCV (Least Constraining Value)**: Pilih nilai yang paling sedikit membatasi variabel lain
3. **Forward Checking / AC-3**: Propagasi constraint untuk mengurangi domain lebih awal

---

## Ringkasan

| Pertemuan | Topik Utama | Konsep Kunci | Algoritma |
|-----------|-------------|--------------|-----------|
| **P1** | Pengantar AI | PEAS, 5 jenis agen, 6 karakteristik | - |
| **P2** | Uninformed Search | Completeness, optimality | BFS, DFS, UCS |
| **P3** | Informed Search | Heuristik, admissibility | Greedy, A* |
| **P4** | Local Search | Landscape, local optima | Hill Climbing, SA, GA |
| **P5** | Game Playing | Minimax value, pruning | Minimax, Alpha-Beta |
| **P6** | CSP | Constraint propagation | AC-3, Backtracking |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. Chapter 1-6.
2. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press. Chapter 1-4.
3. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. Chapter 1-6.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
