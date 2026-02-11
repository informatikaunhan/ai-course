# Modul 06: Constraint Satisfaction Problems (CSP)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 06  
**Topik:** Constraint Satisfaction Problems (CSP)  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan definisi dan komponen Constraint Satisfaction Problem (variabel, domain, constraint)
2. Memformulasikan berbagai masalah nyata sebagai CSP
3. Menerapkan teknik constraint propagation termasuk node consistency dan arc consistency
4. Mengimplementasikan algoritma AC-3 untuk arc consistency
5. Menerapkan backtracking search untuk menyelesaikan CSP
6. Menggunakan heuristik pemilihan variabel (MRV, degree heuristic) dan nilai (LCV)
7. Mengimplementasikan forward checking untuk meningkatkan efisiensi pencarian

---

## 1. Pendahuluan Constraint Satisfaction Problems

### 1.1 Motivasi: Mengapa CSP?

Pada pertemuan sebelumnya (Pertemuan 2-4), kita telah mempelajari algoritma pencarian (BFS, DFS, A*, dll.) untuk memecahkan masalah. Algoritma-algoritma tersebut memperlakukan state sebagai "black box" - tidak memanfaatkan struktur internal dari masalah.

> **Constraint Satisfaction Problem (CSP)** adalah jenis masalah di mana state didefinisikan oleh **variabel** yang harus diberi nilai dari **domain** tertentu, dan solusi harus memenuhi sekumpulan **constraint** (batasan).

CSP memungkinkan kita mengeksploitasi struktur masalah untuk pencarian yang lebih efisien.

### 1.2 Definisi Formal CSP

> **CSP** secara formal didefinisikan oleh tiga komponen:
> 1. **X** = {X₁, X₂, ..., Xₙ} : himpunan variabel
> 2. **D** = {D₁, D₂, ..., Dₙ} : himpunan domain untuk setiap variabel
> 3. **C** = {C₁, C₂, ..., Cₘ} : himpunan constraint yang menentukan kombinasi nilai yang diperbolehkan

| Komponen | Deskripsi | Contoh (Map Coloring) |
|----------|-----------|----------------------|
| **Variabel (X)** | Entitas yang harus diberi nilai | Wilayah: WA, NT, SA, Q, NSW, V, T |
| **Domain (D)** | Nilai-nilai yang mungkin | Warna: {Merah, Hijau, Biru} |
| **Constraint (C)** | Batasan yang harus dipenuhi | Wilayah bertetangga ≠ warna sama |

### 1.3 Jenis-Jenis Constraint

| Jenis Constraint | Deskripsi | Contoh |
|------------------|-----------|--------|
| **Unary** | Melibatkan satu variabel | X₁ ≠ Merah |
| **Binary** | Melibatkan dua variabel | X₁ ≠ X₂ |
| **Higher-order** | Melibatkan lebih dari dua variabel | X₁ + X₂ + X₃ ≤ 10 |
| **Global** | Melibatkan semua/banyak variabel | Alldiff(X₁, X₂, ..., Xₙ) |

#### Solved Problem 1 ⭐

**Soal:** Identifikasi variabel, domain, dan constraint untuk masalah pewarnaan peta Indonesia bagian barat (Sumatera, Kalimantan, Jawa, Bali)!

**Penyelesaian:**

*Step 1:* Identifikasi variabel (pulau-pulau)
- X = {Sumatera, Kalimantan, Jawa, Bali}

*Step 2:* Tentukan domain (warna yang tersedia)
- D = {Merah, Hijau, Biru} untuk setiap variabel

*Step 3:* Identifikasi constraint berdasarkan kedekatan geografis
- Sumatera berseberangan dengan Kalimantan dan Jawa
- Kalimantan berseberangan dengan Jawa
- Jawa bertetangga dengan Bali

**Jawaban:**
- **Variabel:** X = {Sumatera, Kalimantan, Jawa, Bali}
- **Domain:** D_i = {Merah, Hijau, Biru} untuk semua i
- **Constraint:** 
  - C₁: Sumatera ≠ Kalimantan
  - C₂: Sumatera ≠ Jawa
  - C₃: Kalimantan ≠ Jawa
  - C₄: Jawa ≠ Bali

---

### 1.4 Constraint Graph

> **Constraint Graph** adalah representasi visual dari CSP di mana:
> - **Node** merepresentasikan variabel
> - **Edge** merepresentasikan constraint antara variabel

![Constraint Graph untuk Map Coloring Australia](images/p06-01-constraint-graph-australia.png)

*Gambar 6.1: Constraint graph untuk masalah pewarnaan peta Australia*

#### Solved Problem 2 ⭐

**Soal:** Gambarkan constraint graph untuk CSP Sudoku 4×4 (hanya untuk baris pertama)!

**Penyelesaian:**

*Step 1:* Identifikasi variabel untuk baris pertama
- X₁₁, X₁₂, X₁₃, X₁₄ (sel di baris 1, kolom 1-4)

*Step 2:* Identifikasi constraint
- Semua sel dalam satu baris harus berbeda (Alldiff)
- Setiap pasang sel dalam baris memiliki constraint ≠

*Step 3:* Gambarkan graph

```
Baris pertama Sudoku 4×4:
    X₁₁ ---- X₁₂
     | \  /  |
     |  \/   |
     |  /\   |
     | /  \  |
    X₁₃ ---- X₁₄
```

**Jawaban:** Constraint graph untuk baris pertama adalah **complete graph** K₄ karena setiap pasang variabel memiliki constraint (harus berbeda). Terdapat C(4,2) = 6 edge.

---

## 2. Contoh-Contoh CSP Klasik

### 2.1 Map Coloring Problem

> **Map Coloring Problem** adalah masalah mewarnai peta sehingga tidak ada dua wilayah bertetangga yang memiliki warna sama.

