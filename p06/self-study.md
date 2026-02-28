# Panduan Belajar Mandiri Pertemuan 06: Constraint Satisfaction Problems (CSP)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 06  
**Topik:** Constraint Satisfaction Problems (CSP)  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Mendefinisikan komponen CSP (variabel, domain, constraint)
2. Memformulasikan masalah nyata sebagai CSP
3. Menerapkan constraint propagation (node consistency, arc consistency)
4. Mengimplementasikan backtracking search dengan heuristik
5. Menjelaskan forward checking dan maintaining arc consistency

---

## 1. Review Konsep: Definisi dan Komponen CSP (45 menit)

### Ringkasan Materi

> **Constraint Satisfaction Problem (CSP)** adalah masalah yang didefinisikan oleh variabel, domain nilai, dan constraint yang membatasi kombinasi nilai yang diperbolehkan.

**Komponen CSP:**
- **X** = {X₁, X₂, ..., Xₙ} — himpunan variabel
- **D** = {D₁, D₂, ..., Dₙ} — domain untuk setiap variabel
- **C** = {C₁, C₂, ..., Cₘ} — himpunan constraint

| Komponen | Definisi | Contoh (Sudoku) |
|----------|----------|-----------------|
| **Variabel (X)** | Entitas yang diberi nilai | 81 cell dalam grid 9×9 |
| **Domain (D)** | Nilai yang mungkin | {1, 2, 3, 4, 5, 6, 7, 8, 9} |
| **Constraint (C)** | Batasan yang dipenuhi | Semua cell dalam row/column/box berbeda |

**Jenis-Jenis Constraint:**

| Jenis | Definisi | Contoh |
|-------|----------|--------|
| **Unary** | 1 variabel | X₁ ≠ 5 |
| **Binary** | 2 variabel | X₁ ≠ X₂ |
| **Higher-order** | > 2 variabel | AllDifferent(X₁, X₂, X₃) |
| **Global** | Constraint khusus | AllDifferent, Sum |

**Solusi CSP:**
- **Complete assignment:** Semua variabel memiliki nilai
- **Consistent assignment:** Tidak ada constraint dilanggar
- **Solution:** Complete + Consistent

![CSP Components](images/ss06-01-csp-components.png)

*Gambar 1.1: Komponen utama Constraint Satisfaction Problem*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram komponen CSP dengan contoh Map Coloring Australia
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Dua bagian - kiri komponen abstrak, kanan contoh konkret
WARNA:
- Variabel: #2563eb (biru)
- Domain: #10b981 (hijau)
- Constraint: #ef4444 (merah)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Kiri: Kotak "Variabel X", "Domain D", "Constraint C"
2. Kanan: Peta Australia dengan wilayah diberi warna
3. Label menunjukkan X={WA, NT, SA, Q, NSW, V, T}
4. Domain = {Merah, Hijau, Biru}
5. Constraint: wilayah bertetangga berbeda warna
LABEL: "Variables", "Domains", "Constraints", nama wilayah
UKURAN: 900x500 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Introduction to CSP | MIT OCW | 20:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |
| 2 | CSP Overview | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=FhC_TyXE8sQ |
| 3 | Constraint Programming | Google Developers | 10:00 | https://www.youtube.com/watch?v=5sFhRVpxqH4 |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Sudoku | Web Sudoku | Selesaikan Sudoku sebagai CSP | https://www.websudoku.com/ |
| Map Coloring | MathIsFun | Game pewarnaan peta | https://www.mathsisfun.com/games/geography-game.html |

### ✍️ Latihan Pemahaman

1. Apa tiga komponen utama CSP?
2. Sebutkan perbedaan unary dan binary constraint!
3. Apa yang dimaksud dengan "consistent assignment"?

---

## 2. Review Konsep: Formulasi CSP untuk Masalah Klasik (45 menit)

### Ringkasan Materi

**Contoh 1: Map Coloring Australia**

| Komponen | Spesifikasi |
|----------|-------------|
| **Variabel** | X = {WA, NT, SA, Q, NSW, V, T} |
| **Domain** | D = {Red, Green, Blue} untuk semua |
| **Constraint** | WA≠NT, WA≠SA, NT≠SA, NT≠Q, SA≠Q, SA≠NSW, SA≠V, Q≠NSW, NSW≠V |

