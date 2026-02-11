# Latihan Pertemuan 03: Pencarian Heuristik (Informed Search)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 03  
**Topik:** Pencarian Heuristik - Informed Search  
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
Apa yang dimaksud dengan fungsi heuristik h(n) dalam konteks pencarian?

A. Biaya aktual dari start ke node n  
B. Biaya aktual dari node n ke goal  
C. Estimasi biaya dari node n ke goal  
D. Total biaya path melalui node n  
E. Kedalaman node n dalam search tree

---

### Soal 2
Algoritma pencarian mana yang menggunakan fungsi evaluasi f(n) = h(n)?

A. Breadth-First Search  
B. Depth-First Search  
C. Uniform Cost Search  
D. Greedy Best-First Search  
E. A* Search

---

### Soal 3
Fungsi evaluasi f(n) = g(n) + h(n) digunakan oleh algoritma:

A. BFS  
B. DFS  
C. UCS  
D. Greedy Best-First Search  
E. A*

---

### Soal 4
Jika h(n) = 0 untuk semua node n, algoritma A* akan berperilaku seperti:

A. BFS  
B. DFS  
C. UCS  
D. Greedy Best-First Search  
E. Random Search

---

### Soal 5
Heuristik yang tidak pernah meng-overestimate biaya sebenarnya disebut:

A. Consistent  
B. Dominant  
C. Admissible  
D. Optimal  
E. Complete

---

### Soal 6
Manakah pernyataan yang BENAR tentang Greedy Best-First Search?

A. Selalu menemukan solusi optimal  
B. Memiliki kompleksitas ruang O(bd)  
C. Menggunakan g(n) untuk evaluasi  
D. Bisa terjebak di infinite loop pada graph dengan cycle  
E. Menjamin kelengkapan (completeness)

---

### Soal 7
Straight-line distance adalah heuristik admissible untuk pencarian rute karena:

A. Selalu sama dengan jarak jalan sebenarnya  
B. Selalu lebih besar dari jarak jalan sebenarnya  
C. Selalu lebih kecil atau sama dengan jarak jalan sebenarnya  
D. Tidak bergantung pada lokasi goal  
E. Mudah dihitung

---

### Soal 8
Dalam 8-puzzle, Manhattan distance dihitung dengan cara:

A. Menghitung jumlah tile yang salah posisi  
B. Menghitung jarak Euclidean setiap tile ke posisi goalnya  
C. Menghitung jumlah langkah horizontal dan vertikal setiap tile ke posisi goalnya  
D. Menghitung jumlah tile yang berdekatan dengan posisi benar  
E. Menghitung kedalaman state dalam search tree

---

### Soal 9
Jika h₁(n) = 5 dan h₂(n) = 3 untuk suatu state n, dan keduanya admissible, maka kombinasi heuristik terbaik adalah:

A. h(n) = h₁(n) + h₂(n) = 8  
B. h(n) = h₁(n) × h₂(n) = 15  
C. h(n) = min(h₁(n), h₂(n)) = 3  
D. h(n) = max(h₁(n), h₂(n)) = 5  
E. h(n) = (h₁(n) + h₂(n)) / 2 = 4

---

### Soal 10
Kondisi consistency (monotonicity) pada heuristik menyatakan bahwa:

A. h(n) = h*(n) untuk semua n  
B. h(n) ≤ c(n, a, n') + h(n') untuk semua n dan successor n'  
C. h(n) > 0 untuk semua n kecuali goal  
D. h(n) selalu berkurang sepanjang path  
E. h(n) = 0 hanya untuk goal state

---

### Soal 11
Manakah yang merupakan implikasi dari heuristik yang consistent?

A. A* tidak optimal  
B. f(n) bisa berkurang sepanjang path  
C. Node yang sudah diekspansi tidak perlu diekspansi lagi  
D. Kompleksitas ruang menjadi O(d)  
E. Greedy BFS menjadi complete

---

### Soal 12
Teknik "relaxed problem" digunakan untuk:

A. Mengurangi kompleksitas waktu A*  
B. Merancang fungsi heuristik yang admissible  
C. Menghilangkan kebutuhan akan heuristik  
D. Mengubah A* menjadi UCS  
E. Mempercepat konvergensi Greedy BFS

---

### Soal 13
Untuk 8-puzzle, relaxation "tile bisa berpindah ke kotak manapun" menghasilkan heuristik:

A. Manhattan distance  
B. Euclidean distance  
C. Misplaced tiles  
D. Pattern database  
E. Zero heuristic

---

### Soal 14
IDA* (Iterative Deepening A*) memiliki keunggulan dibanding A* dalam hal:

A. Selalu lebih cepat  
B. Kompleksitas ruang yang linear O(bd)  
C. Tidak memerlukan heuristik  
D. Dapat menangani graf dengan cycle  
E. Menghasilkan solusi yang lebih optimal

---

### Soal 15
Jika A* dengan heuristik h₂ mengekspansi lebih sedikit node dibanding A* dengan h₁, maka:

A. h₁ mendominasi h₂  
B. h₂ mendominasi h₁  
C. h₁ tidak admissible  
D. h₂ tidak admissible  
E. Keduanya identik

---

### Soal 16
Pada pencarian dari Arad ke Bucharest menggunakan A* dengan heuristik SLD, node pertama yang diekspansi setelah Arad adalah:

A. Zerind (h=374)  
B. Timisoara (h=329)  
C. Sibiu (h=253)  
D. Oradea (h=380)  
E. Fagaras (h=176)

---

