# Panduan Belajar Mandiri Pertemuan 02: Pemecahan Masalah dengan Pencarian - Uninformed Search

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 02  
**Topik:** Pemecahan Masalah dengan Pencarian - Uninformed Search  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Memformulasikan masalah dunia nyata sebagai problem pencarian
2. Menjelaskan dan membandingkan algoritma BFS, DFS, dan UCS
3. Menganalisis kompleksitas waktu dan ruang setiap algoritma
4. Mengimplementasikan dan menelusuri algoritma uninformed search secara manual
5. Memilih algoritma yang tepat berdasarkan karakteristik masalah

---

## 1. Review Konsep: Formulasi Masalah Pencarian (45 menit)

### Ringkasan Materi

Pencarian adalah proses menemukan **urutan tindakan** yang membawa agen dari **state awal** ke **state tujuan**. Untuk memformulasikan masalah sebagai problem pencarian, kita perlu mendefinisikan lima komponen:

| Komponen | Definisi | Contoh (8-Puzzle) |
|----------|----------|-------------------|
| **State Space** | Himpunan semua konfigurasi yang mungkin | Semua susunan 9 tiles |
| **Initial State** | State awal agen | Susunan acak tiles |
| **Actions** | Tindakan yang dapat dilakukan | UP, DOWN, LEFT, RIGHT |
| **Transition Model** | Hasil dari aksi di state | RESULT(s, a) = s' |
| **Goal Test** | Fungsi untuk cek apakah goal | Apakah tiles tersusun 1-8? |
| **Path Cost** | Total biaya dari path | Jumlah gerakan |

![Komponen Problem Pencarian](images/ss02-01-search-problem-components.png)

*Gambar 1.1: Lima komponen formulasi problem pencarian*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram komponen problem pencarian dengan contoh 8-puzzle
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
TATA LETAK: Diagram pusat dengan lima cabang melingkar
WARNA:
- Pusat: #2563eb (biru) untuk "Problem Pencarian"
- Komponen: #10b981 (hijau), #f59e0b (oranye), #8b5cf6 (ungu), #ec4899 (pink), #ef4444 (merah)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Lingkaran pusat: "PROBLEM PENCARIAN"
2. Lima cabang dengan kotak: State Space, Initial State, Actions, Goal Test, Path Cost
3. Contoh kecil 8-puzzle di samping
LABEL: "State Space", "Initial State", "Actions", "Goal Test", "Path Cost"
UKURAN: 900x700 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Problem Solving and Search | MIT OCW | 50:00 | https://www.youtube.com/watch?v=gGQ-vAmdAOI |
| 2 | Intro to AI: Search Algorithms | Reducible | 15:00 | https://www.youtube.com/watch?v=pcKY4hjDrxk |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Pathfinding Tutorial | Red Blob Games | Tutorial interaktif pathfinding | https://www.redblobgames.com/pathfinding/a-star/introduction.html |

### ✍️ Latihan Pemahaman

1. Sebutkan lima komponen formulasi problem pencarian!
2. Formulasikan masalah "mencari jalan keluar labirin" dengan kelima komponen tersebut!

---

## 2. Review Konsep: Breadth-First Search (BFS) (45 menit)

### Ringkasan Materi

**BFS** mengeksplorasi node **level-by-level** menggunakan **Queue (FIFO)**.

**Karakteristik:**
- **Complete:** Ya (jika b finite)
- **Optimal:** Ya (jika step cost = 1)
- **Time Complexity:** O(b^d)
- **Space Complexity:** O(b^d)

**Pseudocode:**
```
function BFS(problem):
    frontier = Queue([initial_state])
    explored = Set()
    while frontier not empty:
        node = frontier.dequeue()
        if goal_test(node): return node
        explored.add(node)
        for child in expand(node):
            if child not in explored and child not in frontier:
                frontier.enqueue(child)
    return failure
```

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | BFS Algorithm | WilliamFiset | 10:00 | https://www.youtube.com/watch?v=oDqjPvD54Ss |
| 2 | BFS vs DFS | NeetCode | 10:00 | https://www.youtube.com/watch?v=62IcXF_OF3k |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| BFS Visualization | VisuAlgo | Step-by-step BFS | https://visualgo.net/en/dfsbfs |