**Contoh 2: N-Queens Problem**

| Komponen | Spesifikasi |
|----------|-------------|
| **Variabel** | X = {Q₁, Q₂, ..., Qₙ} — posisi queen di kolom i |
| **Domain** | D = {1, 2, ..., n} — row number |
| **Constraint** | Qᵢ ≠ Qⱼ (row berbeda), \|Qᵢ - Qⱼ\| ≠ \|i - j\| (diagonal berbeda) |

**Contoh 3: Sudoku**

| Komponen | Spesifikasi |
|----------|-------------|
| **Variabel** | X = 81 cell dalam grid 9×9 |
| **Domain** | D = {1-9}, reduced jika ada nilai awal |
| **Constraint** | AllDifferent untuk setiap row, column, dan 3×3 box |

**Constraint Graph:**
Graph di mana node = variabel, edge = constraint antara dua variabel.

![CSP Examples](images/ss06-02-csp-examples.png)

*Gambar 2.1: Contoh CSP: Map Coloring, N-Queens, Sudoku*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Tiga contoh CSP klasik: Map Coloring, N-Queens, Sudoku
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tiga panel horizontal
WARNA:
- Map: wilayah dengan warna merah, hijau, biru
- N-Queens: papan catur hitam-putih dengan queen
- Sudoku: grid dengan angka
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Panel 1: Peta Australia dengan pewarnaan valid
2. Panel 2: Papan 8x8 dengan 8 queens tidak saling menyerang
3. Panel 3: Grid Sudoku 9x9 sebagian terisi
LABEL: "Map Coloring", "N-Queens", "Sudoku"
UKURAN: 1000x400 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Map Coloring CSP | AI Course | 10:00 | https://www.youtube.com/watch?v=vvpA0Mz4BuA |
| 2 | Sudoku as CSP | Computerphile | 12:00 | https://www.youtube.com/watch?v=G_UYXzGuqvM |
| 3 | N-Queens Problem | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=xFv_Hl4B83A |

### ✍️ Latihan Pemahaman

1. Formulasikan 4-Queens sebagai CSP lengkap!
2. Berapa jumlah constraint binary untuk Map Coloring Australia?
3. Gambarkan constraint graph untuk Map Coloring dengan 4 wilayah!

---

## 3. Review Konsep: Backtracking Search untuk CSP (45 menit)

### Ringkasan Materi

**CSP sebagai Search Problem:**

| Komponen | Definisi |
|----------|----------|
| **Initial state** | Assignment kosong {} |
| **Actions** | Assign nilai ke variabel unassigned |
| **Goal test** | Complete dan consistent |

**Backtracking Search:**
DFS yang memilih nilai untuk satu variabel pada satu waktu dan backtrack ketika constraint dilanggar.

**Pseudocode:**
```
function BacktrackingSearch(csp):
    return Backtrack({}, csp)

function Backtrack(assignment, csp):
    if assignment is complete:
        return assignment
    
    var = SelectUnassignedVariable(csp, assignment)
    
    for each value in OrderDomainValues(var, assignment, csp):
        if value is consistent with assignment:
            assignment[var] = value
            result = Backtrack(assignment, csp)
            if result ≠ failure:
                return result
            remove assignment[var]
    
    return failure
```

**Kelebihan Backtracking vs Generate-and-Test:**
- Deteksi konflik lebih awal
- Tidak generate semua kemungkinan
- Sudoku: 9^81 → jauh lebih kecil dengan backtracking

![Backtracking CSP](images/ss06-03-backtracking-csp.png)

