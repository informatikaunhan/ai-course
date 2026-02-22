# Panduan Belajar Mandiri Pertemuan 03: Pencarian Heuristik - Informed Search

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 03  
**Topik:** Pencarian Heuristik - Informed Search  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Menjelaskan konsep heuristik dan perannya dalam pencarian
2. Membedakan Greedy Best-First Search dengan algoritma lainnya
3. Menjelaskan dan mengimplementasikan algoritma A*
4. Memahami properti admissibility dan consistency pada heuristik
5. Merancang fungsi heuristik yang baik untuk berbagai domain

---

## 1. Review Konsep: Heuristik dan Fungsi Evaluasi (45 menit)

### Ringkasan Materi

> **Heuristik h(n)** adalah fungsi yang memberikan **estimasi biaya** dari node n ke goal state terdekat.

**Fungsi Evaluasi:**

| Algoritma | Fungsi Evaluasi | Arti |
|-----------|-----------------|------|
| UCS | f(n) = g(n) | Cost sejauh ini |
| Greedy | f(n) = h(n) | Estimasi ke goal |
| A* | f(n) = g(n) + h(n) | Total estimasi |

![Fungsi Evaluasi](images/ss03-01-evaluation-functions.png)

*Gambar 1.1: Hubungan g(n), h(n), dan f(n)*

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | What is a Heuristic? | Spanning Tree | 8:00 | https://www.youtube.com/watch?v=jM3sH9cJwfE |
| 2 | Heuristics in AI | Gate Smashers | 12:00 | https://www.youtube.com/watch?v=PzEWHH2v3TE |

### ✍️ Latihan Pemahaman

1. Apa perbedaan antara g(n) dan h(n)?
2. Mengapa heuristik dapat mempercepat pencarian?

---

## 2. Review Konsep: Greedy Best-First Search (45 menit)

### Ringkasan Materi

**Greedy Best-First Search** selalu mengekspansi node yang **terlihat paling dekat ke goal** berdasarkan h(n).

**Karakteristik:**
- Fungsi evaluasi: f(n) = h(n)
- **Tidak optimal** dan **tidak complete**
- Sangat cepat jika heuristik bagus

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Greedy Best First Search | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=dv1m3L6QXWs |
| 2 | Greedy vs A* Comparison | Gate Smashers | 12:00 | https://www.youtube.com/watch?v=PzEWHH2v3TE |

### ✍️ Latihan Pemahaman

1. Mengapa Greedy Best-First Search tidak optimal?
2. Kapan Greedy bisa gagal menemukan solusi?

---

## 3. Review Konsep: Algoritma A* (45 menit)

### Ringkasan Materi

**A*** mengkombinasikan g(n) dan h(n): **f(n) = g(n) + h(n)**

**Karakteristik:**
- **Complete:** Ya
- **Optimal:** Ya (jika h admissible)
- **Time/Space:** O(b^d) dalam worst case

**Pseudocode:**
```
function A_Star(problem, h):
    frontier = PriorityQueue(key=f)
    frontier.insert(initial_state, f=h(initial))
    explored = Set()
    
    while frontier not empty:
        node = frontier.pop()  // Lowest f(n)
        if goal_test(node): return node
        explored.add(node)
        for child in expand(node):
            f_child = g(child) + h(child)
            if child not in explored:
                frontier.insert(child, f_child)
```

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | A* Pathfinding | Computerphile | 10:00 | https://www.youtube.com/watch?v=ySN5Wnu88nE |
| 2 | A* Algorithm Explained | Spanning Tree | 15:00 | https://www.youtube.com/watch?v=6TsL96NAZCo |
| 3 | A* Step by Step | Tech With Tim | 20:00 | https://www.youtube.com/watch?v=eSOJ3ARN5FM |

### ✍️ Latihan Pemahaman

1. Apa syarat agar A* optimal?
2. Jelaskan perbedaan A* dengan UCS!

---

## 4. Review Konsep: Admissibility dan Consistency (45 menit)

### Ringkasan Materi

**Admissible Heuristic:**
> h(n) ≤ h*(n) untuk semua n
> Tidak pernah **overestimate** biaya ke goal

**Consistent Heuristic (Monotonic):**
> h(n) ≤ c(n,a,n') + h(n')
> Triangle inequality

**Dominance:**
> h₂ dominates h₁ jika h₂(n) ≥ h₁(n) untuk semua n
> Heuristik yang mendominasi lebih efisien

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | A* Optimality Proof | AI Course | 10:00 | https://www.youtube.com/watch?v=HtSuA80QTyo |
| 2 | Admissible Heuristics | CS188 Berkeley | 12:00 | https://www.youtube.com/watch?v=Mlwrx7hbKPs |

### ✍️ Latihan Pemahaman

1. Berikan contoh heuristik yang admissible untuk 8-puzzle!
2. Jika h₁=3 dan h₂=5 untuk node yang sama, mana yang lebih baik?

---

## 5. Review Konsep: Merancang Heuristik (45 menit)

### Ringkasan Materi