### ✍️ Latihan Pemahaman

1. Struktur data apa yang digunakan BFS untuk menyimpan frontier?
2. Kapan BFS menjamin solusi optimal?

---

## 3. Review Konsep: Depth-First Search (DFS) (45 menit)

### Ringkasan Materi

**DFS** mengeksplorasi node **sedalam mungkin** menggunakan **Stack (LIFO)**.

**Karakteristik:**
- **Complete:** Tidak (bisa infinite loop)
- **Optimal:** Tidak
- **Time Complexity:** O(b^m)
- **Space Complexity:** O(bm) - lebih hemat!

**Variasi:**
- **Depth-Limited Search:** DFS dengan batas kedalaman
- **Iterative Deepening (IDDFS):** DFS berulang dengan depth limit meningkat

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | DFS Algorithm | WilliamFiset | 14:00 | https://www.youtube.com/watch?v=7fujbpJ0LB4 |
| 2 | Iterative Deepening | Education 4u | 8:00 | https://www.youtube.com/watch?v=Y69rPaBT3fw |

### ✍️ Latihan Pemahaman

1. Mengapa DFS tidak complete?
2. Apa keunggulan DFS dibanding BFS dari segi memori?

---

## 4. Review Konsep: Uniform-Cost Search (UCS) (45 menit)

### Ringkasan Materi

**UCS** mengekspansi node dengan **path cost terendah** menggunakan **Priority Queue**.

**Fungsi evaluasi:** f(n) = g(n) = total path cost dari start ke n

**Karakteristik:**
- **Complete:** Ya
- **Optimal:** Ya (selalu!)
- **Time/Space:** O(b^(1+⌊C*/ε⌋))

**Kapan menggunakan UCS:** Ketika step cost berbeda-beda (weighted graph).

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Uniform Cost Search | Joe James | 12:00 | https://www.youtube.com/watch?v=dRMvK76xQJI |
| 2 | Dijkstra's Algorithm | Computerphile | 10:00 | https://www.youtube.com/watch?v=GazC3A4OQTE |

### ✍️ Latihan Pemahaman

1. Apa perbedaan utama antara BFS dan UCS?
2. Kapan UCS dan BFS menghasilkan solusi yang sama?

---

## 5. Review Konsep: Perbandingan Algoritma (45 menit)

### Ringkasan Materi

| Kriteria | BFS | DFS | UCS |
|----------|-----|-----|-----|
| **Structure** | Queue | Stack | Priority Queue |
| **Complete?** | Ya* | Tidak | Ya |
| **Optimal?** | Ya* | Tidak | Ya |
| **Time** | O(b^d) | O(b^m) | O(b^(1+⌊C*/ε⌋)) |
| **Space** | O(b^d) | O(bm) | O(b^(1+⌊C*/ε⌋)) |
| **Best for** | Unit cost | Memory limited | Weighted graph |

*Ya jika cost uniform

**Pemilihan Algoritma:**
- Path cost seragam → BFS
- Memori terbatas → DFS (atau IDDFS)
- Path cost berbeda → UCS

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Search Comparison | Gate Smashers | 15:00 | https://www.youtube.com/watch?v=amlkE0g-YFU |

### ✍️ Latihan Pemahaman

1. Dalam kondisi apa Anda memilih IDDFS dibanding BFS?
2. Jelaskan trade-off antara completeness dan memory efficiency!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Deskripsi | Link |
|------|-----------|------|
| PathFinding.js | Bandingkan berbagai algoritma | https://qiao.github.io/PathFinding.js/visual/ |
| VisuAlgo - Graph Traversal | BFS/DFS step-by-step | https://visualgo.net/en/dfsbfs |
| 8-Puzzle Solver | Lihat BFS/DFS menyelesaikan puzzle | https://tristanpenman.com/demos/n-puzzle/ |
| Graph Online | Buat dan analisis graph | https://graphonline.ru/en/ |

### Tugas Eksplorasi