### Soal 17
Effective branching factor b* digunakan untuk mengukur:

A. Jumlah successor rata-rata per node  
B. Efektivitas heuristik dalam mengurangi pencarian  
C. Kedalaman solusi optimal  
D. Kompleksitas waktu worst case  
E. Jumlah goal state yang mungkin

---

### Soal 18
Manakah pernyataan yang SALAH tentang algoritma A*?

A. A* optimal dengan heuristik admissible  
B. A* complete pada finite state space  
C. A* memiliki kompleksitas ruang eksponensial  
D. A* selalu lebih cepat dari UCS  
E. A* menggunakan priority queue untuk frontier

---

### Soal 19
Dalam konteks 8-puzzle, hubungan antara Manhattan distance (h₂) dan misplaced tiles (h₁) adalah:

A. h₁ mendominasi h₂  
B. h₂ mendominasi h₁  
C. h₁ = h₂ untuk semua state  
D. Tidak ada hubungan dominance  
E. h₁ + h₂ adalah heuristik terbaik

---

### Soal 20
SMA* (Simplified Memory-Bounded A*) berbeda dari A* dalam hal:

A. Tidak memerlukan heuristik  
B. Tidak optimal  
C. Membuang node dengan f tertinggi ketika memori penuh  
D. Menggunakan f(n) = h(n) saja  
E. Hanya bekerja pada tree search

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara uninformed search dan informed search! Berikan satu contoh algoritma untuk masing-masing kategori!

---

### Soal 2 ⭐
Apa yang dimaksud dengan heuristik? Sebutkan tiga properti yang harus dimiliki fungsi heuristik yang baik!

---

### Soal 3 ⭐
Hitung Manhattan distance untuk state 8-puzzle berikut menuju goal state standar [1,2,3,4,5,6,7,8,0]:

```
State: [1, 3, 2, 4, 6, 5, 7, 8, 0]

Grid visualization:
┌───┬───┬───┐
│ 1 │ 3 │ 2 │
├───┼───┼───┤
│ 4 │ 6 │ 5 │
├───┼───┼───┤
│ 7 │ 8 │   │
└───┴───┴───┘
```

---

### Soal 4 ⭐
Jelaskan mengapa Greedy Best-First Search tidak optimal! Berikan contoh sederhana!

---

### Soal 5 ⭐⭐
Trace algoritma A* untuk mencari path dari S ke G pada graf berikut. Tunjukkan urutan ekspansi node dan f-value masing-masing!

```
    S --2-- A --3-- G
    |       |
    4       1
    |       |
    B --2-- C

h(S)=5, h(A)=2, h(B)=4, h(C)=1, h(G)=0
```

---

### Soal 6 ⭐⭐
Jelaskan perbedaan antara admissibility dan consistency pada heuristik! Apakah setiap heuristik consistent juga admissible? Jelaskan!

---

### Soal 7 ⭐⭐
Buktikan bahwa straight-line distance adalah heuristik admissible untuk masalah pencarian rute!

---

### Soal 8 ⭐⭐
Jelaskan teknik "relaxed problem" untuk merancang heuristik! Berikan contoh penerapannya pada 8-puzzle!

---

### Soal 9 ⭐⭐
Bandingkan jumlah node yang diekspansi oleh UCS dan A* untuk graf berikut dari S ke G:

```
    S --1-- A --1-- B --1-- G
    |                       |
    5-----------------------+

h(S)=3, h(A)=2, h(B)=1, h(G)=0
```

---

### Soal 10 ⭐⭐
Jelaskan mengapa A* dengan graph search membutuhkan heuristik consistent, bukan hanya admissible!

---

### Soal 11 ⭐⭐⭐
Buktikan bahwa Manhattan distance adalah consistent untuk 8-puzzle!

---

### Soal 12 ⭐⭐⭐
Jika h₁ dan h₂ keduanya admissible, buktikan bahwa h(n) = max(h₁(n), h₂(n)) juga admissible dan mendominasi keduanya!

---

### Soal 13 ⭐⭐⭐
Berikan contoh heuristik yang admissible tetapi tidak consistent! Tunjukkan bahwa heuristik tersebut melanggar kondisi consistency!

---

### Soal 14 ⭐⭐⭐
Jelaskan algoritma IDA* dan bagaimana ia mengatasi masalah memori pada A*! Apa trade-off yang terjadi?

---

### Soal 15 ⭐⭐⭐
Desain fungsi heuristik untuk robot yang harus bernavigasi dalam grid dengan obstacle dan area berbahaya (danger zones). Jelaskan komponen-komponen heuristik dan bagaimana menjamin admissibility!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Navigasi Kapal Selam Otonom

**Latar Belakang:**

TNI Angkatan Laut mengembangkan sistem navigasi otonom untuk kapal selam mini (Autonomous Underwater Vehicle/AUV) yang bertugas:
1. Patroli di perairan strategis
2. Surveilans bawah laut
3. Pemetaan dasar laut

**Lingkungan Operasi:**
- Perairan dengan kedalaman bervariasi (50-500 meter)
- Arus laut yang berubah-ubah
- Zona larangan (area berbahaya, instalasi bawah laut negara lain)
- Komunikasi terbatas (hanya saat di permukaan)
- Baterai terbatas dengan endurance 72 jam

**Grid Operasi:**
Perairan dibagi menjadi grid 20x20 dengan setiap sel berukuran 1 km × 1 km. Setiap sel memiliki atribut:
- Kedalaman (mempengaruhi konsumsi energi)
- Kekuatan arus (mempengaruhi waktu tempuh)
- Tingkat deteksi (probabilitas terdeteksi sonar musuh)
- Status: navigable, restricted, atau forbidden

