# Panduan Belajar Mandiri Pertemuan 07: Review dan Latihan Komprehensif

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 07  
**Topik:** Review dan Latihan Komprehensif (Persiapan UTS)  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Mengintegrasikan konsep dari Pertemuan 01-06
2. Memilih algoritma yang tepat untuk berbagai jenis masalah
3. Menyelesaikan soal-soal yang menggabungkan multiple concepts
4. Mengidentifikasi kelemahan pemahaman untuk diperbaiki
5. Siap menghadapi UTS dengan percaya diri

---

## 1. Review Konsep: Agen Cerdas dan PEAS (45 menit)

### Ringkasan Materi

**Empat Pendekatan AI:**

| Pendekatan | Fokus | Contoh |
|------------|-------|--------|
| Thinking Humanly | Proses kognitif | Cognitive architecture |
| Thinking Rationally | Penalaran logis | Theorem prover |
| Acting Humanly | Perilaku mirip manusia | Chatbot |
| **Acting Rationally** | Tindakan optimal | Self-driving car |

**Lima Jenis Agen (dari sederhana ke kompleks):**

| Jenis | Karakteristik | Contoh |
|-------|---------------|--------|
| Simple Reflex | Condition-action rules | Thermostat |
| Model-Based Reflex | Internal state | Robot dengan memory |
| Goal-Based | Mempertimbangkan goal | Navigation system |
| Utility-Based | Utility function | Self-driving car |
| Learning | Dapat improve | Recommendation system |

**Enam Karakteristik Lingkungan:**

| Karakteristik | Spektrum | Implikasi |
|---------------|----------|-----------|
| Observable | Fully ↔ Partially | Partial → perlu state |
| Deterministic | Deterministic ↔ Stochastic | Stochastic → probabilistic |
| Episode | Episodic ↔ Sequential | Sequential → planning |
| Static | Static ↔ Dynamic | Dynamic → real-time |
| Discrete | Discrete ↔ Continuous | Continuous → discretization |
| Agents | Single ↔ Multi | Multi → game theory |

**PEAS Framework:**
- **P**erformance: Kriteria sukses
- **E**nvironment: Objek di lingkungan
- **A**ctuators: Tindakan yang dapat dilakukan
- **S**ensors: Input yang dapat diterima

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Intelligent Agents Review | Gate Smashers | 10:00 | https://www.youtube.com/watch?v=nDiCxqmDWHQ |
| 2 | PEAS Framework | AI Course | 8:00 | https://www.youtube.com/watch?v=WKMO8jC5OFQ |

### ✍️ Latihan Pemahaman

1. Sistem rekomendasi Netflix yang belajar dari rating user termasuk jenis agen apa?
2. Analisis karakteristik lingkungan permainan catur!
3. Buat analisis PEAS untuk drone pengintai militer!

---

## 2. Review Konsep: Uninformed Search (45 menit)

### Ringkasan Materi

**Formulasi Search Problem:**

| Komponen | Definisi |
|----------|----------|
| State space | Semua state yang mungkin |
| Initial state | State awal |
| Goal test | Fungsi cek goal |
| Actions | Aksi yang tersedia |
| Transition model | Result(s, a) → s' |
| Path cost | Biaya dari initial ke state |

**Perbandingan Algoritma Uninformed:**

| Kriteria | BFS | DFS | UCS |
|----------|-----|-----|-----|
| **Complete?** | Ya (b finite) | Tidak | Ya |
| **Optimal?** | Ya (cost=1) | Tidak | Ya |
| **Time** | O(b^d) | O(b^m) | O(b^(1+⌊C*/ε⌋)) |
| **Space** | O(b^d) | O(bm) | O(b^(1+⌊C*/ε⌋)) |
| **Data Structure** | FIFO Queue | LIFO Stack | Priority Queue (g) |