*Gambar 3.1: Ilustrasi Backtracking Search untuk Map Coloring*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Search tree Backtracking untuk CSP Map Coloring sederhana
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tree vertikal dengan root di atas
WARNA:
- Node sukses: #10b981 (hijau)
- Node gagal: #ef4444 (merah) dengan X
- Node exploring: #2563eb (biru)
- Path backtrack: #f59e0b (oranye) putus-putus
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Root: {} kosong
2. Level 1: A=R, A=G, A=B
3. Level 2: B=R (X), B=G, B=B
4. Path sukses ditandai hijau
5. Path gagal ditandai merah dengan "Backtrack!"
LABEL: "Backtracking Search", "Success", "Failure - Backtrack"
UKURAN: 900x700 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Backtracking for CSP | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=Zq4upTEaQyM |
| 2 | CSP Backtracking | AI Course | 12:00 | https://www.youtube.com/watch?v=708ZL5L3VD8 |
| 3 | Sudoku Solver | Computerphile | 10:00 | https://www.youtube.com/watch?v=G_UYXzGuqvM |

### ✍️ Latihan Pemahaman

1. Mengapa backtracking lebih efisien daripada generate-and-test?
2. Trace backtracking untuk 3-variable CSP dengan domain {1,2} dan constraint X₁≠X₂, X₂≠X₃!
3. Kapan backtracking akan melakukan backtrack?

---

## 4. Review Konsep: Constraint Propagation (45 menit)

### Ringkasan Materi

> **Constraint Propagation** mengurangi domain variabel dengan menggunakan constraint, sebelum atau selama pencarian.

**Tujuan:**
- Mengurangi search space
- Deteksi inkonsistensi lebih awal
- Kadang solve tanpa search!

**Node Consistency:**
Setiap nilai dalam domain memenuhi unary constraint.

**Arc Consistency:**
> Variabel Xᵢ arc-consistent terhadap Xⱼ jika untuk setiap nilai di Dᵢ, ada nilai di Dⱼ yang memenuhi constraint antara Xᵢ dan Xⱼ.

**Algoritma AC-3:**
```
function AC-3(csp):
    queue = all arcs in csp
    while queue is not empty:
        (Xi, Xj) = queue.pop()
        if REVISE(csp, Xi, Xj):
            if Di is empty: return false
            for each Xk in neighbors(Xi) - {Xj}:
                add (Xk, Xi) to queue
    return true

function REVISE(csp, Xi, Xj):
    revised = false
    for each x in Di:
        if no y in Dj satisfies constraint(Xi, Xj):
            delete x from Di
            revised = true
    return revised
```

![Arc Consistency](images/ss06-04-arc-consistency.png)

*Gambar 4.1: Proses Arc Consistency dengan AC-3*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram Arc Consistency menunjukkan proses REVISE dan AC-3
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Dua bagian - sebelum dan sesudah AC-3
WARNA:
- Domain awal: #2563eb (biru)
- Domain setelah pruning: #10b981 (hijau)
- Nilai yang dihapus: #ef4444 (merah) dengan strikethrough
- Arc: #6b7280 (abu-abu)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Kiri: Tiga variabel X, Y, Z dengan domain penuh
2. Panah arc antara variabel dengan constraint
3. Kanan: Domain yang sudah di-prune
4. Nilai yang dihapus ditandai coret
LABEL: "Before AC-3", "After AC-3", "Pruned values"
UKURAN: 900x500 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Kompleksitas AC-3:**
- Time: O(cd³) dimana c = constraints, d = domain size
- Space: O(n²) untuk queue

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Arc Consistency | AI Course | 15:00 | https://www.youtube.com/watch?v=4cCS8rrYT14 |
| 2 | AC-3 Algorithm | Abdul Bari | 12:00 | https://www.youtube.com/watch?v=FhC_TyXE8sQ |
| 3 | Constraint Propagation | MIT OCW | 20:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |

### ✍️ Latihan Pemahaman

1. Apa perbedaan node consistency dan arc consistency?
2. Trace AC-3 untuk X, Y dengan D={1,2,3} dan constraint X < Y!
3. Kapan AC-3 mengembalikan false?

---

## 5. Review Konsep: Heuristik untuk CSP (45 menit)

### Ringkasan Materi

**Heuristik Pemilihan Variabel:**

| Heuristik | Strategi | Tujuan |
|-----------|----------|--------|
| **MRV** | Pilih variabel dengan domain terkecil | Fail-first: deteksi masalah lebih awal |
| **Degree** | Pilih variabel dengan constraint terbanyak | Prioritaskan variabel yang mempengaruhi banyak |
| **Tie-breaker** | Gunakan Degree jika MRV sama | Kombinasi MRV + Degree |