**Misi:**
AUV harus bergerak dari Pos Pangkalan (0, 0) ke Titik Surveilans (15, 18) dengan:
- Meminimalkan waktu tempuh
- Menghindari zona larangan
- Meminimalkan probabilitas deteksi
- Menjaga kecukupan baterai untuk perjalanan pulang

**Data Grid (Sampel):**
```
Zona Larangan: (5,5) sampai (8,8), (12,3) sampai (14,6)
Arus Kuat: (10,10) sampai (13,15) - penambahan waktu 50%
High Detection Zone: (8,12) sampai (11,16) - deteksi 80%
Normal Zone: deteksi 20%
```

**Pertanyaan:**

**1a.** Formulasikan masalah ini sebagai search problem! Definisikan state, action, initial state, goal state, dan cost function! (15 poin)

**1b.** Desain fungsi heuristik yang mempertimbangkan jarak, deteksi, dan konsumsi energi! Jelaskan bagaimana menjamin admissibility! (20 poin)

**1c.** Trace algoritma A* untuk 5 langkah pertama dari posisi (0,0) dengan asumsi grid sederhana 5x5. Tunjukkan f, g, h untuk setiap node yang diekspansi! (15 poin)

**1d.** Bandingkan pendekatan Greedy BFS vs A* untuk misi ini! Identifikasi skenario dimana masing-masing pendekatan lebih menguntungkan! (10 poin)

**1e.** Bagaimana Anda memodifikasi algoritma untuk menangani ketidakpastian arus laut yang berubah? Jelaskan pendekatan yang mungkin! (10 poin)

---

### Studi Kasus 2: Perencanaan Jalur Evakuasi Darurat Pangkalan Militer

**Latar Belakang:**

Sebuah pangkalan militer strategis membutuhkan sistem perencanaan jalur evakuasi otomatis untuk berbagai skenario darurat:
1. Serangan udara
2. Kebocoran bahan berbahaya
3. Kebakaran
4. Intrusi musuh

**Layout Pangkalan:**
- Luas: 50x50 grid (setiap sel = 10m × 10m)
- Terdapat 8 gedung utama (barak, gudang amunisi, hanggar, pusat komando, dll.)
- 3 titik evakuasi (shelter) dengan kapasitas berbeda
- Beberapa koridor dan area terbuka

**Tantangan:**
- Beberapa jalur mungkin terblokir tergantung jenis darurat
- Personel dari berbagai lokasi harus dievakuasi bersamaan
- Jalur tidak boleh melewati area terkena dampak
- Waktu adalah kritis

**Skenario Spesifik - Serangan Udara:**
- Area terdampak: radius 100m dari titik serangan
- Shelter yang tersedia: Bunker A (kapasitas 100), Bunker B (kapasitas 150), Bunker C (kapasitas 200)
- Titik serangan: koordinat (25, 30)
- Lokasi personel: tersebar di 5 gedung berbeda

**Data Personel:**
```
Gedung 1 (Barak): koordinat (10, 10), 80 personel
Gedung 2 (Kantor): koordinat (40, 15), 30 personel
Gedung 3 (Hanggar): koordinat (35, 40), 25 personel
Gedung 4 (Gudang): koordinat (15, 35), 15 personel
Gedung 5 (Mess): koordinat (20, 20), 50 personel
```

**Lokasi Shelter:**
```
Bunker A: koordinat (5, 5), kapasitas 100
Bunker B: koordinat (45, 5), kapasitas 150
Bunker C: koordinat (25, 48), kapasitas 200
```

**Pertanyaan:**

**2a.** Formulasikan masalah evakuasi sebagai multi-agent pathfinding problem! Jelaskan bagaimana memodelkan state, action, dan goal untuk semua kelompok personel! (15 poin)

**2b.** Desain fungsi heuristik untuk meminimalkan total waktu evakuasi semua personel! Pertimbangkan jarak ke shelter terdekat dan kapasitas shelter! (15 poin)

**2c.** Jelaskan bagaimana menangani constraint bahwa jalur tidak boleh melewati area terdampak (radius 100m dari titik serangan)! Modifikasi apa yang diperlukan pada algoritma A*? (15 poin)

**2d.** Implementasikan pseudocode untuk sistem evakuasi yang mengalokasikan personel ke shelter berdasarkan kapasitas dan jarak! Gunakan A* untuk setiap kelompok! (20 poin)