**Formulasi CSP:**
- **Variabel:** Setiap wilayah pada peta
- **Domain:** Warna yang tersedia (biasanya 3 warna cukup untuk peta planar)
- **Constraint:** Wilayah bertetangga ≠ warna sama

**Teorema Empat Warna:** Setiap peta planar dapat diwarnai dengan paling banyak 4 warna.

### 2.2 N-Queens Problem

> **N-Queens Problem** adalah masalah menempatkan N buah ratu pada papan catur N×N sehingga tidak ada dua ratu yang saling menyerang.

**Formulasi CSP:**
- **Variabel:** Q₁, Q₂, ..., Qₙ (satu ratu per kolom)
- **Domain:** {1, 2, ..., N} (baris yang mungkin)
- **Constraint:** 
  - Tidak ada dua ratu di baris yang sama: Qᵢ ≠ Qⱼ
  - Tidak ada dua ratu di diagonal yang sama: |Qᵢ - Qⱼ| ≠ |i - j|

![N-Queens Problem](images/p06-02-nqueens-problem.png)

*Gambar 6.2: Contoh solusi 4-Queens dan constraint-nya*

#### Solved Problem 3 ⭐

**Soal:** Untuk 4-Queens problem, periksa apakah assignment Q₁=2, Q₂=4, Q₃=1, Q₄=3 adalah solusi valid!

**Penyelesaian:**

*Step 1:* Periksa constraint baris (Qᵢ ≠ Qⱼ untuk semua i ≠ j)
- Q₁=2, Q₂=4, Q₃=1, Q₄=3
- Semua nilai berbeda ✓

*Step 2:* Periksa constraint diagonal (|Qᵢ - Qⱼ| ≠ |i - j|)
- |Q₁ - Q₂| = |2-4| = 2, |1-2| = 1 → 2 ≠ 1 ✓
- |Q₁ - Q₃| = |2-1| = 1, |1-3| = 2 → 1 ≠ 2 ✓
- |Q₁ - Q₄| = |2-3| = 1, |1-4| = 3 → 1 ≠ 3 ✓
- |Q₂ - Q₃| = |4-1| = 3, |2-3| = 1 → 3 ≠ 1 ✓
- |Q₂ - Q₄| = |4-3| = 1, |2-4| = 2 → 1 ≠ 2 ✓
- |Q₃ - Q₄| = |1-3| = 2, |3-4| = 1 → 2 ≠ 1 ✓

**Jawaban:** Ya, assignment Q₁=2, Q₂=4, Q₃=1, Q₄=3 adalah **solusi valid** karena memenuhi semua constraint baris dan diagonal.

---

### 2.3 Sudoku

> **Sudoku** adalah puzzle di mana papan 9×9 harus diisi dengan angka 1-9 sehingga setiap baris, kolom, dan kotak 3×3 berisi semua angka 1-9 tepat sekali.

**Formulasi CSP:**
- **Variabel:** 81 sel (X₁₁, X₁₂, ..., X₉₉)
- **Domain:** {1, 2, ..., 9} untuk sel kosong; singleton untuk sel yang sudah terisi
- **Constraint:**
  - Alldiff untuk setiap baris (9 constraint)
  - Alldiff untuk setiap kolom (9 constraint)
  - Alldiff untuk setiap kotak 3×3 (9 constraint)

**Jumlah total constraint:** 27 Alldiff constraint = 27 × C(9,2) = 27 × 36 = 972 binary constraint

#### Solved Problem 4 ⭐⭐

**Soal:** Berapa banyak binary constraint dalam Sudoku 4×4 (menggunakan angka 1-4)?

**Penyelesaian:**

*Step 1:* Identifikasi sumber constraint
- 4 baris, masing-masing dengan Alldiff
- 4 kolom, masing-masing dengan Alldiff
- 4 kotak 2×2, masing-masing dengan Alldiff

*Step 2:* Hitung binary constraint per Alldiff
- Alldiff(4 variabel) = C(4,2) = 6 binary constraint

*Step 3:* Hitung total
- Baris: 4 × 6 = 24
- Kolom: 4 × 6 = 24
- Kotak: 4 × 6 = 24
- Total kasar: 72

*Step 4:* Perhatikan duplikasi
Beberapa constraint dihitung dua kali (sel dalam kotak yang sama juga satu baris/kolom). Namun jika dihitung sebagai constraint unik, perlu analisis lebih detail.

**Jawaban:** Sudoku 4×4 memiliki sekitar **72 binary constraint** (dengan kemungkinan duplikasi untuk sel yang berbagi baris/kolom dan kotak yang sama).

---

### 2.4 Cryptarithmetic

> **Cryptarithmetic** adalah puzzle di mana huruf mewakili digit, dan harus ditemukan assignment sehingga operasi aritmatika benar.

**Contoh:** SEND + MORE = MONEY

**Formulasi CSP:**
- **Variabel:** S, E, N, D, M, O, R, Y, C₁, C₂, C₃, C₄ (carry)
- **Domain:** {0,1,...,9} untuk huruf; {0,1} untuk carry
- **Constraint:**
  - Alldiff(S, E, N, D, M, O, R, Y)
  - S ≠ 0, M ≠ 0 (leading digit tidak boleh 0)
  - D + E = Y + 10×C₁
  - N + R + C₁ = E + 10×C₂
  - E + O + C₂ = N + 10×C₃
  - S + M + C₃ = O + 10×C₄
  - C₄ = M

#### Solved Problem 5 ⭐⭐

**Soal:** Formulasikan CSP untuk puzzle TWO + TWO = FOUR!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- Huruf: T, W, O, F, U, R
- Carry: C₁, C₂, C₃