**Rumus Nodes:**
$$\text{Nodes} = 1 + b + b^2 + ... + b^d = \frac{b^{d+1} - 1}{b - 1}$$

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | BFS vs DFS | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=62IcXF_OF3k |
| 2 | UCS Explained | AI Course | 10:00 | https://www.youtube.com/watch?v=dRMvK76xQJI |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Pathfinding Visualizer | PathFinding.js | Bandingkan BFS, DFS, UCS | https://qiao.github.io/PathFinding.js/visual/ |
| Graph Search | USFCA | Visualisasi BFS/DFS | https://www.cs.usfca.edu/~galles/visualization/BFS.html |

### ✍️ Latihan Pemahaman

1. Jika b=3 dan goal di depth 4, berapa maksimum node yang dikunjungi BFS?
2. Kapan DFS lebih baik dari BFS?
3. Trace UCS untuk graph dengan weighted edges!

---

## 3. Review Konsep: Informed Search dan Heuristik (45 menit)

### Ringkasan Materi

**Konsep Heuristik:**

| Konsep | Definisi |
|--------|----------|
| **h(n)** | Estimasi cost dari n ke goal |
| **Admissible** | h(n) ≤ h*(n) — never overestimate |
| **Consistent** | h(n) ≤ c(n,a,n') + h(n') — triangle inequality |

**Perbandingan Greedy vs A*:**

| Kriteria | Greedy Best-First | A* |
|----------|-------------------|-----|
| **Evaluation** | f(n) = h(n) | f(n) = g(n) + h(n) |
| **Complete?** | Tidak | Ya |
| **Optimal?** | Tidak | Ya (jika h admissible) |

**Contoh Heuristik untuk 8-Puzzle:**
- h₁ = jumlah tiles di posisi salah (misplaced tiles)
- h₂ = total Manhattan distance

**Dominasi:** Jika h₂(n) ≥ h₁(n) untuk semua n, maka h₂ mendominasi h₁ (lebih efisien).

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | A* Algorithm | Computerphile | 12:00 | https://www.youtube.com/watch?v=ySN5Wnu88nE |
| 2 | Heuristics Explained | Sebastian Lague | 10:00 | https://www.youtube.com/watch?v=-L-WgKMFuhE |

### ✍️ Latihan Pemahaman

1. Untuk 8-puzzle, hitung h₁ dan h₂ untuk state tertentu!
2. Apakah h(n) = 2 × Manhattan_distance admissible? Mengapa?
3. Trace A* untuk route finding dengan straight-line heuristic!

---

## 4. Review Konsep: Local Search dan Optimisasi (45 menit)

### Ringkasan Materi

**Perbedaan dengan Systematic Search:**

| Aspek | Systematic | Local Search |
|-------|------------|--------------|
| Tujuan | Path ke goal | State terbaik |
| Memory | Banyak node | Hanya current |
| Path | Penting | Tidak penting |

**Algoritma Local Search:**

| Algoritma | Karakteristik | Escape Local Optima? |
|-----------|---------------|---------------------|
| Hill Climbing | Greedy, selalu naik | Tidak |
| Simulated Annealing | Probabilistic downhill | Ya (dengan T tinggi) |
| Genetic Algorithm | Populasi, evolusi | Ya |

**Simulated Annealing - Acceptance Probability:**
$$P(accept) = e^{\Delta E / T}$$ (untuk langkah buruk)

**Genetic Algorithm Components:**
- Selection (Roulette, Tournament)
- Crossover (Single-point, Two-point)
- Mutation (Random change)

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Hill Climbing | Abdul Bari | 12:00 | https://www.youtube.com/watch?v=oSdPmxRCWws |
| 2 | Simulated Annealing | Reducible | 18:00 | https://www.youtube.com/watch?v=eBmU1ONJ-os |
| 3 | Genetic Algorithm | The Coding Train | 25:00 | https://www.youtube.com/watch?v=uQj5UNhCPuo |

### ✍️ Latihan Pemahaman

1. Mengapa Hill Climbing bisa stuck di local maximum?
2. Hitung P(accept) untuk SA dengan T=50, ΔE=-10!
3. Untuk GA dengan fitness [6,4,3,2], hitung probabilitas roulette wheel!

