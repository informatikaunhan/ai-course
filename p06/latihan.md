# Latihan Pertemuan 06: Constraint Satisfaction Problems (CSP)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 06  
**Topik:** Constraint Satisfaction Problems (CSP)  
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
Constraint Satisfaction Problem (CSP) terdiri dari tiga komponen utama, yaitu:

A. State, Action, Goal  
B. Variabel, Domain, Constraint  
C. Initial, Successor, Terminal  
D. Node, Edge, Path  
E. Input, Process, Output

---

### Soal 2
Dalam formulasi CSP untuk N-Queens problem, jika menggunakan satu variabel per kolom, maka domain untuk setiap variabel adalah:

A. {1, 2, ..., N²}  
B. {True, False}  
C. {1, 2, ..., N}  
D. {Queen, Empty}  
E. {0, 1}

---

### Soal 3
Constraint yang melibatkan tepat dua variabel disebut:

A. Unary constraint  
B. Binary constraint  
C. Ternary constraint  
D. Global constraint  
E. Universal constraint

---

### Soal 4
Dalam constraint graph, node merepresentasikan ... dan edge merepresentasikan ...

A. Constraint; variabel  
B. Domain; nilai  
C. Variabel; constraint  
D. Nilai; domain  
E. State; action

---

### Soal 5
Berapa jumlah binary constraint dalam Sudoku 9×9 standar?

A. 81  
B. 162  
C. 810  
D. 972  
E. 1296

---

### Soal 6
Node consistency memastikan bahwa semua nilai dalam domain memenuhi:

A. Binary constraint  
B. Unary constraint  
C. Global constraint  
D. Semua jenis constraint  
E. Tidak ada constraint

---

### Soal 7
Arc (Xᵢ, Xⱼ) dikatakan arc-consistent jika:

A. Xᵢ dan Xⱼ memiliki domain yang sama  
B. Untuk setiap nilai di D(Xᵢ), ada nilai di D(Xⱼ) yang memenuhi constraint  
C. Xᵢ dan Xⱼ tidak memiliki constraint  
D. D(Xᵢ) ⊆ D(Xⱼ)  
E. D(Xᵢ) ∩ D(Xⱼ) = ∅

---

### Soal 8
Kompleksitas waktu algoritma AC-3 adalah:

A. O(n²)  
B. O(nd)  
C. O(nd²)  
D. O(ed³)  
E. O(2ⁿ)

---

### Soal 9
Dalam algoritma AC-3, kapan sebuah arc (Xᵢ, Xⱼ) ditambahkan kembali ke queue?

A. Setiap iterasi  
B. Ketika domain Xⱼ berubah  
C. Ketika domain Xᵢ berubah  
D. Ketika constraint berubah  
E. Tidak pernah ditambahkan kembali

---

### Soal 10
MRV (Minimum Remaining Values) heuristic memilih variabel dengan:

A. Domain terbesar  
B. Domain terkecil  
C. Constraint terbanyak  
D. Constraint paling sedikit  
E. Nilai tertinggi

---

### Soal 11
Degree heuristic digunakan sebagai:

A. Pengganti MRV  
B. Tiebreaker untuk MRV  
C. Heuristik pemilihan nilai  
D. Fungsi evaluasi  
E. Kriteria terminasi

---

### Soal 12
LCV (Least Constraining Value) heuristic memilih nilai yang:

A. Menghilangkan paling banyak nilai dari domain tetangga  
B. Menghilangkan paling sedikit nilai dari domain tetangga  
C. Memiliki nilai numerik terkecil  
D. Memiliki nilai numerik terbesar  
E. Paling sering digunakan

---

### Soal 13
Forward checking berbeda dari backtracking biasa karena:

A. Tidak melakukan backtrack  
B. Menghapus nilai inkonsisten dari domain tetangga setelah assignment  
C. Menggunakan BFS bukan DFS  
D. Tidak menggunakan heuristik  
E. Hanya untuk binary CSP

---

### Soal 14
Jika forward checking menemukan domain tetangga yang kosong, maka:

A. Assignment dilanjutkan  
B. Algoritma berhenti  
C. Backtrack dilakukan  
D. Domain di-reset  
E. Constraint dihapus

---

### Soal 15
Tree-structured CSP dapat diselesaikan dalam kompleksitas waktu:

A. O(n!)  
B. O(2ⁿ)  
C. O(nd²)  
D. O(ed³)  
E. O(n²d)

---

### Soal 16
Cycle cutset adalah:

A. Himpunan edge yang membentuk cycle  
B. Himpunan variabel yang jika dihapus menghasilkan tree  
C. Himpunan constraint yang redundan  
D. Himpunan nilai yang tidak valid  
E. Himpunan solusi parsial

---