1. Buka **PathFinding.js** dan bandingkan BFS vs DFS pada maze yang sama
2. Catat: Berapa node yang dikunjungi masing-masing algoritma?
3. Buat graph sederhana di **Graph Online** dan trace BFS/DFS secara manual
4. Screenshot hasil dan bandingkan dengan trace Anda

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | BFS/DFS Visualized | Spanning Tree | 8:00 | https://www.youtube.com/watch?v=HZ5YTanv5QE |
| 2 | Dijkstra Visualized | WilliamFiset | 12:00 | https://www.youtube.com/watch?v=pSqmAO-m7Lk |
| 3 | Graph vs Tree Traversal | Back To Back SWE | 14:00 | https://www.youtube.com/watch?v=TIbUeeksXcI |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 3.1-3.4 (Solving Problems by Searching)
- Red Blob Games Tutorial: Introduction to A*

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| LeetCode | BFS/DFS Problems | https://leetcode.com/tag/breadth-first-search/ |
| HackerRank | Graph Traversal | https://www.hackerrank.com/domains/algorithms |

### Soal Latihan Mandiri

**Soal 1:** Diberikan graph berikut, trace BFS dan DFS dari node A ke G:
```
    A---B---E
    |   |   |
    C---D---G
        |
        F
```

**Soal 2:** Sebuah drone TNI AU harus mencari jalur dari pangkalan ke target melalui waypoints. Jika setiap waypoint memiliki jarak berbeda, algoritma mana yang tepat? Mengapa?

**Soal 3:** Hitung kompleksitas BFS jika b=4 dan d=5. Berapa total node yang dikunjungi?

**Soal 4:** Jelaskan mengapa IDDFS menggabungkan keunggulan BFS dan DFS!

**Soal 5:** Berikan contoh kasus di mana DFS menemukan solusi lebih cepat dari BFS!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dipahami dari materi Uninformed Search?
2. Bagaimana algoritma pencarian dapat diterapkan untuk navigasi UAV militer?
3. Dalam skenario pertahanan, kapan kecepatan lebih penting dari optimalitas?

### 💬 Forum Diskusi Online

- Reddit: r/artificial, r/learnprogramming
- Stack Overflow: tag [breadth-first-search], [depth-first-search]

### Topik Diskusi

- Trade-off antara completeness dan efficiency
- Real-world applications of search algorithms

---

## Checklist Belajar Mandiri

- [ ] Section 1: Formulasi Problem Pencarian selesai
- [ ] Section 2: BFS selesai
- [ ] Section 3: DFS selesai
- [ ] Section 4: UCS selesai
- [ ] Section 5: Perbandingan Algoritma selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS188: Introduction to AI | Berkeley | https://inst.eecs.berkeley.edu/~cs188/ |
| Algorithms Specialization | Coursera | https://www.coursera.org/specializations/algorithms |
| Elements of AI | University of Helsinki | https://www.elementsofai.com/ |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 3.
- Cormen, T.H. et al. (2022). *Introduction to Algorithms* (4th Ed.). MIT Press. Chapter 22 (Graph Algorithms).

### 🎥 Channel YouTube Rekomendasi

- **WilliamFiset** - Graph algorithms
- **NeetCode** - Coding interview problems
- **Reducible** - Visual explanations
- **Abdul Bari** - Algorithm explanations

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. State Space, Initial State, Actions, Transition Model, Goal Test, Path Cost
2. Labirin: State=posisi, Initial=pintu masuk, Actions=UP/DOWN/LEFT/RIGHT, Goal=pintu keluar, Cost=jumlah langkah

### Section 2
1. Queue (FIFO)
2. Ketika semua step cost sama (cost = 1)

### Section 3
1. DFS bisa masuk ke cabang tak terhingga dan tidak pernah kembali
2. DFS hanya menyimpan O(bm) node di memori, BFS menyimpan O(b^d)

### Section 4
1. BFS tidak mempertimbangkan path cost, UCS memprioritaskan path cost terendah
2. Ketika semua edge memiliki cost yang sama

### Section 5
1. Ketika butuh optimalitas BFS tapi memori terbatas
2. DFS hemat memori tapi tidak complete/optimal; BFS complete/optimal tapi boros memori

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