---

## 5. Review Konsep: Adversarial Search dan CSP (45 menit)

### Ringkasan Materi

**Minimax:**
- MAX memilih nilai tertinggi
- MIN memilih nilai terendah
- Kompleksitas: O(b^m)

**Alpha-Beta Pruning:**
- α = best for MAX so far
- β = best for MIN so far
- Prune when α ≥ β
- Best case: O(b^(m/2))

**CSP Components:**
- Variables (X)
- Domains (D)
- Constraints (C)

**CSP Techniques:**

| Technique | Purpose |
|-----------|---------|
| Arc Consistency (AC-3) | Reduce domains |
| Backtracking | Search with pruning |
| MRV Heuristic | Variable selection (fail-first) |
| LCV Heuristic | Value selection (succeed-first) |
| Forward Checking | Propagate after assignment |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Minimax & Alpha-Beta | Sebastian Lague | 12:00 | https://www.youtube.com/watch?v=l-hh51ncgDI |
| 2 | CSP Overview | MIT OCW | 20:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |
| 3 | AC-3 Algorithm | AI Course | 15:00 | https://www.youtube.com/watch?v=4cCS8rrYT14 |

### ✍️ Latihan Pemahaman

1. Trace Minimax untuk tree dengan terminals [3,5,2,9]!
2. Trace Alpha-Beta dan identifikasi pruning!
3. Trace AC-3 untuk X,Y dengan D={1,2,3} dan X<Y!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Kegunaan | Link |
|------|----------|------|
| Pathfinding Visualizer | BFS, DFS, A* | https://qiao.github.io/PathFinding.js/visual/ |
| Minimax Visualizer | Game trees | https://www.cs.usfca.edu/~galles/visualization/MinMax.html |
| Genetic Cars | GA evolution | https://rednuht.org/genetic_cars_2/ |
| Sudoku Solver | CSP | https://www.sudoku-solutions.com/ |

### Tugas Eksplorasi

1. Bandingkan **BFS vs A*** untuk maze solving
2. Trace **Minimax** pada visualizer
3. Jalankan **Genetic Cars** dan amati evolusi
4. Selesaikan Sudoku dengan memperhatikan constraint propagation

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | CS188 Full Review | Berkeley | 60:00 | https://www.youtube.com/watch?v=J4pLZnepxIo |
| 2 | AI Algorithms Comparison | MIT OCW | 50:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |
| 3 | Search Algorithm Review | Abdul Bari | 30:00 | https://www.youtube.com/watch?v=62IcXF_OF3k |
| 4 | Game AI Deep Dive | Sebastian Lague | 25:00 | https://www.youtube.com/watch?v=U4ogK0MIzqk |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapters 1-6 (Review)
- CS188 Lecture Notes
- Practice Problems from Berkeley AI Course

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| CS188 Practice | All Topics | https://inst.eecs.berkeley.edu/~cs188/ |
| AI Exercises | Comprehensive | https://aimacode.github.io/aima-exercises/ |

### Soal Latihan Komprehensif

**Soal 1 (Agen):** Sebuah sistem pertahanan udara harus mendeteksi, melacak, dan mencegat ancaman. Tentukan jenis agen minimum dan buat analisis PEAS!

**Soal 2 (Search):** Formulasikan misi SAR (Search and Rescue) sebagai search problem. Pilih algoritma yang tepat!

**Soal 3 (A*):** Untuk graph dengan heuristik, trace A* dan buktikan optimalitas!

**Soal 4 (Local Search):** Desain utility function untuk penempatan radar yang memaksimalkan coverage!

**Soal 5 (Minimax):** Trace Minimax dan Alpha-Beta untuk game tree. Hitung efisiensi pruning!

**Soal 6 (CSP):** Formulasikan jadwal patroli sebagai CSP dengan constraint waktu dan personel!