**Heuristik Pemilihan Nilai:**

| Heuristik | Strategi | Tujuan |
|-----------|----------|--------|
| **LCV** | Pilih nilai yang mengurangi domain neighbor paling sedikit | Succeed-first: maksimalkan peluang sukses |

**Forward Checking:**
Setelah assign variabel, hapus nilai inconsistent dari domain neighbor.

**Maintaining Arc Consistency (MAC):**
Setelah assign, jalankan AC-3 pada neighbor.

![CSP Heuristics](images/ss06-05-csp-heuristics.png)

*Gambar 5.1: Ilustrasi MRV dan LCV heuristics*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram menunjukkan heuristik MRV dan LCV untuk CSP
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Dua panel - MRV di atas, LCV di bawah
WARNA:
- Variabel terpilih: #2563eb (biru) highlight
- Domain: #10b981 (hijau)
- Constraint: garis #6b7280 (abu-abu)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Panel MRV: Tiga variabel dengan domain berbeda ukuran, yang terkecil di-highlight
2. Panel LCV: Satu variabel dengan opsi nilai, menunjukkan dampak ke neighbor
3. Label menjelaskan pilihan
LABEL: "MRV: Choose smallest domain", "LCV: Choose least constraining value"
UKURAN: 900x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Perbandingan Teknik:**

| Teknik | Kapan Dipanggil | Overhead | Pruning Power |
|--------|-----------------|----------|---------------|
| **No propagation** | Never | O(1) | None |
| **Forward Checking** | After assignment | O(nd) | Medium |
| **MAC (AC-3)** | After assignment | O(cd³) | High |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | CSP Heuristics | CS188 Berkeley | 15:00 | https://www.youtube.com/watch?v=UhAmM3z6KS0 |
| 2 | MRV and LCV | AI Course | 10:00 | https://www.youtube.com/watch?v=DhsCsNFFRWY |
| 3 | Forward Checking | Abdul Bari | 12:00 | https://www.youtube.com/watch?v=FhC_TyXE8sQ |

### ✍️ Latihan Pemahaman

1. Mengapa MRV disebut "fail-first"?
2. Kapan menggunakan LCV vs random value selection?
3. Apa perbedaan Forward Checking dan MAC?

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Kegunaan | Link |
|------|----------|------|
| CSP Visualizer | Trace AC-3 dan Backtracking | https://algorithm-visualizer.org/ |
| Google OR-Tools | Library CSP untuk Python | https://developers.google.com/optimization |
| MiniZinc | Constraint modeling language | https://www.minizinc.org/ |
| Sudoku Solver | Lihat CSP solve Sudoku | https://www.sudoku-solutions.com/ |

### Tugas Eksplorasi

1. Buka **Sudoku Solver** dan perhatikan bagaimana constraint propagation bekerja
2. Install **OR-Tools** dan coba selesaikan N-Queens
3. Visualisasikan **AC-3** untuk Map Coloring sederhana
4. Refleksikan: Bagaimana CSP dapat digunakan untuk scheduling militer?

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | CSP Complete Lecture | MIT OCW | 50:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |
| 2 | Constraint Programming | Google Developers | 30:00 | https://www.youtube.com/watch?v=5sFhRVpxqH4 |
| 3 | Sudoku AI | Computerphile | 15:00 | https://www.youtube.com/watch?v=G_UYXzGuqvM |
| 4 | SAT Solvers | Computerphile | 20:00 | https://www.youtube.com/watch?v=d76e4hV1iJY |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 6 (Constraint Satisfaction Problems)
- Tutorial: Google OR-Tools Documentation
- Paper: "Maintaining Arc Consistency" - Mackworth (1977)

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| CS188 Practice | CSP | https://inst.eecs.berkeley.edu/~cs188/ |
| HackerRank | Constraint Problems | https://www.hackerrank.com/domains/algorithms |

### Soal Latihan Mandiri

**Soal 1:** Formulasikan jadwal ujian sebagai CSP dengan 5 mata kuliah, 3 slot waktu, dan constraint mahasiswa yang mengambil >1 mata kuliah!