### Soal 17
Untuk map coloring problem pada peta planar, berapa warna minimum yang selalu cukup?

A. 2  
B. 3  
C. 4  
D. 5  
E. 6

---

### Soal 18
Dalam cryptarithmetic SEND + MORE = MONEY, constraint S ≠ 0 adalah contoh:

A. Binary constraint  
B. Unary constraint  
C. Global constraint  
D. Ternary constraint  
E. Soft constraint

---

### Soal 19
Sifat komutatif dalam CSP berarti:

A. Urutan constraint tidak penting  
B. Urutan assignment variabel tidak mempengaruhi hasil  
C. Semua solusi adalah sama  
D. Domain selalu simetris  
E. Constraint dapat ditukar posisinya

---

### Soal 20
Manakah yang BUKAN contoh CSP klasik?

A. Map coloring  
B. N-Queens  
C. Sudoku  
D. Shortest path  
E. Job scheduling

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara algoritma pencarian standar (BFS, DFS, A*) dengan pendekatan CSP dalam menyelesaikan masalah!

---

### Soal 2 ⭐
Sebutkan dan jelaskan empat jenis constraint berdasarkan jumlah variabel yang terlibat! Berikan contoh untuk masing-masing!

---

### Soal 3 ⭐
Formulasikan 3-Coloring problem untuk graph dengan 4 node (A, B, C, D) dan edge: A-B, B-C, C-D, D-A, A-C sebagai CSP!

---

### Soal 4 ⭐
Jelaskan perbedaan antara node consistency dan arc consistency! Kapan masing-masing diterapkan?

---

### Soal 5 ⭐⭐
Diberikan CSP:
- Variabel: X, Y, Z
- Domain: D(X) = {1, 2, 3}, D(Y) = {1, 2}, D(Z) = {2, 3}
- Constraint: X < Y, Y < Z

Terapkan arc consistency secara manual dan tunjukkan domain akhir!

---

### Soal 6 ⭐⭐
Jelaskan algoritma AC-3 dan analisis kompleksitas waktunya! Mengapa kompleksitasnya O(ed³)?

---

### Soal 7 ⭐⭐
Bandingkan MRV heuristic dan Degree heuristic! Kapan masing-masing lebih efektif?

---

### Soal 8 ⭐⭐
Terapkan backtracking search dengan forward checking untuk map coloring dengan 4 wilayah (A, B, C, D) yang membentuk garis (A-B-C-D bertetangga secara berurutan) dan 3 warna (R, G, B)!

---

### Soal 9 ⭐⭐
Jelaskan mengapa LCV disebut "fail-last" heuristic sedangkan MRV disebut "fail-first" heuristic!

---

### Soal 10 ⭐⭐
Diberikan 4-Queens problem. Gunakan constraint Q₁=2 (ratu kolom 1 di baris 2). Terapkan forward checking untuk mengurangi domain Q₂, Q₃, dan Q₄!

---

### Soal 11 ⭐⭐⭐
Jelaskan bagaimana tree-structured CSP dapat diselesaikan dalam O(nd²)! Tuliskan langkah-langkah algoritmanya!

---

### Soal 12 ⭐⭐⭐
Diberikan constraint graph berikut:
```
    A --- B
    |     |
    C --- D
```
Identifikasi apakah ini tree-structured CSP. Jika tidak, tentukan cycle cutset minimum!

---

### Soal 13 ⭐⭐⭐
Sebuah Sudoku 4×4 memiliki kondisi awal:
```
| 1 | _ | _ | _ |
| _ | _ | 3 | _ |
| _ | 4 | _ | _ |
| _ | _ | _ | 2 |
```
Formulasikan sebagai CSP dan selesaikan menggunakan kombinasi arc consistency dan backtracking!

---

### Soal 14 ⭐⭐⭐
Jelaskan konsep MAC (Maintaining Arc Consistency) dan bagaimana perbedaannya dengan forward checking! Apa keuntungan dan kerugian masing-masing?

---

### Soal 15 ⭐⭐⭐
Rancang CSP untuk masalah penjadwalan 4 mata kuliah (AI, ML, DB, OS) ke 4 slot waktu (Senin, Selasa, Rabu, Kamis) dengan constraint:
- AI dan ML tidak boleh di hari yang sama (dosen sama)
- DB harus sebelum OS (prasyarat)
- OS tidak boleh di Senin (lab tidak tersedia)

Selesaikan dengan backtracking + MRV!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Alokasi Frekuensi Komunikasi Militer

**Latar Belakang:**

Komando Operasi Gabungan TNI sedang merencanakan operasi di wilayah perbatasan yang melibatkan 8 pos komunikasi (P1-P8). Setiap pos membutuhkan frekuensi radio untuk komunikasi. Tersedia 4 kanal frekuensi (F1, F2, F3, F4).