**Soal 7 (Integrasi):** Bandingkan pendekatan search, local search, dan CSP untuk N-Queens problem!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Topik mana yang paling sulit? Mengapa?
2. Bagaimana konsep-konsep ini saling terhubung?
3. Bagaimana menerapkan materi ini dalam konteks pertahanan Indonesia?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/artificial, r/learnmachinelearning
- Stack Overflow: tag [artificial-intelligence]
- Discord: AI/ML study groups

### Tips Menghadapi UTS

1. **Pahami konsep, bukan hafal** - fokus pada "mengapa" bukan hanya "bagaimana"
2. **Latihan trace algoritma** - Minimax, A*, AC-3 sering keluar
3. **Bandingkan algoritma** - tahu kapan menggunakan yang mana
4. **Hitung kompleksitas** - O(b^d) vs O(b^m) dll
5. **Kerjakan soal latihan** - dari CS188 dan AIMA

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Agen Cerdas dan PEAS selesai
- [ ] Section 2: Review Uninformed Search selesai
- [ ] Section 3: Review Informed Search selesai
- [ ] Section 4: Review Local Search selesai
- [ ] Section 5: Review Adversarial Search dan CSP selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 7 soal komprehensif)
- [ ] Section 9: Refleksi dan persiapan UTS selesai

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS188: Full Course | Berkeley | https://inst.eecs.berkeley.edu/~cs188/ |
| AI for Everyone | Coursera | https://www.coursera.org/learn/ai-for-everyone |
| Elements of AI | Helsinki | https://www.elementsofai.com/ |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapters 1-6.
- CS188 Lecture Slides and Notes

### 🎥 Channel YouTube Rekomendasi

- **Sebastian Lague** - Algorithm visualizations
- **Abdul Bari** - Algorithm explanations
- **MIT OCW** - Full lectures
- **3Blue1Brown** - Mathematical intuition

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. Learning Agent (belajar dari rating user)
2. Catur: Fully Observable, Deterministic, Sequential, Static (tanpa timer), Discrete, Multi-Agent (Competitive)
3. PEAS Drone: P=detection rate, coverage; E=airspace, targets; A=flight control, camera; S=radar, camera, GPS

### Section 2
1. Nodes = (3^5-1)/(3-1) = 121 nodes
2. DFS lebih baik ketika: solusi banyak dan di depth dalam, memori terbatas, tidak butuh optimal
3. (Trace sesuai graph yang diberikan)

### Section 3
1. Untuk state tertentu, hitung h₁ (jumlah salah posisi) dan h₂ (total Manhattan)
2. Tidak admissible karena bisa overestimate (h > h*)
3. (Trace A* dengan priority queue berdasarkan f=g+h)

### Section 4
1. Hill Climbing hanya menerima langkah yang meningkatkan nilai, tidak bisa escape local max
2. P = e^(-10/50) = e^(-0.2) ≈ 0.819
3. Total=15. P(1)=6/15=0.4, P(2)=4/15=0.27, P(3)=3/15=0.2, P(4)=2/15=0.13

### Section 5
1. MIN level: min(3,5)=3, min(2,9)=2. MAX root: max(3,2)=3
2. (Trace dengan α=-∞, β=+∞, identifikasi kapan α≥β)
3. Setelah AC-3: X={1,2}, Y={2,3} (hapus X=3 karena tidak ada Y>3)

---

## Ringkasan Formula Penting untuk UTS

| Topik | Formula | Keterangan |
|-------|---------|------------|
| BFS Nodes | (b^(d+1)-1)/(b-1) | b=branching, d=depth |
| A* | f(n) = g(n) + h(n) | g=path cost, h=heuristic |
| Admissible | h(n) ≤ h*(n) | Never overestimate |
| SA Accept | P = e^(ΔE/T) | Untuk langkah buruk |
| Minimax | O(b^m) | Time complexity |
| Alpha-Beta | O(b^(m/2)) | Best case |
| AC-3 | O(cd³) | c=constraints, d=domain |

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