**Soal 2:** Trace AC-3 untuk variabel A, B, C dengan domain {1,2,3} dan constraint: A<B, B<C!

**Soal 3:** Untuk Map Coloring 4 wilayah berbentuk linear (A-B-C-D), berapa node yang dikunjungi dengan dan tanpa MRV?

**Soal 4:** Sebuah pangkalan TNI harus menjadwalkan 6 tugas patroli ke 4 tim dengan constraint waktu dan kompetensi. Formulasikan sebagai CSP!

**Soal 5:** Bandingkan performa Backtracking dengan Forward Checking untuk 8-Queens!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dari materi Pertemuan 06? Mengapa?
2. Bagaimana CSP dapat diterapkan untuk scheduling operasi militer?
3. Kapan sebaiknya menggunakan CSP vs optimization algorithm?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/ConstraintProgramming, r/optimization
- Stack Overflow: tag [constraint-satisfaction], [csp]
- Discord: OR & Optimization communities

### Topik Diskusi

- Bagaimana CSP dapat membantu dalam resource allocation militer?
- Apakah Sudoku solver merupakan contoh AI yang "cerdas"?
- Bagaimana constraint propagation mirip dengan reasoning manusia?

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Definisi dan Komponen CSP selesai
- [ ] Section 2: Review Formulasi CSP untuk Masalah Klasik selesai
- [ ] Section 3: Review Backtracking Search untuk CSP selesai
- [ ] Section 4: Review Constraint Propagation selesai
- [ ] Section 5: Review Heuristik untuk CSP selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS188: CSP | Berkeley | https://inst.eecs.berkeley.edu/~cs188/ |
| Discrete Optimization | Coursera | https://www.coursera.org/learn/discrete-optimization |
| Constraint Programming | MiniZinc | https://www.minizinc.org/doc-2.5.5/en/index.html |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 6.
- Mackworth, A.K. (1977). "Consistency in Networks of Relations"
- Dechter, R. (2003). "Constraint Processing"

### 🎥 Channel YouTube Rekomendasi

- **Computerphile** - Sudoku and constraint algorithms
- **Abdul Bari** - Algorithm explanations
- **MIT OCW** - Full lectures on CSP
- **Google Developers** - OR-Tools tutorials

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. Tiga komponen utama: Variabel (X), Domain (D), Constraint (C)
2. Unary melibatkan 1 variabel (X≠5), Binary melibatkan 2 variabel (X≠Y)
3. Consistent assignment: assignment yang tidak melanggar constraint apapun

### Section 2
1. 4-Queens: X={Q1,Q2,Q3,Q4}, D={1,2,3,4}, C: Qi≠Qj dan |Qi-Qj|≠|i-j| untuk semua i≠j
2. Map Coloring Australia: 9 binary constraints (WA-NT, WA-SA, NT-SA, NT-Q, SA-Q, SA-NSW, SA-V, Q-NSW, NSW-V)
3. Graph dengan 4 node dan edge antara wilayah yang bertetangga

### Section 3
1. Backtracking mendeteksi konflik lebih awal dan tidak perlu generate semua kemungkinan
2. Trace: {X1=1,X2=2,X3=1} sukses; atau backtrack jika X1=1,X2=1 (konflik)
3. Backtrack ketika tidak ada nilai yang consistent untuk variabel saat ini

### Section 4
1. Node: setiap nilai memenuhi unary constraint variabel itu. Arc: untuk setiap nilai di Xi ada nilai di Xj yang memenuhi constraint
2. Setelah AC-3: X={1,2}, Y={2,3} (hapus X=3 karena tidak ada Y>3)
3. AC-3 return false ketika domain suatu variabel menjadi kosong

### Section 5
1. MRV memilih variabel dengan domain terkecil → jika akan gagal, gagal lebih cepat
2. LCV untuk CSP di mana solusi ada dan kita ingin menemukannya cepat; random jika semua nilai sama baiknya
3. Forward Checking hanya cek neighbor langsung; MAC menjalankan full AC-3 (lebih banyak pruning tapi lebih mahal)

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