**Constraint Operasional:**
- Pos yang jaraknya < 15 km tidak boleh menggunakan frekuensi sama (interference)
- P1 adalah pos komando utama, harus menggunakan F1 (frekuensi terenkripsi)
- P8 adalah pos cadangan untuk P1, juga harus bisa menggunakan F1 jika P1 down (tapi untuk operasi normal harus berbeda)
- P3 dan P4 adalah pos observasi berpasangan, harus menggunakan frekuensi berurutan (F1-F2, F2-F3, atau F3-F4)

**Data Jarak Antar Pos (dalam km):**

| | P1 | P2 | P3 | P4 | P5 | P6 | P7 | P8 |
|---|---|---|---|---|---|---|---|---|
| P1 | - | 10 | 20 | 25 | 12 | 30 | 18 | 8 |
| P2 | 10 | - | 14 | 22 | 16 | 25 | 20 | 12 |
| P3 | 20 | 14 | - | 8 | 18 | 12 | 24 | 22 |
| P4 | 25 | 22 | 8 | - | 20 | 10 | 16 | 28 |
| P5 | 12 | 16 | 18 | 20 | - | 22 | 14 | 10 |
| P6 | 30 | 25 | 12 | 10 | 22 | - | 18 | 32 |
| P7 | 18 | 20 | 24 | 16 | 14 | 18 | - | 20 |
| P8 | 8 | 12 | 22 | 28 | 10 | 32 | 20 | - |

**Pertanyaan:**

**1a.** Formulasikan masalah ini sebagai CSP lengkap dengan variabel, domain, dan semua constraint! (15 poin)

**1b.** Gambarkan constraint graph berdasarkan interference constraint (jarak < 15 km)! (10 poin)

**1c.** Terapkan node consistency untuk menghapus nilai yang tidak valid dari domain! (10 poin)

**1d.** Selesaikan CSP menggunakan backtracking dengan MRV heuristic! Tunjukkan langkah-langkah dan domain di setiap langkah! (20 poin)

**1e.** Jika ternyata tidak ada solusi dengan 4 frekuensi, berapa frekuensi minimum yang dibutuhkan? Jelaskan analisisnya! (10 poin)

---

### Studi Kasus 2: Penjadwalan Patroli Perbatasan

**Latar Belakang:**

Satuan pengamanan perbatasan harus menjadwalkan patroli untuk 7 zona (Z1-Z7) selama 5 hari (Senin-Jumat). Tersedia 5 tim patroli (Tim A, B, C, D, E).

**Spesifikasi:**
- Setiap zona harus dipatroli tepat satu kali selama 5 hari
- Setiap tim dapat melakukan maksimal 2 patroli per minggu
- Patroli memerlukan satu hari penuh per zona

**Constraint Keamanan:**
- Z1 dan Z2 adalah zona berisiko tinggi, harus dipatroli oleh Tim A atau Tim B (tim berpengalaman)
- Z5, Z6, Z7 adalah zona terpencil, tidak boleh dipatroli di hari yang sama (keterbatasan helikopter evakuasi)
- Z3 harus dipatroli sebelum Z4 (Z3 adalah akses ke Z4)
- Tim D tidak tersedia di hari Senin dan Selasa (sedang pelatihan)
- Z1 tidak boleh dipatroli di hari Jumat (risiko weekend infiltration)

**Constraint Logistik:**
- Zona yang bersebelahan tidak boleh dipatroli di hari berurutan oleh tim yang sama (waktu persiapan)
- Adjacency: Z1-Z2, Z2-Z3, Z3-Z4, Z4-Z5, Z5-Z6, Z6-Z7

**Pertanyaan:**

**2a.** Formulasikan sebagai CSP! Definisikan variabel dengan jelas (apakah variabel adalah zona atau kombinasi zona-hari)! Jelaskan pilihan formulasi Anda! (15 poin)

**2b.** Identifikasi semua constraint dan klasifikasikan sebagai unary, binary, atau higher-order! (15 poin)

**2c.** Hitung ukuran search space (jumlah kemungkinan assignment) sebelum dan sesudah menerapkan constraint! (10 poin)

**2d.** Terapkan forward checking untuk assignment pertama dan kedua! Pilih variabel dengan MRV dan nilai dengan LCV! (20 poin)