**2e.** Analisis trade-off antara optimalitas global (total waktu minimum) vs fairness (tidak ada kelompok yang terlalu lama). Bagaimana memodifikasi utility function untuk menyeimbangkan keduanya? (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | Heuristik h(n) adalah *estimasi* biaya dari node n ke goal, bukan biaya aktual. Biaya aktual disimbolkan h*(n). |
| 2 | **D** | Greedy Best-First Search menggunakan f(n) = h(n), hanya mempertimbangkan estimasi jarak ke goal tanpa biaya path. |
| 3 | **E** | A* menggunakan f(n) = g(n) + h(n), kombinasi biaya aktual dari start dan estimasi ke goal. |
| 4 | **C** | Jika h(n) = 0, maka f(n) = g(n) + 0 = g(n), yang sama dengan fungsi evaluasi UCS. |
| 5 | **C** | Heuristik admissible adalah heuristik yang tidak pernah overestimate, yaitu h(n) ≤ h*(n). |
| 6 | **D** | Greedy BFS tidak complete karena bisa terjebak di infinite loop pada graph dengan cycle jika tidak menggunakan explored set yang proper. |
| 7 | **C** | Jarak garis lurus selalu ≤ jarak melalui jalan karena garis lurus adalah path terpendek dalam ruang Euclidean. |
| 8 | **C** | Manhattan distance = Σ|xi - xgoal| + |yi - ygoal|, jumlah jarak horizontal dan vertikal. |
| 9 | **D** | Untuk kombinasi heuristik admissible, h(n) = max(h₁, h₂) memberikan heuristik terbaik yang tetap admissible. |
| 10 | **B** | Kondisi consistency: h(n) ≤ c(n, a, n') + h(n'), ketidaksamaan segitiga. |
| 11 | **C** | Dengan heuristik consistent, f(n) monoton non-decreasing, sehingga node yang sudah diekspansi pasti sudah optimal. |
| 12 | **B** | Relaxed problem digunakan untuk merancang heuristik admissible dengan menghilangkan constraint dari masalah asli. |
| 13 | **C** | Jika tile bisa berpindah ke mana saja, setiap tile yang salah posisi memerlukan tepat 1 langkah → misplaced tiles. |
| 14 | **B** | IDA* menggunakan DFS dengan f-limit, sehingga kompleksitas ruang menjadi O(bd), linear dengan kedalaman. |
| 15 | **B** | Jika A* dengan h₂ lebih efisien, berarti h₂ lebih informatif (nilai lebih tinggi), sehingga h₂ mendominasi h₁. |
| 16 | **C** | f(Sibiu) = g + h = 140 + 253 = 393 adalah yang terkecil setelah Arad diekspansi. |
| 17 | **B** | Effective branching factor b* mengukur seberapa efektif heuristik dalam memangkas search tree. |
| 18 | **D** | A* tidak selalu lebih cepat dari UCS. Dengan heuristik buruk, A* bisa sama lambat atau lebih lambat. |
| 19 | **B** | Manhattan distance selalu ≥ misplaced tiles karena setiap tile yang salah posisi berkontribusi minimal 1 ke Manhattan (dan bisa lebih). |
| 20 | **C** | SMA* membuang node dengan f tertinggi ketika memori penuh untuk tetap bisa melanjutkan pencarian. |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Perbedaan Uninformed dan Informed Search:**

| Aspek | Uninformed Search | Informed Search |
|-------|-------------------|-----------------|
| Pengetahuan | Tidak menggunakan informasi domain | Menggunakan heuristik/pengetahuan domain |
| Arah pencarian | "Buta", tidak terarah | Terarah ke goal |
| Efisiensi | Umumnya kurang efisien | Lebih efisien dengan heuristik baik |

**Contoh:**
- **Uninformed:** BFS, DFS, UCS
- **Informed:** Greedy Best-First Search, A*

---

#### Jawaban Soal 2 ⭐

**Definisi Heuristik:**
Heuristik h(n) adalah fungsi yang memberikan estimasi biaya dari node n ke goal terdekat.

**Tiga Properti Heuristik yang Baik:**

1. **Non-negative:** h(n) ≥ 0 untuk semua node n
2. **Goal-aware:** h(goal) = 0
3. **Admissible:** h(n) ≤ h*(n), tidak pernah overestimate

Properti tambahan yang diinginkan:
- **Consistent:** h(n) ≤ c(n,a,n') + h(n')
- **Informatif:** Nilai h(n) setinggi mungkin sambil tetap admissible

---

#### Jawaban Soal 3 ⭐

**State:** [1, 3, 2, 4, 6, 5, 7, 8, 0]

```
Current:               Goal:
┌───┬───┬───┐         ┌───┬───┬───┐
│ 1 │ 3 │ 2 │         │ 1 │ 2 │ 3 │
├───┼───┼───┤         ├───┼───┼───┤
│ 4 │ 6 │ 5 │         │ 4 │ 5 │ 6 │
├───┼───┼───┤         ├───┼───┼───┤
│ 7 │ 8 │   │         │ 7 │ 8 │   │
└───┴───┴───┘         └───┴───┴───┘
```

**Perhitungan Manhattan Distance:**

| Tile | Current (row, col) | Goal (row, col) | Manhattan |
|------|-------------------|-----------------|-----------|
| 1 | (0, 0) | (0, 0) | 0 |
| 2 | (0, 2) | (0, 1) | 1 |
| 3 | (0, 1) | (0, 2) | 1 |
| 4 | (1, 0) | (1, 0) | 0 |
| 5 | (1, 2) | (1, 1) | 1 |
| 6 | (1, 1) | (1, 2) | 1 |
| 7 | (2, 0) | (2, 0) | 0 |
| 8 | (2, 1) | (2, 1) | 0 |

**h_Manhattan = 0 + 1 + 1 + 0 + 1 + 1 + 0 + 0 = 4**

---

#### Jawaban Soal 4 ⭐

**Mengapa Greedy BFS Tidak Optimal:**

Greedy BFS hanya mempertimbangkan h(n) tanpa g(n), sehingga mengabaikan biaya path yang sudah ditempuh.

**Contoh:**
```
    A --1-- B --10-- G
     \            /
      --5--------/

h(A)=6, h(B)=1, h(G)=0
```

**Trace Greedy:**
1. Expand A: neighbors B(h=1), G(h=0 via langsung)
2. Jika ada edge langsung A-G dengan cost 5:
   - Greedy pilih edge dengan h terkecil
   - A → B → G = 1 + 10 = 11
   - A → G langsung = 5 (optimal)

Greedy memilih B karena h(B)=1 < estimasi langsung ke G, padahal path langsung lebih murah.

---

#### Jawaban Soal 5 ⭐⭐

**Graf:**
```
    S --2-- A --3-- G
    |       |
    4       1
    |       |
    B --2-- C

h(S)=5, h(A)=2, h(B)=4, h(C)=1, h(G)=0
```

**Trace A*:**

| Step | Node | g | h | f | Frontier (sorted by f) |
|------|------|---|---|---|------------------------|
| 1 | S | 0 | 5 | 5 | {S(5)} |
| 2 | Expand S | - | - | - | {A(2+2=4), B(4+4=8)} |
| 3 | Expand A | 2 | 2 | 4 | {B(8), G(2+3+0=5), C(2+1+1=4)} |
| 4 | Expand C | 3 | 1 | 4 | {B(8), G(5)} |
| 5 | Expand G | 5 | 0 | 5 | GOAL! |

**Path optimal: S → A → G dengan cost 5**

---

#### Jawaban Soal 6 ⭐⭐

**Admissibility:**
- h(n) ≤ h*(n) untuk semua n
- Tidak pernah overestimate biaya sebenarnya

**Consistency:**
- h(n) ≤ c(n, a, n') + h(n') untuk semua n dan successor n'
- Ketidaksamaan segitiga

**Hubungan:**
**Ya, setiap heuristik consistent pasti admissible.**

**Bukti:**
Misalkan h consistent. Untuk path n₀ → n₁ → ... → nₖ = goal:
- h(n₀) ≤ c(n₀,n₁) + h(n₁)
- h(n₁) ≤ c(n₁,n₂) + h(n₂)
- ...
- h(nₖ₋₁) ≤ c(nₖ₋₁,nₖ) + h(nₖ) = c(nₖ₋₁,nₖ) + 0

Jumlahkan: h(n₀) ≤ Σc(nᵢ,nᵢ₊₁) = h*(n₀)

Jadi h admissible.

**Catatan:** Sebaliknya tidak berlaku (admissible belum tentu consistent).

---

#### Jawaban Soal 7 ⭐⭐

**Bukti SLD Admissible:**

**Teorema Geometri:** Jarak terpendek antara dua titik dalam ruang Euclidean adalah garis lurus.

**Aplikasi pada pencarian rute:**
- h_SLD(n) = jarak garis lurus dari n ke goal
- h*(n) = jarak jalan terpendek dari n ke goal

Karena jalan apapun dari n ke goal memiliki panjang ≥ jarak garis lurus:
$$h_{SLD}(n) \leq h^*(n)$$

untuk semua n.

**Kesimpulan:** SLD tidak pernah overestimate, sehingga admissible. ∎

---

#### Jawaban Soal 8 ⭐⭐

**Teknik Relaxed Problem:**

Relaxed problem adalah versi masalah dengan beberapa constraint dihilangkan. Solusi optimal dari relaxed problem selalu ≤ solusi masalah asli, sehingga menjadi heuristik admissible.

**Contoh pada 8-Puzzle:**

**Constraint asli:**
1. Tile hanya bisa ke kotak kosong
2. Kotak kosong harus adjacent
3. Satu tile per gerakan

**Relaxation 1: Hilangkan semua constraint**
- Tile bisa teleport ke mana saja
- Heuristik: **Misplaced tiles** (1 langkah per tile salah)

**Relaxation 2: Hilangkan constraint 1**
- Tile bisa ke kotak adjacent manapun (meski terisi)
- Heuristik: **Manhattan distance** (jumlah jarak minimal per tile)

**Relaxation 3: Tidak ada relaxation**
- Heuristik: h* (biaya sebenarnya)

Manhattan lebih informatif dari misplaced tiles karena relaxation lebih ketat.

---

#### Jawaban Soal 9 ⭐⭐

**Graf:**
```
    S --1-- A --1-- B --1-- G
    |                       |
    5-----------------------+
```

**UCS (f = g):**

| Step | Expand | g | Frontier |
|------|--------|---|----------|
| 1 | S | 0 | {A(1), G(5)} |
| 2 | A | 1 | {B(2), G(5)} |
| 3 | B | 2 | {G(3), G(5)} |
| 4 | G | 3 | GOAL |

**UCS: 4 nodes expanded (S, A, B, G)**

**A* (f = g + h):**

| Step | Expand | g | h | f | Frontier |
|------|--------|---|---|---|----------|
| 1 | S | 0 | 3 | 3 | {A(1+2=3), G(5+0=5)} |
| 2 | A | 1 | 2 | 3 | {B(2+1=3), G(5)} |
| 3 | B | 2 | 1 | 3 | {G(3+0=3), G(5)} |
| 4 | G | 3 | 0 | 3 | GOAL |

**A*: 4 nodes expanded (S, A, B, G)**

Dalam kasus ini sama karena heuristik exact (h = h*) untuk path atas.

Jika ada lebih banyak jalur alternatif, A* akan lebih efisien.

---

#### Jawaban Soal 10 ⭐⭐

**Mengapa Graph Search A* Butuh Consistent:**

Pada graph search, setiap node hanya diekspansi sekali (disimpan di explored set). Jika heuristik tidak consistent:

1. Node n mungkin diekspansi dengan g(n) yang bukan optimal
2. Path lebih baik ke n ditemukan kemudian
3. Tapi n sudah di explored, tidak akan diproses ulang
4. Solusi mungkin suboptimal

**Dengan heuristik consistent:**
- f(n) non-decreasing sepanjang path
- Ketika node diekspansi, dijamin sudah dengan g optimal
- Tidak perlu re-expand

**Solusi untuk non-consistent admissible:**
- Gunakan tree search (re-expansion allowed)
- Atau modifikasi graph search untuk allow re-expansion

---

#### Jawaban Soal 11 ⭐⭐⭐

**Bukti Manhattan Distance Consistent untuk 8-Puzzle:**

**Kondisi consistency:** h(n) ≤ c(n, a, n') + h(n')

**Pada 8-puzzle:**
- Setiap aksi: geser 1 tile ke posisi kosong
- c(n, a, n') = 1 untuk semua aksi

**Analisis:**
Ketika satu tile digeser:
- Tile tersebut bergerak 1 langkah (horizontal atau vertikal)
- Manhattan distance tile itu berubah ±1 atau tetap

**Kasus 1:** Tile mendekat ke goal
- h(n') = h(n) - 1
- h(n) = h(n') + 1 = c + h(n') ✓

**Kasus 2:** Tile menjauh dari goal
- h(n') = h(n) + 1
- h(n) = h(n') - 1 < c + h(n') ✓

**Kasus 3:** Tile tidak terpengaruh
- h(n') = h(n)
- h(n) ≤ 1 + h(n') = c + h(n') ✓

Semua kasus terpenuhi, jadi Manhattan distance consistent. ∎

---

#### Jawaban Soal 12 ⭐⭐⭐

**Buktikan h(n) = max(h₁(n), h₂(n)) admissible dan mendominasi:**

**Bagian 1: Admissibility**

Karena h₁ dan h₂ admissible:
- h₁(n) ≤ h*(n) untuk semua n
- h₂(n) ≤ h*(n) untuk semua n

Maka:
- max(h₁(n), h₂(n)) ≤ h*(n) untuk semua n

Karena max dari dua nilai yang ≤ X juga ≤ X.

**h(n) = max(h₁, h₂) admissible** ✓

**Bagian 2: Dominance**

Untuk semua n:
- max(h₁(n), h₂(n)) ≥ h₁(n) (by definition of max)
- max(h₁(n), h₂(n)) ≥ h₂(n) (by definition of max)

**h mendominasi h₁ dan h₂** ✓

---

#### Jawaban Soal 13 ⭐⭐⭐

**Contoh Admissible tapi Tidak Consistent:**

**Graf:**
```
A --1-- B --1-- C (Goal)
```

**Heuristik:**
- h(A) = 2 (h* = 2, admissible ✓)
- h(B) = 0 (h* = 1, admissible karena 0 ≤ 1 ✓)
- h(C) = 0 (goal, admissible ✓)

**Cek Consistency dari A ke B:**
- h(A) ≤ c(A,B) + h(B)?
- 2 ≤ 1 + 0?
- 2 ≤ 1? ✗

**Heuristik ini admissible tapi tidak consistent** karena melanggar ketidaksamaan segitiga dari A ke B.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Algoritma IDA*:**

```
function IDA*(problem, h):
    limit ← h(initial)
    
    loop:
        result, new_limit ← DFS_Contour(initial, 0, limit)
        if result = FOUND: return solution
        if new_limit = ∞: return failure
        limit ← new_limit

function DFS_Contour(node, g, limit):
    f ← g + h(node)
    if f > limit: return (CUTOFF, f)
    if goal(node): return (FOUND, node)
    
    min_exceeded ← ∞
    for each successor s with cost c:
        result, new_f ← DFS_Contour(s, g+c, limit)
        if result = FOUND: return (FOUND, result)
        min_exceeded ← min(min_exceeded, new_f)
    
    return (CUTOFF, min_exceeded)
```

**Cara Mengatasi Masalah Memori:**
- Menggunakan DFS (bukan BFS/best-first)
- Tidak menyimpan seluruh frontier
- Space complexity: O(bd) - linear!

**Trade-off:**
- (+) Memori sangat efisien
- (-) Nodes di-explore berulang kali
- (-) Lebih banyak iterasi dibanding A*
- Trade-off: Ruang vs Waktu

---

#### Jawaban Soal 15 ⭐⭐⭐

**Heuristik untuk Robot Navigation dengan Danger Zones:**

**Komponen Heuristik:**

```cpp
double heuristic(State n, State goal, Grid& grid) {
    // 1. Komponen jarak (admissible baseline)
    double dist = euclideanDistance(n, goal);
    
    // 2. Komponen obstacle (underestimate detour)
    double obstaclePenalty = 0;
    if (pathBlockedByObstacle(n, goal)) {
        obstaclePenalty = estimateDetour(n, goal) * 0.5; // underestimate
    }
    
    // 3. Komponen danger (optional, bisa dimasukkan ke cost)
    // Untuk menjaga admissibility, JANGAN tambahkan penalty
    // ke heuristik, tapi ke actual cost
    
    return dist + obstaclePenalty;
}
```

**Menjamin Admissibility:**

1. **Euclidean distance** selalu ≤ path aktual (admissible)
2. **Obstacle penalty** harus di-underestimate:
   - Estimasi detour × faktor < 1
   - Atau tidak include sama sekali
3. **Danger zones** dihandle di cost function, bukan heuristic

**Cost Function:**
```cpp
double cost(State from, State to, Grid& grid) {
    double baseCost = distance(from, to);
    
    if (isDangerZone(to)) {
        baseCost *= DANGER_MULTIPLIER; // e.g., 2.0
    }
    
    return baseCost;
}
```

Dengan pemisahan ini, A* akan menghindari danger zones karena cost lebih tinggi, tapi heuristik tetap admissible.

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Navigasi Kapal Selam Otonom

**1a. Formulasi Search Problem (15 poin)**

**State:**
```
State = (x, y, depth, battery_remaining, detection_status)
```
Simplified: State = (x, y) dengan atribut grid

**Initial State:** (0, 0) - Pos Pangkalan

**Goal State:** (15, 18) - Titik Surveilans

**Actions:** 
- Move ke 8 arah (N, NE, E, SE, S, SW, W, NW)
- Setiap move: cek navigability

**Cost Function:**
```
cost(s, s') = base_distance 
            + current_penalty(s') 
            + depth_penalty(s') 
            + detection_risk(s')

dimana:
- base_distance = 1 (atau 1.414 untuk diagonal)
- current_penalty = 0.5 jika di zona arus kuat
- depth_penalty = 0.1 × |depth_change|
- detection_risk = 0.8 × detection_prob(s')
```

**1b. Desain Fungsi Heuristik (20 poin)**

```cpp
double heuristic(State s, State goal, Grid& grid) {
    // Komponen 1: Jarak Euclidean (admissible)
    double dist = sqrt(pow(s.x - goal.x, 2) + pow(s.y - goal.y, 2));
    
    // Komponen 2: Minimum detection exposure (underestimate)
    // Estimasi: jarak × minimum detection rate
    double minDetection = dist * MIN_DETECTION_RATE; // 0.2
    
    // Komponen 3: Minimum energy (underestimate)
    // Asumsi: pergerakan di kedalaman optimal
    double minEnergy = dist * BASE_ENERGY_RATE;
    
    // Kombinasi dengan weights konservatif
    return dist + 0.3 * minDetection + 0.2 * minEnergy;
}
```

**Menjamin Admissibility:**
1. Euclidean distance ≤ actual path length ✓
2. Gunakan MINIMUM detection rate untuk estimasi ✓
3. Gunakan MINIMUM energy rate ✓
4. Semua komponen di-underestimate ✓

**1c. Trace A* 5 Langkah Pertama (15 poin)**

Asumsi grid 5x5 sederhana, goal di (4,4):

| Step | Expand | g | h | f | Frontier (top 3) |
|------|--------|---|---|---|------------------|
| 1 | (0,0) | 0 | 5.66 | 5.66 | {(0,1), (1,0), (1,1)} |
| 2 | (1,1) | 1.41 | 4.24 | 5.65 | {(2,2), (1,2), (2,1)} |
| 3 | (2,2) | 2.83 | 2.83 | 5.66 | {(3,3), (2,3), (3,2)} |
| 4 | (3,3) | 4.24 | 1.41 | 5.65 | {(4,4), (3,4), (4,3)} |
| 5 | (4,4) | 5.66 | 0 | 5.66 | GOAL! |

**1d. Perbandingan Greedy vs A* (10 poin)**

| Aspek | Greedy BFS | A* |
|-------|------------|-----|
| Kecepatan | Lebih cepat | Lebih lambat |
| Optimalitas | Tidak optimal | Optimal |
| Memori | Sama-sama eksponensial | Sama |

**Kapan Greedy lebih baik:**
- Waktu sangat kritis (darurat)
- Heuristik sangat akurat
- Suboptimal acceptable

**Kapan A* lebih baik:**
- Baterai terbatas (perlu path optimal)
- Misi jangka panjang
- Risiko deteksi harus minimal

**1e. Menangani Ketidakpastian Arus (10 poin)**

**Pendekatan 1: Replanning**
- Jalankan A* dengan informasi terkini
- Jika arus berubah signifikan, replan dari posisi saat ini

**Pendekatan 2: Stochastic A***
- Model arus sebagai distribusi probabilitas
- Gunakan expected cost dalam evaluasi

**Pendekatan 3: Online Planning**
- Rencanakan hanya beberapa langkah ke depan
- Update plan secara kontinu berdasarkan sensor

---

#### Studi Kasus 2: Perencanaan Jalur Evakuasi Darurat

**2a. Formulasi Multi-Agent Pathfinding (15 poin)**

**State untuk sistem keseluruhan:**
```
GlobalState = {
    groups: [(pos₁, size₁, assigned_shelter₁), 
             (pos₂, size₂, assigned_shelter₂), 
             ...]
    time: t
}
```

**State per kelompok:**
```
GroupState = (position, remaining_personnel, target_shelter)
```

**Actions:**
- Move ke cell adjacent (8 arah)
- Constraint: tidak boleh ke area terdampak

**Goal:**
- Semua kelompok mencapai shelter yang ditugaskan
- Total personel ≤ kapasitas shelter

**2b. Fungsi Heuristik (15 poin)**

```cpp
double heuristicGroup(Group g, Shelter target) {
    // Manhattan distance ke shelter (admissible)
    return manhattanDistance(g.position, target.position);
}

double heuristicGlobal(vector<Group>& groups, vector<Shelter>& shelters) {
    double totalH = 0;
    for (auto& g : groups) {
        // Gunakan jarak ke shelter yang dialokasikan
        totalH += heuristicGroup(g, g.assigned_shelter);
    }
    return totalH;
}
```

**Alokasi shelter awal (greedy):**
```cpp
void allocateShelters(vector<Group>& groups, vector<Shelter>& shelters) {
    // Sort groups by size (largest first)
    sort(groups.begin(), groups.end(), bySize);
    
    for (auto& g : groups) {
        // Assign ke shelter terdekat dengan kapasitas cukup
        Shelter* best = nullptr;
        double minDist = INF;
        
        for (auto& s : shelters) {
            if (s.remaining_capacity >= g.size) {
                double d = distance(g.position, s.position);
                if (d < minDist) {
                    minDist = d;
                    best = &s;
                }
            }
        }
        
        g.assigned_shelter = best;
        best->remaining_capacity -= g.size;
    }
}
```

**2c. Menangani Area Terdampak (15 poin)**

**Modifikasi pada ekspansi successor:**

```cpp
vector<State> getSuccessors(State current, AttackInfo attack) {
    vector<State> successors;
    
    for (Direction d : directions) {
        State next = move(current, d);
        
        // Cek apakah di area terdampak
        double distToImpact = distance(next, attack.center);
        
        if (distToImpact > attack.radius && isNavigable(next)) {
            successors.push_back(next);
        }
        // Jika dalam radius, jangan tambahkan sebagai successor
    }
    
    return successors;
}
```

**Alternatif: Infinite cost**
```cpp
double cost(State from, State to, AttackInfo attack) {
    if (distance(to, attack.center) <= attack.radius) {
        return INFINITY; // Never choose this path
    }
    return normalCost(from, to);
}
```

**2d. Pseudocode Sistem Evakuasi (20 poin)**

```cpp
struct EvacuationSystem {
    vector<Group> groups;
    vector<Shelter> shelters;
    AttackInfo attack;
    
    map<int, Path> planEvacuation() {
        map<int, Path> allPaths;
        
        // Step 1: Alokasi shelter
        allocateShelters();
        
        // Step 2: Plan path untuk setiap kelompok
        for (int i = 0; i < groups.size(); i++) {
            Path path = aStarSearch(
                groups[i].position,
                groups[i].assigned_shelter.position,
                attack
            );
            allPaths[i] = path;
        }
        
        // Step 3: Deteksi dan resolve konflik
        resolveConflicts(allPaths);
        
        return allPaths;
    }
    
    void allocateShelters() {
        // Reset kapasitas
        for (auto& s : shelters) {
            s.remaining = s.capacity;
        }
        
        // Sort groups by urgency (closest to impact first)
        sort(groups.begin(), groups.end(), 
             [&](Group& a, Group& b) {
                 return distance(a.pos, attack.center) < 
                        distance(b.pos, attack.center);
             });
        
        // Greedy assignment
        for (auto& g : groups) {
            Shelter* best = findBestShelter(g);
            g.target = best;
            best->remaining -= g.size;
        }
    }
    
    Path aStarSearch(Position start, Position goal, AttackInfo attack) {
        PriorityQueue<Node> frontier;
        set<Position> explored;
        
        Node startNode = {start, 0, heuristic(start, goal), {}};
        frontier.push(startNode);
        
        while (!frontier.empty()) {
            Node current = frontier.pop();
            
            if (current.pos == goal) {
                return current.path;
            }
            
            if (explored.count(current.pos)) continue;
            explored.insert(current.pos);
            
            for (Position next : getValidNeighbors(current.pos, attack)) {
                if (!explored.count(next)) {
                    double newG = current.g + cost(current.pos, next);
                    double newH = heuristic(next, goal);
                    Path newPath = current.path;
                    newPath.push_back(next);
                    
                    frontier.push({next, newG, newH, newPath});
                }
            }
        }
        
        return {}; // No path found
    }
    
    vector<Position> getValidNeighbors(Position p, AttackInfo attack) {
        vector<Position> neighbors;
        for (auto dir : directions) {
            Position next = p + dir;
            // Cek: dalam grid, tidak di impact zone, tidak blocked
            if (isValid(next) && 
                distance(next, attack.center) > attack.radius &&
                !isBlocked(next)) {
                neighbors.push_back(next);
            }
        }
        return neighbors;
    }
};
```

**2e. Trade-off Optimalitas vs Fairness (10 poin)**

**Optimalitas Global:**
- Minimize total time: Σ time(groupᵢ)
- Masalah: Kelompok jauh bisa sangat lama

**Fairness:**
- Minimize max time: max(time(groupᵢ))
- Masalah: Mungkin tidak minimize total

**Solusi: Utility Function Gabungan**

```cpp
double utility(vector<double>& times) {
    double totalTime = sum(times);
    double maxTime = max(times);
    double variance = calculateVariance(times);
    
    // Weighted combination
    return ALPHA * totalTime + 
           BETA * maxTime + 
           GAMMA * variance;
}
```

**Strategi Praktis:**

1. **Threshold approach:**
   - Semua kelompok harus evakuasi dalam T_max
   - Di bawah threshold, optimize total time

2. **Priority-based:**
   - Kelompok di area lebih berbahaya dapat prioritas
   - Rute lebih pendek meski total time naik

3. **Iterative improvement:**
   - Mulai dengan greedy allocation
   - Iterasi untuk mengurangi max time tanpa signifikan naikkan total

**Contoh modifikasi:**
```cpp
// Jika kelompok dengan waktu terlama > 2× rata-rata
if (maxTime > 2 * avgTime) {
    // Realokasi shelter atau cari alternatif path
    reallocateLongestGroup();
}
```

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin  
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 113 poin

### Studi Kasus
- Studi Kasus 1: 70 poin
- Studi Kasus 2: 75 poin
- Total: 145 poin

### Total Keseluruhan: 298 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