*Step 2:* Tentukan domain
- T, W, O, F, U, R ∈ {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
- C₁, C₂, C₃ ∈ {0, 1}

*Step 3:* Formulasikan constraint

**Jawaban:**
- **Variabel:** X = {T, W, O, F, U, R, C₁, C₂, C₃}
- **Domain:** Huruf: {0-9}, Carry: {0,1}
- **Constraint:**
  1. Alldiff(T, W, O, F, U, R)
  2. T ≠ 0 (leading digit)
  3. F ≠ 0 (leading digit)
  4. O + O = R + 10×C₁
  5. W + W + C₁ = U + 10×C₂
  6. T + T + C₂ = O + 10×C₃
  7. C₃ = F

---

### 2.5 Job Scheduling

> **Job Scheduling** adalah masalah menjadwalkan serangkaian pekerjaan dengan batasan waktu dan dependensi.

**Formulasi CSP:**
- **Variabel:** Waktu mulai setiap pekerjaan
- **Domain:** Slot waktu yang tersedia
- **Constraint:**
  - Precedence: Job A selesai sebelum Job B mulai
  - Resource: Tidak ada dua job menggunakan resource yang sama bersamaan
  - Deadline: Job selesai sebelum deadline

#### Solved Problem 6 ⭐⭐

**Soal:** Sebuah operasi militer memiliki 4 tahapan: Pengintaian (P), Pergerakan Pasukan (M), Serangan (S), dan Evakuasi (E). Setiap tahap memerlukan 2 jam. Constraint: P sebelum M, M sebelum S, S sebelum E. Waktu tersedia: 08:00-18:00. Formulasikan sebagai CSP!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- X = {P, M, S, E} (waktu mulai setiap tahap)

*Step 2:* Tentukan domain (dalam jam dari 08:00)
- Setiap variabel: {0, 2, 4, 6, 8} (mulai jam 08, 10, 12, 14, 16)
- Tahap terakhir harus selesai sebelum 18:00, jadi E ≤ 8 (mulai paling lambat 16:00)

*Step 3:* Formulasikan constraint

**Jawaban:**
- **Variabel:** X = {P, M, S, E} (waktu mulai dalam jam dari 08:00)
- **Domain:** D = {0, 2, 4, 6, 8} untuk semua variabel
- **Constraint:**
  1. P + 2 ≤ M (Pengintaian selesai sebelum Pergerakan)
  2. M + 2 ≤ S (Pergerakan selesai sebelum Serangan)
  3. S + 2 ≤ E (Serangan selesai sebelum Evakuasi)
  4. E + 2 ≤ 10 (Evakuasi selesai sebelum 18:00)

---

## 3. CSP sebagai Search Problem

### 3.1 State Space untuk CSP

CSP dapat dipandang sebagai masalah pencarian dengan:

| Komponen Search | Definisi untuk CSP |
|-----------------|-------------------|
| **Initial State** | Assignment kosong {} |
| **Successor Function** | Assign nilai ke variabel yang belum di-assign |
| **Goal Test** | Assignment lengkap dan semua constraint terpenuhi |
| **Path Cost** | Konstan (biasanya tidak relevan) |

### 3.2 Karakteristik Khusus CSP

> **Commutative Property:** Urutan assignment variabel tidak mempengaruhi hasil akhir. Ini memungkinkan kita memilih satu variabel pada setiap level pencarian.

Keuntungan CSP:
1. Dapat mendeteksi failure lebih awal (saat partial assignment melanggar constraint)
2. Dapat menggunakan struktur masalah untuk memangkas search space
3. Dapat menggunakan heuristic domain-independent

#### Solved Problem 7 ⭐

**Soal:** Untuk map coloring dengan 3 wilayah (A, B, C) dan 2 warna (Merah, Hijau), hitung total state dalam search tree jika menggunakan standard search vs CSP search!

**Penyelesaian:**

*Step 1:* Standard search (setiap state bisa assign variabel manapun)
- Branching factor = n × d (variabel × nilai)
- Sangat besar dan banyak duplikasi

*Step 2:* CSP search (satu variabel per level)
- Level 1: pilih nilai untuk A → 2 pilihan
- Level 2: pilih nilai untuk B → 2 pilihan
- Level 3: pilih nilai untuk C → 2 pilihan
- Total leaf nodes = 2 × 2 × 2 = 8

**Jawaban:** Dengan CSP search, total leaf node adalah **8** (2³). Standard search akan menghasilkan lebih banyak state karena duplikasi dan redundansi.

---

## 4. Constraint Propagation

### 4.1 Konsep Constraint Propagation

> **Constraint Propagation** adalah teknik untuk mengurangi domain variabel dengan memanfaatkan constraint, sehingga memperkecil search space sebelum atau selama pencarian.

Tujuan: Mendeteksi inconsistency sedini mungkin dan mengurangi nilai-nilai yang tidak mungkin dari domain.

### 4.2 Node Consistency

> **Node Consistency:** Variabel X node-consistent jika semua nilai dalam domain D_X memenuhi unary constraint pada X.

**Contoh:** Jika constraint X₁ ≠ Merah, maka hapus Merah dari domain X₁.

#### Solved Problem 8 ⭐

**Soal:** Diberikan CSP dengan X₁ memiliki domain {1,2,3,4,5} dan unary constraint X₁ > 2 dan X₁ ≤ 4. Terapkan node consistency!

**Penyelesaian:**

*Step 1:* Domain awal
- D(X₁) = {1, 2, 3, 4, 5}

*Step 2:* Terapkan constraint X₁ > 2
- Hapus nilai ≤ 2
- D(X₁) = {3, 4, 5}

*Step 3:* Terapkan constraint X₁ ≤ 4
- Hapus nilai > 4
- D(X₁) = {3, 4}

**Jawaban:** Setelah node consistency, D(X₁) = **{3, 4}**

---

### 4.3 Arc Consistency

> **Arc Consistency:** Variabel Xᵢ arc-consistent terhadap Xⱼ jika untuk setiap nilai dalam domain Xᵢ, terdapat nilai dalam domain Xⱼ yang memenuhi constraint antara Xᵢ dan Xⱼ.

**Definisi formal:**
- Arc (Xᵢ, Xⱼ) adalah consistent jika untuk setiap nilai x ∈ D(Xᵢ), terdapat nilai y ∈ D(Xⱼ) sehingga (x, y) memenuhi constraint C(Xᵢ, Xⱼ).

![Arc Consistency](images/p06-03-arc-consistency.png)

*Gambar 6.3: Ilustrasi arc consistency*

#### Solved Problem 9 ⭐⭐

**Soal:** Diberikan CSP dengan:
- X₁ dengan domain {1, 2, 3}
- X₂ dengan domain {1, 2}
- Constraint: X₁ < X₂

Terapkan arc consistency untuk arc (X₁, X₂) dan arc (X₂, X₁)!

**Penyelesaian:**

*Step 1:* Periksa arc (X₁, X₂)
- Untuk X₁ = 1: Apakah ada X₂ sehingga 1 < X₂? Ya, X₂ = 2. ✓
- Untuk X₁ = 2: Apakah ada X₂ sehingga 2 < X₂? Tidak ada di {1,2}. ✗
- Untuk X₁ = 3: Apakah ada X₂ sehingga 3 < X₂? Tidak ada. ✗
- Hapus 2 dan 3 dari D(X₁)
- D(X₁) = {1}

*Step 2:* Periksa arc (X₂, X₁)
- Untuk X₂ = 1: Apakah ada X₁ sehingga X₁ < 1? Tidak ada di {1}. ✗
- Untuk X₂ = 2: Apakah ada X₁ sehingga X₁ < 2? Ya, X₁ = 1. ✓
- Hapus 1 dari D(X₂)
- D(X₂) = {2}

**Jawaban:** Setelah arc consistency: D(X₁) = **{1}**, D(X₂) = **{2}**

---

### 4.4 Algoritma AC-3

> **AC-3 (Arc Consistency Algorithm #3)** adalah algoritma untuk mencapai arc consistency pada seluruh CSP.

**Pseudocode AC-3:**

```python
def AC3(csp):
    queue = [(Xi, Xj) for all arcs in csp]
    while queue is not empty:
        (Xi, Xj) = queue.pop()
        if REVISE(csp, Xi, Xj):
            if domain[Xi] is empty:
                return False  # Inconsistency detected
            for Xk in neighbors[Xi] - {Xj}:
                queue.add((Xk, Xi))
    return True

def REVISE(csp, Xi, Xj):
    revised = False
    for x in domain[Xi]:
        if no value y in domain[Xj] satisfies constraint(Xi, Xj):
            domain[Xi].remove(x)
            revised = True
    return revised
```

**Kompleksitas AC-3:**
- Time: O(ed³) di mana e = jumlah arc, d = ukuran domain maksimum
- Space: O(e)

#### Solved Problem 10 ⭐⭐⭐

**Soal:** Terapkan AC-3 pada CSP berikut:
- Variabel: A, B, C
- Domain: D(A) = D(B) = D(C) = {1, 2, 3}
- Constraint: A < B, B < C

**Penyelesaian:**

*Step 1:* Inisialisasi queue dengan semua arc
- Queue = [(A,B), (B,A), (B,C), (C,B)]

*Step 2:* Proses (A,B) dengan constraint A < B
- A=1: Ada B>1? Ya (2,3). Keep.
- A=2: Ada B>2? Ya (3). Keep.
- A=3: Ada B>3? Tidak. Remove.
- D(A) = {1, 2}
- Revised! Tambah (B,A) jika belum ada.

*Step 3:* Proses (B,A) dengan constraint A < B
- B=1: Ada A<1? Tidak. Remove.
- B=2: Ada A<2? Ya (1). Keep.
- B=3: Ada A<3? Ya (1,2). Keep.
- D(B) = {2, 3}
- Revised! Tambah (A,B), (C,B).

*Step 4:* Proses (B,C) dengan constraint B < C
- B=2: Ada C>2? Ya (3). Keep.
- B=3: Ada C>3? Tidak. Remove.
- D(B) = {2}
- Revised! Tambah (A,B), (C,B).

*Step 5:* Proses (C,B) dengan constraint B < C
- C=1: Ada B<1? Tidak. Remove.
- C=2: Ada B<2? Tidak (B={2}). Remove.
- C=3: Ada B<3? Ya (2). Keep.
- D(C) = {3}
- Revised! Tambah (B,C).

*Step 6:* Proses (A,B) dengan D(B) = {2}
- A=1: Ada B>1 di {2}? Ya. Keep.
- A=2: Ada B>2 di {2}? Tidak. Remove.
- D(A) = {1}
- Revised!

*Step 7:* Tidak ada lagi perubahan.

**Jawaban:** Setelah AC-3: D(A) = **{1}**, D(B) = **{2}**, D(C) = **{3}**

---

## 5. Backtracking Search untuk CSP

### 5.1 Algoritma Backtracking Dasar

> **Backtracking Search** adalah algoritma DFS yang memilih satu variabel pada setiap langkah dan melakukan backtrack ketika tidak ada nilai legal yang tersisa.

**Pseudocode:**

```python
def BACKTRACKING_SEARCH(csp):
    return BACKTRACK({}, csp)

def BACKTRACK(assignment, csp):
    if assignment is complete:
        return assignment
    var = SELECT_UNASSIGNED_VARIABLE(csp)
    for value in ORDER_DOMAIN_VALUES(var, assignment, csp):
        if value is consistent with assignment:
            assignment[var] = value
            result = BACKTRACK(assignment, csp)
            if result != failure:
                return result
            del assignment[var]
    return failure
```

### 5.2 Ilustrasi Backtracking

![Backtracking Search Tree](images/p06-04-backtracking-search.png)

*Gambar 6.4: Search tree untuk backtracking pada map coloring*

#### Solved Problem 11 ⭐⭐

**Soal:** Jalankan backtracking search untuk CSP map coloring sederhana dengan 3 wilayah (A, B, C), semua bertetangga, dan 3 warna (R, G, B)!

**Penyelesaian:**

*Step 1:* Mulai dengan assignment kosong {}
- Pilih variabel A
- Coba A = R

*Step 2:* Assignment = {A: R}
- Pilih variabel B
- Coba B = R → Konflik dengan A! Backtrack.
- Coba B = G → OK

*Step 3:* Assignment = {A: R, B: G}
- Pilih variabel C
- Coba C = R → Konflik dengan A! Backtrack.
- Coba C = G → Konflik dengan B! Backtrack.
- Coba C = B → OK

*Step 4:* Assignment = {A: R, B: G, C: B}
- Semua variabel ter-assign
- Periksa semua constraint: A≠B ✓, A≠C ✓, B≠C ✓

**Jawaban:** Solusi: **{A: R, B: G, C: B}** (atau permutasi lainnya)

---

## 6. Heuristik untuk Backtracking

### 6.1 Heuristik Pemilihan Variabel

#### 6.1.1 Minimum Remaining Values (MRV)

> **MRV (Fail-First Heuristic):** Pilih variabel dengan nilai legal tersisa paling sedikit.

Intuisi: Jika variabel ini akan menyebabkan failure, lebih baik menemukan failure lebih awal.

**Contoh:** 
- D(X₁) = {1, 2, 3, 4}
- D(X₂) = {1, 2}  ← Pilih X₂ (MRV = 2)
- D(X₃) = {1, 2, 3}

#### 6.1.2 Degree Heuristic

> **Degree Heuristic:** Pilih variabel yang terlibat dalam constraint paling banyak dengan variabel lain yang belum di-assign.

Digunakan sebagai tiebreaker untuk MRV.

#### Solved Problem 12 ⭐⭐

**Soal:** Diberikan CSP dengan domain:
- D(A) = {1, 2, 3}, degree = 2
- D(B) = {1, 2}, degree = 3
- D(C) = {1, 2}, degree = 1

Variabel mana yang dipilih pertama dengan MRV? Jika tie, gunakan degree heuristic!

**Penyelesaian:**

*Step 1:* Terapkan MRV
- |D(A)| = 3
- |D(B)| = 2
- |D(C)| = 2
- MRV terkecil: B dan C (tie)

*Step 2:* Terapkan degree heuristic untuk tiebreaker
- Degree(B) = 3
- Degree(C) = 1
- Pilih yang degree lebih tinggi: B

**Jawaban:** Pilih variabel **B** (MRV = 2, degree = 3)

---

### 6.2 Heuristik Pemilihan Nilai

#### Least Constraining Value (LCV)

> **LCV (Least Constraining Value):** Pilih nilai yang menghilangkan paling sedikit nilai dari domain variabel tetangga.

Intuisi: Memaksimalkan fleksibilitas untuk assignment selanjutnya.

![LCV Heuristic](images/p06-05-lcv-heuristic.png)

*Gambar 6.5: Ilustrasi Least Constraining Value heuristic*

#### Solved Problem 13 ⭐⭐

**Soal:** Variabel A memiliki domain {R, G, B}. Tetangga A adalah B dan C dengan:
- D(B) = {R, G}
- D(C) = {G, B}
- Constraint: A ≠ B dan A ≠ C

Nilai mana yang harus dipilih dengan LCV?

**Penyelesaian:**

*Step 1:* Hitung nilai yang dihilangkan jika A = R
- Dari D(B): hapus R → D(B) = {G} (hilang 1)
- Dari D(C): tidak ada R → D(C) = {G, B} (hilang 0)
- Total hilang: 1

*Step 2:* Hitung nilai yang dihilangkan jika A = G
- Dari D(B): hapus G → D(B) = {R} (hilang 1)
- Dari D(C): hapus G → D(C) = {B} (hilang 1)
- Total hilang: 2

*Step 3:* Hitung nilai yang dihilangkan jika A = B
- Dari D(B): tidak ada B → D(B) = {R, G} (hilang 0)
- Dari D(C): hapus B → D(C) = {G} (hilang 1)
- Total hilang: 1

*Step 4:* Pilih nilai dengan LCV terkecil
- R: 1, G: 2, B: 1
- Tie antara R dan B (pilih salah satu, misal R)

**Jawaban:** Pilih **A = R** atau **A = B** (keduanya adalah LCV dengan 1 nilai terhapus)

---

## 7. Forward Checking

### 7.1 Konsep Forward Checking

> **Forward Checking** adalah teknik yang menghapus nilai inkonsisten dari domain variabel yang belum di-assign segera setelah setiap assignment.

Keuntungan:
- Mendeteksi failure lebih awal (domain kosong)
- Mengurangi branching factor

**Pseudocode:**

```python
def BACKTRACK_FC(assignment, csp):
    if assignment is complete:
        return assignment
    var = SELECT_UNASSIGNED_VARIABLE(csp)
    for value in ORDER_DOMAIN_VALUES(var, assignment, csp):
        if value is consistent with assignment:
            assignment[var] = value
            # Forward Checking
            saved_domains = copy(domains)
            if FORWARD_CHECK(var, value, csp):
                result = BACKTRACK_FC(assignment, csp)
                if result != failure:
                    return result
            domains = saved_domains  # Restore domains
            del assignment[var]
    return failure

def FORWARD_CHECK(var, value, csp):
    for neighbor in neighbors[var]:
        if neighbor not in assignment:
            for v in domain[neighbor]:
                if not consistent(var=value, neighbor=v):
                    domain[neighbor].remove(v)
            if domain[neighbor] is empty:
                return False
    return True
```

### 7.2 Ilustrasi Forward Checking

![Forward Checking](images/p06-06-forward-checking.png)

*Gambar 6.6: Forward checking pada map coloring*

#### Solved Problem 14 ⭐⭐⭐

**Soal:** Terapkan forward checking pada map coloring Australia dengan urutan: WA, Q, V, NSW, SA, NT, T. Asumsikan 3 warna {R, G, B}.

**Penyelesaian:**

*Step 1:* Initial domains
```
WA={R,G,B}, NT={R,G,B}, SA={R,G,B}, 
Q={R,G,B}, NSW={R,G,B}, V={R,G,B}, T={R,G,B}
```

*Step 2:* Assign WA = R
- Forward check neighbors: NT, SA
- D(NT) = {G, B} (hapus R)
- D(SA) = {G, B} (hapus R)

*Step 3:* Assign Q = G
- Forward check neighbors: NT, SA, NSW
- D(NT) = {B} (hapus G dari {G,B})
- D(SA) = {B} (hapus G dari {G,B})
- D(NSW) = {R, B} (hapus G)

*Step 4:* Assign V = R
- Forward check neighbors: SA, NSW
- D(SA) = {B} (tetap, R sudah tidak ada)
- D(NSW) = {B} (hapus R dari {R,B})

*Step 5:* Assign NSW = B
- Forward check neighbors: SA
- D(SA) = {} (hapus B dari {B})
- **Domain kosong! Failure!**

*Step 6:* Backtrack ke V, coba V = B
- D(SA) = {B} → tetap {B}
- D(NSW) = {R} (hapus B dari {R,B})

*Step 7:* Assign NSW = R
- D(SA) = {B} → tetap (tidak bertetangga dengan NSW via constraint yang relevan? Perlu cek ulang...)

**Jawaban:** Dengan forward checking, failure terdeteksi lebih awal di Step 5 ketika D(SA) menjadi kosong. Algoritma kemudian backtrack dan mencoba nilai berbeda untuk V.

---

#### Solved Problem 15 ⭐⭐

**Soal:** Bandingkan jumlah node yang dieksplorasi antara backtracking biasa dan forward checking untuk 4-Queens problem!

**Penyelesaian:**

*Step 1:* Analisis backtracking biasa
- Setiap level mencoba semua 4 posisi
- Failure terdeteksi hanya saat constraint dilanggar
- Worst case: 4⁴ = 256 leaf nodes
- Actual (dengan pruning langsung): masih banyak karena tidak ada look-ahead

*Step 2:* Analisis dengan forward checking
- Setelah menempatkan Q₁, domain Q₂, Q₃, Q₄ dikurangi
- Jika ada domain kosong, langsung backtrack
- Failure terdeteksi lebih awal
- Typical: jauh lebih sedikit nodes

**Jawaban:** 
- **Backtracking biasa:** ~262 nodes (dengan consistency check setiap level)
- **Forward checking:** ~24 nodes (estimasi)

Forward checking mengurangi node yang dieksplorasi secara signifikan dengan deteksi failure lebih awal.

---

## 8. Struktur Masalah dalam CSP

### 8.1 CSP dengan Struktur Tree

> **Tree-structured CSP:** CSP di mana constraint graph membentuk tree (tidak ada cycle).

Tree-structured CSP dapat diselesaikan dalam waktu **O(nd²)** dengan algoritma khusus.

**Algoritma untuk Tree-structured CSP:**
1. Pilih root variabel
2. Lakukan topological sort
3. Terapkan arc consistency dari leaf ke root
4. Assign nilai dari root ke leaf

#### Solved Problem 16 ⭐⭐

**Soal:** Diberikan tree-structured CSP:
```
    A
   / \
  B   C
 /
D
```
Dengan domain D(A)={1,2}, D(B)={1,2}, D(C)={1,2}, D(D)={1,2} dan constraint A≠B, A≠C, B≠D. Selesaikan menggunakan algoritma tree CSP!

**Penyelesaian:**

*Step 1:* Topological order dari leaf ke root
- D, B, C, A (atau D, C, B, A)

*Step 2:* Arc consistency dari leaf ke root
- Arc (D,B): D=1→B∈{2}, D=2→B∈{1}. OK.
- Arc (B,A): B=1→A∈{2}, B=2→A∈{1}. OK.
- Arc (C,A): C=1→A∈{2}, C=2→A∈{1}. OK.

*Step 3:* Assign dari root ke leaf
- A: Pilih A=1
- B: A=1, constraint A≠B, jadi B=2
- C: A=1, constraint A≠C, jadi C=2
- D: B=2, constraint B≠D, jadi D=1

**Jawaban:** Solusi: **{A=1, B=2, C=2, D=1}**

---

### 8.2 Cutset Conditioning

> **Cutset:** Himpunan variabel yang jika dihapus akan menghasilkan tree structure.

> **Cycle Cutset:** Himpunan minimum variabel untuk membuat graph menjadi tree.

Jika cycle cutset berukuran c, kompleksitas: O(d^c × (n-c)d²)

#### Solved Problem 17 ⭐⭐⭐

**Soal:** Untuk constraint graph berikut, identifikasi cycle cutset minimum!
```
A --- B
|  X  |
C --- D
```

**Penyelesaian:**

*Step 1:* Identifikasi cycle
- A-B-D-C-A adalah cycle
- A-D juga membentuk diagonal

*Step 2:* Coba menghapus satu variabel
- Hapus A: B-D-C masih terhubung, tapi linear (tree). ✓
- Hapus B: A-C-D dengan A-D diagonal. Masih cycle (A-D-C-A). ✗

*Step 3:* Verifikasi
- Menghapus A atau D (vertex diagonal) akan menghasilkan tree

**Jawaban:** Cycle cutset minimum adalah **{A}** atau **{D}** (ukuran 1)

---

## 9. Aplikasi CSP dalam Konteks Pertahanan

### 9.1 Resource Allocation untuk Operasi Militer

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Komando Operasi harus mengalokasikan 4 tim khusus (Alpha, Bravo, Charlie, Delta) ke 4 sektor (S1, S2, S3, S4) dengan constraint:
- Setiap tim ditugaskan ke tepat satu sektor
- Setiap sektor hanya boleh satu tim
- Alpha tidak boleh ke S1 (risiko tinggi, personel belum berpengalaman)
- Bravo harus adjacent dengan Charlie (sektor berurutan untuk koordinasi)
- Delta tidak boleh ke S4 (butuh di reserve)

Formulasikan sebagai CSP dan selesaikan!

**Penyelesaian:**

*Step 1:* Identifikasi variabel dan domain
- Variabel: {Alpha, Bravo, Charlie, Delta}
- Domain awal: {S1, S2, S3, S4} untuk semua

*Step 2:* Terapkan node consistency (unary constraint)
- D(Alpha) = {S2, S3, S4} (bukan S1)
- D(Delta) = {S1, S2, S3} (bukan S4)

*Step 3:* Formulasikan binary constraint
- Alldiff(Alpha, Bravo, Charlie, Delta)
- |Bravo - Charlie| = 1 (adjacent sectors)

*Step 4:* Selesaikan dengan backtracking + forward checking

**Coba Bravo = S2:**
- Charlie harus adjacent → D(Charlie) = {S1, S3}
- Forward check: Alpha dan Delta tidak bisa S2

**Coba Charlie = S1:**
- Alpha tidak bisa S1 → OK (sudah dihapus)
- Delta bisa S1? → OK
- Tapi Alldiff: jika Charlie=S1, Delta tidak bisa S1
- D(Alpha) = {S3, S4}, D(Delta) = {S3}

**Coba Delta = S3:**
- D(Alpha) = {S4}
- Alpha = S4

**Verifikasi:** Bravo=S2, Charlie=S1, Delta=S3, Alpha=S4
- Alpha tidak di S1 ✓
- |Bravo-Charlie| = |2-1| = 1 ✓
- Delta tidak di S4 ✓
- Alldiff ✓

**Jawaban:** Solusi: **{Alpha: S4, Bravo: S2, Charlie: S1, Delta: S3}**

---

### 9.2 Jadwal Patroli

#### Solved Problem 19 ⭐⭐

**Soal:** Buat jadwal patroli untuk 3 shift (Pagi, Siang, Malam) selama 2 hari dengan 6 personel (P1-P6). Constraint:
- Setiap shift butuh 2 personel
- Tidak ada personel yang bekerja 2 shift berturutan
- P1 dan P2 tidak boleh satu shift (konflik personal)

Formulasikan sebagai CSP!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- Shift: Pagi1, Siang1, Malam1, Pagi2, Siang2, Malam2
- Untuk setiap shift, butuh 2 variabel assignment
- Total: 12 variabel (Shift1_personel1, Shift1_personel2, ...)

Alternatif: Variabel per personel
- Variabel: P1, P2, P3, P4, P5, P6
- Domain: kombinasi 2 shift dari 6 shift yang tersedia

*Step 2:* Simplifikasi - gunakan pendekatan assignment

**Variabel:** X_s,i = personel ke-i untuk shift s (6 shift × 2 slot = 12 variabel)

**Domain:** {P1, P2, P3, P4, P5, P6}

**Constraint:**
1. Alldiff untuk setiap shift: X_s,1 ≠ X_s,2
2. Consecutive shift: Jika X melakukan Malam, tidak boleh Pagi berikutnya
3. P1 dan P2 tidak boleh di shift yang sama

**Jawaban:** CSP dengan 12 variabel, domain {P1-P6}, dan constraint berupa Alldiff per shift, anti-consecutive, dan separation constraint untuk P1/P2.

---

### 9.3 Frequency Assignment untuk Komunikasi

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Enam pos komunikasi (K1-K6) perlu dialokasikan frekuensi dari {F1, F2, F3}. Pos yang jaraknya < 10 km tidak boleh menggunakan frekuensi sama (interference). Jarak antar pos:
- K1-K2: 5km, K1-K3: 15km, K1-K4: 8km
- K2-K3: 7km, K2-K4: 12km
- K3-K4: 6km, K3-K5: 9km
- K4-K5: 5km, K4-K6: 11km
- K5-K6: 8km

Selesaikan dengan CSP!

**Penyelesaian:**

*Step 1:* Identifikasi constraint (jarak < 10km)
- K1 ≠ K2 (5km)
- K1 ≠ K4 (8km)
- K2 ≠ K3 (7km)
- K3 ≠ K4 (6km)
- K3 ≠ K5 (9km)
- K4 ≠ K5 (5km)
- K5 ≠ K6 (8km)

*Step 2:* Gambar constraint graph
```
K1 --- K2 --- K3 --- K5 --- K6
 \           /  \   /
  --- K4 -------
```

*Step 3:* Selesaikan dengan backtracking + MRV

**Iterasi:**
- K1 = F1
- K2 ≠ K1 → K2 = F2
- K3 ≠ K2 → K3 = F1 atau F3
- K3 = F1 (pilih)
- K4 ≠ K1, K3 → K4 = F2 atau F3 (K4 ≠ F1)
- K4 = F2 (pilih)
- K5 ≠ K3, K4 → K5 ≠ F1, F2 → K5 = F3
- K6 ≠ K5 → K6 ≠ F3 → K6 = F1 atau F2
- K6 = F1 (pilih)

**Jawaban:** **{K1:F1, K2:F2, K3:F1, K4:F2, K5:F3, K6:F1}**

---

#### Solved Problem 21 ⭐

**Soal:** Jelaskan mengapa CSP lebih cocok untuk masalah frequency assignment dibanding standard search!

**Penyelesaian:**

*Step 1:* Analisis karakteristik masalah
- Masalah memiliki struktur constraint yang jelas
- Banyak solusi yang feasible (tidak perlu optimal)
- Domain terbatas (jumlah frekuensi terbatas)

*Step 2:* Keuntungan CSP
1. **Constraint propagation** dapat mengurangi domain lebih awal
2. **Heuristic domain-independent** (MRV, LCV) dapat digunakan
3. **Deteksi failure lebih awal** dengan forward checking
4. **Struktur masalah** dapat dieksploitasi (jika graph sparse)

**Jawaban:** CSP lebih cocok karena:
1. Mengeksploitasi struktur constraint untuk pruning
2. Domain-independent heuristics tersedia
3. Constraint propagation mengurangi search space secara signifikan
4. Tidak perlu mencari solusi optimal, hanya feasible

---

#### Solved Problem 22 ⭐⭐

**Soal:** Implementasikan pseudocode untuk simple backtracking CSP solver dalam Python-style!

**Penyelesaian:**

```python
def solve_csp(variables, domains, constraints):
    """
    Main CSP solver function
    """
    assignment = {}
    return backtrack(assignment, variables, domains, constraints)

def backtrack(assignment, variables, domains, constraints):
    # Base case: all variables assigned
    if len(assignment) == len(variables):
        return assignment
    
    # Select unassigned variable (MRV heuristic)
    var = select_mrv(variables, assignment, domains)
    
    # Try each value in domain (LCV ordering)
    for value in order_lcv(var, domains, constraints):
        if is_consistent(var, value, assignment, constraints):
            # Assign value
            assignment[var] = value
            
            # Forward checking
            saved = copy_domains(domains)
            if forward_check(var, value, domains, constraints):
                result = backtrack(assignment, variables, domains, constraints)
                if result is not None:
                    return result
            
            # Restore and backtrack
            restore_domains(domains, saved)
            del assignment[var]
    
    return None  # Failure

def is_consistent(var, value, assignment, constraints):
    """Check if assigning value to var is consistent with current assignment"""
    for constraint in constraints:
        if var in constraint.variables:
            if not constraint.is_satisfied(assignment, var, value):
                return False
    return True

def forward_check(var, value, domains, constraints):
    """Remove inconsistent values from unassigned neighbors"""
    for neighbor in get_neighbors(var, constraints):
        if neighbor not in assignment:
            for v in list(domains[neighbor]):
                if not is_consistent_pair(var, value, neighbor, v, constraints):
                    domains[neighbor].remove(v)
            if len(domains[neighbor]) == 0:
                return False
    return True
```

**Jawaban:** Pseudocode di atas mengimplementasikan backtracking dengan MRV, LCV, dan forward checking untuk CSP solver yang efisien.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Berapa minimum warna yang dibutuhkan untuk mewarnai graph complete K₅?

**Jawaban:** Untuk complete graph Kₙ, diperlukan n warna karena setiap node bertetangga dengan semua node lain. Jadi untuk K₅, dibutuhkan **5 warna**.

---

### Problem S2 ⭐⭐
**Soal:** Apa perbedaan antara node consistency dan arc consistency?

**Jawaban:**
- **Node consistency:** Menghapus nilai dari domain satu variabel yang melanggar unary constraint
- **Arc consistency:** Menghapus nilai dari domain satu variabel yang tidak memiliki "support" di variabel tetangga untuk binary constraint

---

### Problem S3 ⭐⭐
**Soal:** Mengapa MRV disebut "fail-first heuristic"?

**Jawaban:** MRV memilih variabel dengan domain terkecil, yang paling mungkin menyebabkan failure. Dengan mencoba variabel ini lebih dulu, kita menemukan failure lebih awal di search tree, mengurangi backtracking yang tidak perlu.

---

### Problem S4 ⭐⭐
**Soal:** Kapan forward checking tidak cukup efektif?

**Jawaban:** Forward checking hanya melihat satu langkah ke depan (constraint langsung). Tidak mendeteksi inconsistency yang muncul dari interaksi antara variabel yang belum di-assign. AC-3 atau MAC (Maintaining Arc Consistency) lebih kuat dalam kasus ini.

---

### Problem S5 ⭐⭐⭐
**Soal:** Jelaskan kompleksitas waktu AC-3 dan mengapa!

**Jawaban:** Kompleksitas AC-3 adalah **O(ed³)** dimana e = jumlah edge (constraint), d = ukuran domain maksimum.
- Setiap arc (Xi, Xj) bisa dimasukkan ke queue O(d) kali (setiap kali domain Xi berkurang)
- Setiap pemeriksaan arc memerlukan O(d²) untuk memeriksa semua pasangan nilai
- Total: O(e × d × d²) = O(ed³)

---

## Ringkasan

| Konsep | Deskripsi |
|--------|-----------|
| **CSP** | Problem dengan variabel, domain, dan constraint |
| **Constraint Graph** | Graph dengan node=variabel, edge=constraint |
| **Node Consistency** | Semua nilai di domain memenuhi unary constraint |
| **Arc Consistency** | Setiap nilai memiliki support di variabel tetangga |
| **AC-3** | Algoritma untuk mencapai arc consistency, O(ed³) |
| **Backtracking** | DFS dengan satu variabel per level |
| **MRV** | Pilih variabel dengan domain terkecil |
| **Degree Heuristic** | Pilih variabel dengan constraint terbanyak |
| **LCV** | Pilih nilai yang menghilangkan paling sedikit opsi |
| **Forward Checking** | Hapus nilai inkonsisten setelah setiap assignment |
| **Tree-structured CSP** | Dapat diselesaikan dalam O(nd²) |
| **Cutset Conditioning** | Hapus variabel untuk membuat tree |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 6**.
2. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press. **Chapter 4**.
3. CS188 Berkeley AI Materials: https://inst.eecs.berkeley.edu/~cs188/

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