**Teknik Relaxed Problem:**
- Hilangkan constraint dari masalah asli
- Solusi optimal relaxed problem = admissible heuristic

**Contoh 8-Puzzle:**

| Heuristik | Formula | Admissible? |
|-----------|---------|-------------|
| h₁: Misplaced Tiles | Jumlah tile tidak di tempat | Ya |
| h₂: Manhattan Distance | Σ |row_diff| + |col_diff| | Ya |

h₂ dominates h₁ → A* dengan h₂ lebih efisien

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | 8-Puzzle Heuristics | AI Course | 12:00 | https://www.youtube.com/watch?v=G0wHY4s2ZiA |
| 2 | Manhattan Distance | Abdul Bari | 8:00 | https://www.youtube.com/watch?v=TE6KIHCuxNY |

### ✍️ Latihan Pemahaman

1. Hitung h₁ dan h₂ untuk state 8-puzzle tertentu!
2. Jelaskan mengapa Manhattan distance admissible!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Deskripsi | Link |
|------|-----------|------|
| PathFinding.js | Bandingkan A*, Dijkstra, BFS | https://qiao.github.io/PathFinding.js/visual/ |
| Red Blob Games | Tutorial A* interaktif | https://www.redblobgames.com/pathfinding/a-star/introduction.html |
| 8-Puzzle Solver | Lihat A* menyelesaikan puzzle | https://tristanpenman.com/demos/n-puzzle/ |

### Tugas Eksplorasi

1. Buka **PathFinding.js** dan bandingkan A* dengan Dijkstra pada maze yang sama
2. Catat: Berapa node yang dikunjungi masing-masing?
3. Baca tutorial **Red Blob Games** section tentang heuristics
4. Gunakan **8-Puzzle Solver** dan perhatikan bagaimana A* bekerja

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | A* for Game AI | Sebastian Lague | 20:00 | https://www.youtube.com/watch?v=-L-WgKMFuhE |
| 2 | Pathfinding in RTS | AI and Games | 15:00 | https://www.youtube.com/watch?v=MnctS-LPwP0 |
| 3 | IDA* Algorithm | AI Course | 10:00 | https://www.youtube.com/watch?v=5LMXQ1NGHwU |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 3.5-3.6 (Informed Search)

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| LeetCode | Shortest Path Problems | https://leetcode.com/ |

### Soal Latihan Mandiri

**Soal 1:** Trace A* pada graph dengan heuristik yang diberikan. Tunjukkan urutan ekspansi node!

**Soal 2:** Untuk navigasi drone militer dari A ke B melewati obstacles, rancang heuristik yang admissible!

**Soal 3:** Buktikan bahwa Euclidean distance adalah admissible heuristic untuk pathfinding pada peta!

**Soal 4:** Bandingkan node yang diekspansi oleh A* menggunakan h₁ vs h₂ pada 8-puzzle!

**Soal 5:** Jelaskan mengapa A* dengan h(n)=0 sama dengan UCS!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dipahami dari materi Informed Search?
2. Bagaimana A* dapat diterapkan untuk perencanaan rute kapal selam?
3. Apa trade-off antara kualitas heuristik dan waktu komputasi?

### 💬 Forum Diskusi Online

- Reddit: r/artificial, r/algorithms
- Stack Overflow: tag [a-star], [heuristics]

### Topik Diskusi

- Aplikasi A* dalam game development
- Bagaimana merancang heuristik untuk domain baru

---

## Checklist Belajar Mandiri

- [ ] Section 1: Heuristik dan Fungsi Evaluasi selesai
- [ ] Section 2: Greedy Best-First Search selesai
- [ ] Section 3: Algoritma A* selesai
- [ ] Section 4: Admissibility dan Consistency selesai
- [ ] Section 5: Merancang Heuristik selesai
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

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 3.5-3.6.
- Hart, P.E., Nilsson, N.J. & Raphael, B. (1968). "A Formal Basis for the Heuristic Determination of Minimum Cost Paths"

### 🎥 Channel YouTube Rekomendasi

- **Sebastian Lague** - Game AI tutorials
- **Spanning Tree** - Algorithm visualizations
- **Computerphile** - Algorithm explanations
- **Abdul Bari** - AI algorithm walkthroughs

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. g(n) = biaya aktual dari start ke n; h(n) = estimasi biaya dari n ke goal
2. Heuristik memberikan "petunjuk" arah yang benar, mengurangi node yang perlu dieksplorasi

### Section 2
1. Greedy hanya mempertimbangkan h(n), tidak g(n), bisa memilih path yang tampak bagus tapi sebenarnya panjang
2. Ketika heuristik menyesatkan ke dead-end atau loop

### Section 3
1. Heuristik harus admissible (tidak overestimate)
2. A* mempertimbangkan g(n) + h(n), UCS hanya g(n)

### Section 4
1. Misplaced tiles atau Manhattan distance
2. h₂=5 lebih informatif (dominates h₁), lebih efisien untuk A*

### Section 5
1. [Tergantung state yang diberikan]
2. Manhattan distance menghitung minimum langkah jika tile bisa bergerak menembus tile lain - ini relaxation dari constraint asli

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