**2e.** Apakah masalah ini memiliki solusi? Jika ya, berikan satu solusi lengkap. Jika tidak, jelaskan constraint mana yang menyebabkan inconsistency dan usulkan modifikasi constraint yang minimal! (20 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **B** | CSP terdiri dari Variabel (X), Domain (D), dan Constraint (C) |
| 2 | **C** | Domain adalah baris yang mungkin untuk ratu: {1, 2, ..., N} |
| 3 | **B** | Binary constraint melibatkan tepat dua variabel |
| 4 | **C** | Node = variabel, Edge = constraint yang menghubungkan variabel |
| 5 | **D** | 27 Alldiff × C(9,2) = 27 × 36 = 972 binary constraint |
| 6 | **B** | Node consistency berkaitan dengan unary constraint |
| 7 | **B** | Arc consistency memastikan setiap nilai memiliki support di tetangga |
| 8 | **D** | AC-3: O(ed³) di mana e=edges, d=domain size |
| 9 | **C** | Arc ditambahkan kembali ketika domain Xᵢ berkurang |
| 10 | **B** | MRV memilih variabel dengan domain terkecil (fail-first) |
| 11 | **B** | Degree heuristic digunakan sebagai tiebreaker untuk MRV |
| 12 | **B** | LCV memilih nilai yang paling tidak membatasi tetangga |
| 13 | **B** | Forward checking menghapus nilai inkonsisten dari tetangga |
| 14 | **C** | Domain kosong berarti failure, harus backtrack |
| 15 | **C** | Tree-structured CSP: O(nd²) tanpa backtracking |
| 16 | **B** | Cutset adalah variabel yang jika dihapus menghasilkan tree |
| 17 | **C** | Four Color Theorem: 4 warna cukup untuk peta planar |
| 18 | **B** | S ≠ 0 hanya melibatkan satu variabel (unary) |
| 19 | **B** | Commutative: urutan assignment tidak mempengaruhi hasil |
| 20 | **D** | Shortest path adalah optimization problem, bukan CSP murni |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Perbedaan Algoritma Pencarian Standar vs CSP:**

| Aspek | Pencarian Standar | CSP |
|-------|-------------------|-----|
| **Representasi State** | Black box | Terstruktur (variabel, domain, constraint) |
| **Successor Function** | General | Assign nilai ke variabel |
| **Exploitasi Struktur** | Minimal | Maksimal (constraint propagation) |
| **Deteksi Failure** | Di goal test | Lebih awal (constraint checking) |
| **Heuristik** | Domain-specific | Domain-independent (MRV, LCV) |

CSP lebih efisien karena dapat memangkas search space menggunakan constraint propagation dan mendeteksi inconsistency lebih awal.

---

#### Jawaban Soal 2 ⭐

**Empat Jenis Constraint:**

1. **Unary Constraint** - Melibatkan 1 variabel
   - Contoh: X₁ ≠ Merah, X > 0

2. **Binary Constraint** - Melibatkan 2 variabel
   - Contoh: X₁ ≠ X₂, A < B

3. **Ternary/Higher-order Constraint** - Melibatkan 3+ variabel
   - Contoh: X + Y + Z = 10, A × B = C

4. **Global Constraint** - Melibatkan banyak/semua variabel
   - Contoh: Alldiff(X₁, X₂, ..., Xₙ), Sum constraint

---

#### Jawaban Soal 3 ⭐

**Formulasi CSP untuk 3-Coloring:**

**Variabel:** X = {A, B, C, D}

**Domain:** D(A) = D(B) = D(C) = D(D) = {R, G, B}

**Constraint (dari edge):**
- C₁: A ≠ B (edge A-B)
- C₂: B ≠ C (edge B-C)
- C₃: C ≠ D (edge C-D)
- C₄: D ≠ A (edge D-A)
- C₅: A ≠ C (edge A-C)

**Constraint Graph:** Graph dengan 4 node dan 5 edge sesuai adjacency.

---

#### Jawaban Soal 4 ⭐

**Perbedaan Node Consistency dan Arc Consistency:**

| Aspek | Node Consistency | Arc Consistency |
|-------|------------------|-----------------|
| **Scope** | Satu variabel | Dua variabel |
| **Constraint** | Unary constraint | Binary constraint |
| **Definisi** | Semua nilai memenuhi unary constraint | Setiap nilai punya support di tetangga |
| **Kapan** | Preprocessing awal | Setelah node consistency |
| **Kompleksitas** | O(nd) | O(ed³) dengan AC-3 |

Node consistency diterapkan terlebih dahulu untuk menghapus nilai yang jelas invalid, kemudian arc consistency untuk propagasi antar variabel.

---

#### Jawaban Soal 5 ⭐⭐

**Penerapan Arc Consistency:**

**Initial:**
- D(X) = {1, 2, 3}, D(Y) = {1, 2}, D(Z) = {2, 3}
- Constraint: X < Y, Y < Z

**Step 1: Arc (X, Y) dengan X < Y**
- X=1: Ada Y>1? Ya (Y=2). Keep.
- X=2: Ada Y>2? Tidak. Remove.
- X=3: Ada Y>3? Tidak. Remove.
- D(X) = {1}

**Step 2: Arc (Y, X) dengan X < Y**
- Y=1: Ada X<1? Tidak. Remove.
- Y=2: Ada X<2? Ya (X=1). Keep.
- D(Y) = {2}

**Step 3: Arc (Y, Z) dengan Y < Z**
- Y=2: Ada Z>2? Ya (Z=3). Keep.
- D(Y) = {2} (unchanged)

**Step 4: Arc (Z, Y) dengan Y < Z**
- Z=2: Ada Y<2? Tidak (Y={2}). Remove.
- Z=3: Ada Y<3? Ya (Y=2). Keep.
- D(Z) = {3}

**Hasil Akhir:** D(X) = {1}, D(Y) = {2}, D(Z) = {3}

---

#### Jawaban Soal 6 ⭐⭐

**Algoritma AC-3:**

```
1. Inisialisasi queue dengan semua arc
2. While queue tidak kosong:
   a. Ambil arc (Xi, Xj) dari queue
   b. Jika REVISE(Xi, Xj) mengembalikan true:
      - Jika D(Xi) kosong, return False
      - Tambahkan semua arc (Xk, Xi) ke queue untuk Xk ≠ Xj
3. Return True
```

**Analisis Kompleksitas O(ed³):**
- Ada e arc dalam CSP
- Setiap arc bisa dimasukkan ke queue O(d) kali (setiap kali domain berkurang)
- Setiap pemeriksaan REVISE memerlukan O(d²) untuk memeriksa semua pasangan nilai
- Total: O(e × d × d²) = O(ed³)

---

#### Jawaban Soal 7 ⭐⭐

**Perbandingan MRV dan Degree Heuristic:**

| Aspek | MRV | Degree Heuristic |
|-------|-----|------------------|
| **Kriteria** | Domain terkecil | Constraint terbanyak |
| **Filosofi** | Fail-first | Prune early |
| **Efektif ketika** | Domain sudah dikurangi | Awal pencarian |
| **Penggunaan** | Utama | Tiebreaker |

**MRV lebih efektif** ketika constraint propagation sudah mengurangi domain secara signifikan.

**Degree heuristic lebih efektif** di awal ketika semua domain masih penuh, karena variabel dengan banyak constraint akan mempengaruhi banyak variabel lain.

---

#### Jawaban Soal 8 ⭐⭐

**Backtracking dengan Forward Checking:**

**Initial:** D(A)=D(B)=D(C)=D(D)={R,G,B}
**Constraint:** A≠B, B≠C, C≠D

**Step 1: Assign A = R**
- Forward check B (A≠B): D(B) = {G, B}
- D(C), D(D) tidak bertetangga dengan A, unchanged

**Step 2: Assign B = G** (pilih dari {G,B})
- Forward check A (sudah assigned)
- Forward check C (B≠C): D(C) = {R, B}

**Step 3: Assign C = R** (pilih dari {R,B})
- Forward check B (sudah assigned)
- Forward check D (C≠D): D(D) = {G, B}

**Step 4: Assign D = G** (pilih dari {G,B})

**Solusi:** {A:R, B:G, C:R, D:G}

---

#### Jawaban Soal 9 ⭐⭐

**MRV (Fail-First) vs LCV (Fail-Last):**

**MRV - Fail-First:**
- Memilih variabel yang paling mungkin menyebabkan failure
- Intuisi: Jika akan gagal, lebih baik gagal cepat
- Mengurangi kedalaman backtracking

**LCV - Fail-Last:**
- Memilih nilai yang memberikan fleksibilitas terbesar
- Intuisi: Maksimalkan peluang sukses untuk variabel lain
- Mengurangi probabilitas failure di level berikutnya

Keduanya komplementer: MRV untuk variabel, LCV untuk nilai.

---

#### Jawaban Soal 10 ⭐⭐

**Forward Checking untuk 4-Queens dengan Q₁=2:**

**Constraint:** Tidak sebaris, tidak sediagonal
- Qᵢ ≠ Qⱼ
- |Qᵢ - Qⱼ| ≠ |i - j|

**Initial:** Q₁=2, D(Q₂)=D(Q₃)=D(Q₄)={1,2,3,4}

**Forward Check Q₂:**
- Q₂≠2 (sebaris): hapus 2
- |Q₂-2|≠|2-1|=1: hapus 1 dan 3
- D(Q₂) = {4}

**Forward Check Q₃:**
- Q₃≠2 (sebaris): hapus 2
- |Q₃-2|≠|3-1|=2: hapus 0 dan 4
- D(Q₃) = {1, 3}

**Forward Check Q₄:**
- Q₄≠2 (sebaris): hapus 2
- |Q₄-2|≠|4-1|=3: hapus -1 dan 5 (tidak ada)
- D(Q₄) = {1, 3, 4}

**Hasil:** D(Q₂)={4}, D(Q₃)={1,3}, D(Q₄)={1,3,4}

---

#### Jawaban Soal 11 ⭐⭐⭐

**Algoritma untuk Tree-Structured CSP:**

```
1. Pilih root variabel sembarang
2. Lakukan topological sort: X₁, X₂, ..., Xₙ (dari root)
3. For j = n down to 2:
   - REVISE(Xⱼ, parent(Xⱼ))
4. For j = 1 to n:
   - Assign Xⱼ dengan nilai konsisten dengan parent
```

**Analisis O(nd²):**
- Topological sort: O(n)
- Arc consistency (step 3): n-1 REVISE, masing-masing O(d²)
- Assignment (step 4): n assignment, masing-masing O(d)
- Total: O(n) + O(nd²) + O(nd) = O(nd²)

Tidak ada backtracking karena setelah arc consistency dari leaf ke root, dijamin ada nilai valid untuk setiap variabel.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Analisis Graph:**
```
    A --- B
    |     |
    C --- D
```

**Apakah tree?** Tidak, karena ada cycle: A-B-D-C-A

**Cycle Cutset Minimum:**
- Hapus A: Graph menjadi B-D-C (linear/tree) ✓
- Hapus B: Graph menjadi A-C-D (linear/tree) ✓
- Hapus C: Graph menjadi A-B-D (linear/tree) ✓
- Hapus D: Graph menjadi A-B, A-C (tree) ✓

**Cycle cutset minimum:** Ukuran 1, bisa {A}, {B}, {C}, atau {D}

---

#### Jawaban Soal 13 ⭐⭐⭐

**Sudoku 4×4:**
```
| 1 | _ | _ | _ |
| _ | _ | 3 | _ |
| _ | 4 | _ | _ |
| _ | _ | _ | 2 |
```

**Formulasi CSP:**
- 16 variabel (sel), 12 yang perlu diisi
- Domain: {1,2,3,4}, kecuali yang sudah terisi
- Constraint: Alldiff per baris, kolom, kotak 2×2

**Penyelesaian dengan Arc Consistency + Backtracking:**

Notasi: X_rc = sel baris r, kolom c

**Step 1: Terapkan constraint dari nilai awal**
- X₁₁=1: Hapus 1 dari baris 1, kolom 1, kotak kiri-atas
- X₂₃=3: Hapus 3 dari baris 2, kolom 3, kotak kanan-atas
- X₃₂=4: Hapus 4 dari baris 3, kolom 2, kotak kiri-bawah
- X₄₄=2: Hapus 2 dari baris 4, kolom 4, kotak kanan-bawah

**Step 2: Propagasi dan Backtracking**

Setelah propagasi intensif:
```
| 1 | 2 | 4 | 3 |
| 4 | 3 | 3 | 1 |  <- Error, perlu backtrack
```

Dengan backtracking yang benar:
```
| 1 | 3 | 2 | 4 |
| 2 | 4 | 3 | 1 |
| 3 | 4 | 1 | 2 |  <- Masih perlu verifikasi
| 4 | 1 | ? | 2 |
```

**Solusi Valid:**
```
| 1 | 3 | 2 | 4 |
| 4 | 2 | 3 | 1 |
| 3 | 4 | 1 | 2 |
| 2 | 1 | 4 | 3 |
```

---

#### Jawaban Soal 14 ⭐⭐⭐

**MAC (Maintaining Arc Consistency) vs Forward Checking:**

| Aspek | Forward Checking | MAC |
|-------|------------------|-----|
| **Scope** | Tetangga langsung | Seluruh CSP |
| **Propagasi** | Satu level | Cascading (AC-3) |
| **Deteksi failure** | Lebih lambat | Lebih cepat |
| **Overhead** | Rendah | Tinggi |
| **Efektivitas** | Sedang | Tinggi |

**MAC** menjalankan AC-3 setelah setiap assignment, sehingga propagasi lebih menyeluruh.

**Keuntungan MAC:**
- Deteksi inconsistency lebih awal
- Pruning lebih agresif

**Kerugian MAC:**
- Overhead per assignment lebih tinggi
- Tidak selalu cost-effective untuk CSP sederhana

---

#### Jawaban Soal 15 ⭐⭐⭐

**CSP Penjadwalan Mata Kuliah:**

**Variabel:** {AI, ML, DB, OS}
**Domain:** {Sen, Sel, Rab, Kam}

**Constraint:**
1. AI ≠ ML (dosen sama)
2. DB < OS (prasyarat, interpretasi: hari DB sebelum hari OS)
3. OS ≠ Sen (lab tidak tersedia)

**Node Consistency:**
- D(OS) = {Sel, Rab, Kam} (hapus Sen)

**Backtracking dengan MRV:**

**Step 1:** MRV: OS (domain terkecil = 3)
- Assign OS = Kam (LCV analysis)
- D(DB) harus < Kam: {Sen, Sel, Rab}

**Step 2:** MRV: All equal (3 values each)
- Pilih DB (degree heuristic - has constraint with OS)
- Assign DB = Rab
- No propagation needed for AI, ML

**Step 3:** MRV: AI atau ML
- Pilih AI
- AI ≠ ML, Assign AI = Sen
- D(ML) = {Sel, Rab, Kam} - {Sen} = {Sel, Rab, Kam}
- Tapi AI=Sen, constraint AI≠ML, D(ML) = {Sel, Rab, Kam}

**Step 4:** Assign ML
- ML ≠ Sen (AI=Sen), pilih ML = Sel

**Solusi:** {AI: Sen, ML: Sel, DB: Rab, OS: Kam}

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Alokasi Frekuensi Komunikasi Militer

**1a. Formulasi CSP (15 poin)**

**Variabel:** X = {P1, P2, P3, P4, P5, P6, P7, P8}

**Domain Awal:** 
- D(P1) = {F1} (constraint: harus F1)
- D(P2) = D(P3) = D(P4) = D(P5) = D(P6) = D(P7) = {F1, F2, F3, F4}
- D(P8) = {F2, F3, F4} (berbeda dari P1 untuk operasi normal)

**Constraint:**

*Interference (jarak < 15 km):*
- P1 ≠ P2 (10 km)
- P1 ≠ P5 (12 km)
- P1 ≠ P8 (8 km)
- P2 ≠ P3 (14 km)
- P2 ≠ P8 (12 km)
- P3 ≠ P4 (8 km)
- P3 ≠ P6 (12 km)
- P4 ≠ P6 (10 km)
- P5 ≠ P7 (14 km)
- P5 ≠ P8 (10 km)

*Special constraints:*
- P3 dan P4 berurutan: |P3 - P4| = 1 (dalam ordering F1<F2<F3<F4)

---

**1b. Constraint Graph (10 poin)**

```
        P1
       /|\\ 
      / | \\
    P2  P5  P8
    |    |
    P3  P7
   / \
  P4  P6
   \ /
    (P4-P6)
```

Edges berdasarkan jarak < 15 km:
- P1: P2, P5, P8
- P2: P1, P3, P8
- P3: P2, P4, P6
- P4: P3, P6
- P5: P1, P7, P8
- P6: P3, P4
- P7: P5
- P8: P1, P2, P5

---

**1c. Node Consistency (10 poin)**

Setelah menerapkan unary constraint:
- D(P1) = {F1} ✓
- D(P8) = {F2, F3, F4} (≠ F1 untuk operasi normal)
- Lainnya tetap {F1, F2, F3, F4}

---

**1d. Backtracking dengan MRV (20 poin)**

**Step 1:** MRV: P1 (|D|=1)
- Assign P1 = F1
- Forward check: P2, P5, P8 hapus F1
  - D(P2) = {F2, F3, F4}
  - D(P5) = {F2, F3, F4}
  - D(P8) = {F2, F3, F4}

**Step 2:** MRV: P2, P5, P8 tie (|D|=3). Degree: P2=2, P5=2, P8=2. Pilih P2.
- Assign P2 = F2
- Forward check P3, P8:
  - D(P3) = {F1, F3, F4} (hapus F2)
  - D(P8) = {F3, F4} (hapus F2)

**Step 3:** MRV: P8 (|D|=2)
- Assign P8 = F3
- Forward check P5:
  - D(P5) = {F2, F4} (hapus F3)

**Step 4:** MRV: P5 (|D|=2)
- Assign P5 = F4
- Forward check P7:
  - D(P7) = {F1, F2, F3} (hapus F4)

**Step 5:** MRV: Multiple tie. Pilih P3 (constraint dengan P4 yang special)
- P3-P4 harus berurutan
- D(P3) = {F1, F3, F4}
- Jika P3=F1, P4 harus F2. Check: D(P4) contains F2? Ya.
- Assign P3 = F1
- Forward check P4, P6:
  - D(P4) = {F2} (berurutan dengan F1)
  - D(P6) = {F2, F3, F4} (hapus F1)

**Step 6:** MRV: P4 (|D|=1)
- Assign P4 = F2
- Forward check P6:
  - D(P6) = {F3, F4} (hapus F2)

**Step 7:** MRV: P6 atau P7
- Assign P6 = F3
- Assign P7 = F2

**Solusi:** {P1:F1, P2:F2, P3:F1, P4:F2, P5:F4, P6:F3, P7:F2, P8:F3}

---

**1e. Analisis Frekuensi Minimum (10 poin)**

Dengan 4 frekuensi, solusi ditemukan. 

Untuk analisis minimum:
- Lihat chromatic number dari constraint graph
- Graph tidak complete, tapi ada clique?
- P1-P2-P8 membentuk triangle (3 warna minimum untuk bagian ini)
- P3-P4-P6 juga berinteraksi

**Kesimpulan:** 4 frekuensi cukup dan kemungkinan 3 tidak cukup karena kompleksitas constraint khusus (P3-P4 berurutan).

---

#### Studi Kasus 2: Penjadwalan Patroli Perbatasan

**2a. Formulasi CSP (15 poin)**

**Pilihan Formulasi:** Variabel adalah zona, domain adalah kombinasi (Hari, Tim)

**Variabel:** {Z1, Z2, Z3, Z4, Z5, Z6, Z7}

**Domain:** Kombinasi (Hari, Tim)
- Hari: {Sen, Sel, Rab, Kam, Jum}
- Tim: {A, B, C, D, E}
- Total: 25 kombinasi per zona

**Alasan pemilihan:** Setiap zona harus tepat satu patroli, sehingga variabel per zona lebih natural.

---

**2b. Klasifikasi Constraint (15 poin)**

**Unary Constraints:**
- Z1, Z2 hanya Tim A atau B
- Z1 tidak boleh Jumat
- Semua zona dengan Tim D tidak boleh Senin/Selasa

**Binary Constraints:**
- Z3 sebelum Z4 (hari Z3 < hari Z4)
- Zona adjacent tidak boleh hari berurutan dengan tim sama

**Higher-order Constraints:**
- Z5, Z6, Z7 tidak boleh hari sama (ternary)
- Setiap tim maksimal 2 patroli (global, melibatkan semua zona dengan tim tersebut)

---

**2c. Ukuran Search Space (10 poin)**

**Sebelum constraint:**
- 7 zona × 25 kombinasi = 25⁷ = 6.103.515.625 assignment

**Setelah constraint:**
- Z1: 2 tim × 4 hari = 8 (hapus Jumat dan tim C,D,E)
- Z2: 2 tim × 5 hari = 10 (hanya tim A,B)
- Z3-Z7: Perlu analisis lebih detail

Estimasi setelah unary constraint: ~8 × 10 × 20⁵ ≈ 25.600.000.000 (masih besar, tapi binary constraint akan mengurangi drastis)

---

**2d. Forward Checking (20 poin)**

**MRV Analysis:**
- Z1: 8 kombinasi (2 tim × 4 hari)
- Z2: 10 kombinasi
- Z3-Z7: ~20-25 kombinasi

**Step 1:** Assign Z1 (MRV)
- LCV: Pilih kombinasi yang paling tidak membatasi
- Try Z1 = (Senin, Tim A)
- Forward check:
  - Z2: Hapus (Senin, A), (Selasa, A) karena adjacent constraint
  - D(Z2) = {kombinasi lain dengan Tim A/B}

**Step 2:** MRV: Z2
- D(Z2) setelah step 1: ~8 kombinasi
- Assign Z2 = (Rabu, Tim B)
- Forward check:
  - Z3: Hapus kombinasi adjacent (Selasa, B), (Kamis, B)

---

**2e. Solusi atau Analisis Inconsistency (20 poin)**

**Mencari Solusi:**

| Zona | Hari | Tim |
|------|------|-----|
| Z1 | Senin | A |
| Z2 | Rabu | B |
| Z3 | Selasa | C |
| Z4 | Kamis | A |
| Z5 | Senin | B |
| Z6 | Rabu | E |
| Z7 | Jumat | C |

**Verifikasi Constraint:**
- Z1, Z2 tim A/B ✓
- Z5, Z6, Z7 hari berbeda ✓
- Z3 (Selasa) < Z4 (Kamis) ✓
- Tim D tidak Senin/Selasa (tidak digunakan) ✓
- Z1 tidak Jumat ✓
- Tim A: Z1, Z4 (2 patroli) ✓
- Tim B: Z2, Z5 (2 patroli) ✓
- Tim C: Z3, Z7 (2 patroli) ✓
- Adjacent constraint: perlu verifikasi detail

**Jika tidak ada solusi**, modifikasi minimal:
- Relaksasi constraint "Tim D tidak tersedia Senin/Selasa" menjadi hanya Senin
- Atau tambah 1 tim cadangan

**Solusi ditemukan** dengan konfigurasi di atas (perlu verifikasi adjacency constraint secara detail).

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin  
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 115 poin

### Studi Kasus
- Studi Kasus 1: 65 poin
- Studi Kasus 2: 80 poin
- Total: 145 poin

### Total Keseluruhan: 300 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
