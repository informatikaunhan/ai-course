# Panduan Belajar Mandiri Pertemuan 05: Pencarian Adversarial - Game Playing

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 05  
**Topik:** Pencarian Adversarial - Game Playing  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Memformulasikan game sebagai search problem dengan komponen lengkap
2. Mengimplementasikan dan melakukan trace algoritma Minimax
3. Menerapkan Alpha-Beta Pruning untuk optimisasi Minimax
4. Merancang fungsi evaluasi untuk game non-terminal
5. Memahami konsep Expectiminimax untuk game dengan elemen stokastik

---

## 1. Review Konsep: Pengantar Game dalam AI (45 menit)

### Ringkasan Materi

**Mengapa Game Penting untuk AI?**
- Game adalah "fruit fly" AI—domain terbatas tapi memerlukan kecerdasan nyata
- Milestone AI: Deep Blue (catur 1997), AlphaGo (Go 2016), OpenAI Five (Dota 2019)
- Teknik yang sama digunakan untuk strategi militer, negosiasi, dan ekonomi

**Klasifikasi Game:**

| Kriteria | Kategori | Contoh |
|----------|----------|--------|
| **Jumlah pemain** | Two-player | Catur, Go |
| **Informasi** | Perfect information | Catur (semua terlihat) |
| | Imperfect information | Poker (kartu tersembunyi) |
| **Determinisme** | Deterministic | Catur |
| | Stochastic | Backgammon (ada dadu) |
| **Hasil** | Zero-sum | Catur (menang = lawan kalah) |

**Fokus Pertemuan:** Two-player, deterministic, zero-sum, perfect information

> **Zero-Sum Game:** Keuntungan satu pemain = kerugian pemain lain.
> U_A + U_B = 0 → Jika kita menang (+1), lawan kalah (-1)

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Game Theory Intro | Primer | 15:00 | https://www.youtube.com/watch?v=M3oWYHYoBvk |
| 2 | Zero Sum Games | Khan Academy | 8:00 | https://www.youtube.com/watch?v=vAkTcd0t1Xg |
| 3 | AI in Games | Two Minute Papers | 5:00 | https://www.youtube.com/watch?v=Lu56xVlZ40M |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Play Tic-Tac-Toe AI | PlayTicTacToe | Mainkan melawan AI optimal | https://playtictactoe.org/ |
| Game Theory Simulator | Ncase | Interactive game theory demo | https://ncase.me/trust/ |

### ✍️ Latihan Pemahaman

1. Mengapa game menjadi testbed favorit untuk penelitian AI?
2. Apa yang dimaksud dengan zero-sum game? Berikan contoh!
3. Klasifikasikan permainan Poker berdasarkan keempat kriteria!

---

## 2. Review Konsep: Game Tree dan Formulasi (45 menit)

### Ringkasan Materi

> **Game Tree** adalah representasi semua kemungkinan permainan dari posisi awal hingga akhir.

**Komponen Game Tree:**
- **Node:** State permainan
- **Edge:** Move/aksi yang legal
- **Root:** Posisi awal
- **Terminal nodes:** Posisi akhir (menang/kalah/seri)

**Formulasi Game sebagai Search Problem:**

| Komponen | Deskripsi | Contoh (Tic-Tac-Toe) |
|----------|-----------|----------------------|
| **Initial State** | Konfigurasi awal | Papan kosong + giliran X |
| **Player(s)** | Siapa yang bergerak | MAX (X) atau MIN (O) |
| **Actions(s)** | Move legal dari state s | Kotak kosong yang tersedia |
| **Result(s, a)** | State setelah aksi a | Papan dengan tanda baru |
| **Terminal-Test(s)** | Apakah game selesai? | 3 berjajar atau papan penuh |
| **Utility(s, p)** | Nilai akhir untuk pemain p | +1, 0, -1 |

**Konvensi MAX dan MIN:**
- **MAX** (kita/AI): ingin **memaksimalkan** utility
- **MIN** (lawan): ingin **meminimalkan** utility

![Game Tree Tic-Tac-Toe](images/ss05-01-game-tree.png)

*Gambar 2.1: Game tree Tic-Tac-Toe dengan giliran MAX dan MIN*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Game tree Tic-Tac-Toe menunjukkan giliran MAX dan MIN bergantian
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tree vertikal dengan root di atas, 3 level kedalaman
WARNA:
- Node MAX (giliran X): #2563eb (biru) dengan border tebal
- Node MIN (giliran O): #ef4444 (merah) dengan border tebal
- Papan Tic-Tac-Toe: grid hitam dengan X biru dan O merah
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Level 0 (Root): Papan kosong, label "MAX (X bermain)"
2. Level 1: Tiga papan dengan X di posisi berbeda
3. Level 2: Respons O untuk setiap node level 1
4. Terminal node ditandai dengan nilai: "+1" atau "0"
LABEL: "MAX", "MIN", "Game Tree", nilai utility
UKURAN: 1000x700 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Kompleksitas Game Tree:**

| Game | Branching (b) | Depth (m) | Ukuran Tree |
|------|---------------|-----------|-------------|
| Tic-Tac-Toe | ~4 | 9 | ~10^5 |
| Chess | ~35 | ~100 | ~10^154 |
| Go | ~250 | ~150 | ~10^360 |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Game Trees | MIT OCW | 50:00 | https://www.youtube.com/watch?v=STjW3eH0Cik |
| 2 | Tic Tac Toe AI | The Coding Train | 20:00 | https://www.youtube.com/watch?v=trKjYdBASyQ |

### ✍️ Latihan Pemahaman

1. Gambarkan game tree untuk permainan sederhana dengan 2 langkah!
2. Mengapa tidak mungkin mengeksplorasi seluruh tree untuk catur?
3. Apa perbedaan antara MAX node dan MIN node?

---

## 3. Review Konsep: Algoritma Minimax (45 menit)

### Ringkasan Materi

> **Minimax** adalah strategi dimana setiap pemain bermain **optimal**: MAX memilih nilai tertinggi, MIN memilih nilai terendah.

**Asumsi Minimax:**
- Kedua pemain bermain **perfectly rational**
- Lawan akan selalu memilih langkah terbaik untuknya
- Kita harus mempertimbangkan respons terburuk dari lawan

**Definisi Rekursif:**
```
MINIMAX-VALUE(n) =
    UTILITY(n)                          jika n terminal
    max(MINIMAX-VALUE(child))           jika n adalah MAX node
    min(MINIMAX-VALUE(child))           jika n adalah MIN node
```

**Pseudocode:**
```
function MINIMAX(node, depth, maximizingPlayer):
    if depth == 0 or node is terminal:
        return utility(node)
    
    if maximizingPlayer:
        value = -infinity
        for each child of node:
            value = max(value, MINIMAX(child, depth-1, false))
        return value
    else:
        value = +infinity
        for each child of node:
            value = min(value, MINIMAX(child, depth-1, true))
        return value
```

![Minimax Trace](images/ss05-02-minimax-trace.png)

*Gambar 3.1: Trace algoritma Minimax pada game tree*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Game tree dengan 3 level menunjukkan nilai Minimax di setiap node
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tree dengan root di atas, nilai utility di terminal nodes, propagasi nilai ke atas
WARNA:
- Node MAX: #2563eb (biru) segitiga atas
- Node MIN: #ef4444 (merah) segitiga bawah
- Terminal nodes: #10b981 (hijau) kotak
- Panah propagasi: #f59e0b (oranye) putus-putus
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Root (MAX): nilai "3" setelah propagasi
2. Level 1 (MIN): 3 node dengan nilai "3", "2", "2"
3. Level 2 (Terminal): nilai [3,12,8], [2,4,6], [14,5,2]
4. Panah menunjukkan propagasi nilai
5. Highlight path optimal
LABEL: "MAX picks max", "MIN picks min", nilai numerik
UKURAN: 900x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Kompleksitas Minimax:**
- **Time:** O(b^m) - eksponensial
- **Space:** O(bm) dengan DFS
- **Complete:** Ya, jika tree finite
- **Optimal:** Ya, melawan lawan optimal

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Minimax Algorithm | Sebastian Lague | 10:00 | https://www.youtube.com/watch?v=l-hh51ncgDI |
| 2 | Minimax Explained | CS Dojo | 20:00 | https://www.youtube.com/watch?v=5oXyibEgJr0 |
| 3 | Minimax for Tic-Tac-Toe | The Coding Train | 20:00 | https://www.youtube.com/watch?v=trKjYdBASyQ |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Minimax Visualization | USFCA | Trace interaktif Minimax | https://www.cs.usfca.edu/~galles/visualization/MinMax.html |
| Minimax Calculator | Raphsilva | Hitung nilai Minimax | https://raphsilva.github.io/utilities/minimax/ |

### ✍️ Latihan Pemahaman

1. Untuk tree dengan terminal values [3,5,2,9], trace Minimax jika root adalah MAX!
2. Mengapa Minimax diasumsikan lawan bermain optimal?
3. Berapa kompleksitas waktu Minimax untuk b=35 dan m=10?

---

## 4. Review Konsep: Alpha-Beta Pruning (45 menit)

### Ringkasan Materi

> **Alpha-Beta Pruning** memotong cabang yang tidak perlu dieksplorasi, tanpa mempengaruhi hasil Minimax!

**Motivasi:** Minimax terlalu lambat karena mengeksplorasi semua node.

**Parameter Alpha dan Beta:**

| Parameter | Definisi | Inisialisasi |
|-----------|----------|--------------|
| **α (alpha)** | Nilai terbaik yang ditemukan MAX | -∞ |
| **β (beta)** | Nilai terbaik yang ditemukan MIN | +∞ |

**Aturan Pruning:**
- Di MAX node: Jika value ≥ β → prune (β cutoff)
- Di MIN node: Jika value ≤ α → prune (α cutoff)
- Kondisi: **α ≥ β** → Prune!

**Pseudocode Alpha-Beta:**
```
function AlphaBeta(node, depth, α, β, maximizingPlayer):
    if depth == 0 or node is terminal:
        return evaluate(node)
    
    if maximizingPlayer:
        value = -infinity
        for each child of node:
            value = max(value, AlphaBeta(child, depth-1, α, β, false))
            α = max(α, value)
            if α >= β:
                break  // β cutoff
        return value
    else:
        value = +infinity
        for each child of node:
            value = min(value, AlphaBeta(child, depth-1, α, β, true))
            β = min(β, value)
            if α >= β:
                break  // α cutoff
        return value
```

![Alpha-Beta Pruning](images/ss05-03-alpha-beta-trace.png)

*Gambar 4.1: Trace Alpha-Beta Pruning dengan cutoff*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Game tree dengan Alpha-Beta pruning menunjukkan cabang yang dipotong
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tree dengan cabang yang dipotong ditandai jelas
WARNA:
- Node MAX: #2563eb (biru)
- Node MIN: #ef4444 (merah)
- Terminal nodes: #10b981 (hijau)
- Pruned branches: #9ca3af (abu-abu) dengan garis coret
- α dan β values: #f59e0b (oranye)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Game tree 3 level
2. Terminal values di daun
3. α dan β values di setiap node
4. Cabang pruned dengan garis coret dan warna abu-abu
5. Label "β cutoff" dan "α cutoff"
LABEL: "α cutoff", "β cutoff", nilai α dan β
UKURAN: 1000x700 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Efisiensi Alpha-Beta:**
- Best case (optimal ordering): O(b^(m/2)) - **dua kali lebih dalam!**
- Worst case (bad ordering): O(b^m) - sama dengan Minimax
- Average case: O(b^(3m/4))

**Move Ordering untuk Optimasi:**
- Evaluasi node dengan heuristik terlebih dahulu
- Explore best moves first untuk maximize pruning

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Alpha-Beta Pruning | Sebastian Lague | 12:00 | https://www.youtube.com/watch?v=l-hh51ncgDI |
| 2 | Alpha Beta Explained | Abdul Bari | 15:00 | https://www.youtube.com/watch?v=xBXHtz4Gbdo |
| 3 | Pruning Visualization | MIT OCW | 20:00 | https://www.youtube.com/watch?v=STjW3eH0Cik |

### ✍️ Latihan Pemahaman

1. Trace Alpha-Beta pada tree dengan terminals [3,5,6,9,1,2,0,7]. Mana yang dipruned?
2. Mengapa move ordering penting untuk Alpha-Beta?
3. Jika best-case Alpha-Beta adalah O(b^(m/2)), berapa improvement untuk b=35, m=10?

---

## 5. Review Konsep: Evaluation Function dan Variasi (45 menit)

### Ringkasan Materi

**Evaluation Function:**
Karena tidak mungkin search hingga terminal untuk game kompleks, kita gunakan **evaluation function** untuk mengestimasi nilai non-terminal state.

$$EVAL(s) \approx UTILITY(s)$$

**Desain Evaluation Function:**
- Harus cepat dihitung
- Harus berkorelasi dengan actual winning probability
- Biasanya linear combination of features

**Contoh untuk Catur:**
$$EVAL(s) = w_1 \cdot material + w_2 \cdot mobility + w_3 \cdot king\_safety + ...$$

Dimana:
- Material: Σ(nilai bidak) - Σ(nilai bidak lawan)
- Mobility: jumlah legal moves
- King safety: perlindungan raja

**Depth-Limited Minimax:**
```
function MinimaxCutoff(node, depth, maximizingPlayer):
    if depth == 0 or node is terminal:
        return EVAL(node)  // gunakan evaluation function
    ...
```

**Expectiminimax untuk Game Stokastik:**
Untuk game dengan elemen acak (dadu, kartu), gunakan expected value:

$$EXPECTIMINIMAX(n) = \sum_i P(i) \cdot MINIMAX(child_i)$$

![Expectiminimax Tree](images/ss05-04-expectiminimax.png)

*Gambar 5.1: Expectiminimax dengan chance nodes*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Expectiminimax tree dengan MAX, MIN, dan CHANCE nodes
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tree dengan tiga jenis node
WARNA:
- Node MAX: #2563eb (biru) segitiga atas
- Node MIN: #ef4444 (merah) segitiga bawah
- Node CHANCE: #10b981 (hijau) lingkaran
- Terminal: kotak dengan nilai
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Root MAX node
2. Level 1: CHANCE nodes dengan probabilitas
3. Level 2: MIN nodes
4. Terminal nodes dengan values
5. Probabilitas pada edge dari CHANCE (1/6, 2/6, dll)
LABEL: "MAX", "MIN", "CHANCE", probabilitas, nilai expected
UKURAN: 900x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

**Aplikasi Pertahanan - Game Theory:**
- **Wargaming:** Simulasi strategi militer dengan adversarial thinking
- **Resource Allocation:** Zero-sum competition untuk resources
- **Cybersecurity:** Defender vs Attacker game

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Evaluation Functions | AI Course | 15:00 | https://www.youtube.com/watch?v=DZfv0YgLJ2Q |
| 2 | Chess AI Deep Dive | Sebastian Lague | 25:00 | https://www.youtube.com/watch?v=U4ogK0MIzqk |
| 3 | Expectiminimax | CS188 | 10:00 | https://www.youtube.com/watch?v=jaFRyzp7yWw |

### ✍️ Latihan Pemahaman

1. Desain evaluation function untuk Tic-Tac-Toe!
2. Mengapa evaluation function harus cepat dihitung?
3. Bagaimana Expectiminimax berbeda dari Minimax standar?

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Kegunaan | Link |
|------|----------|------|
| Minimax Visualizer | Trace algoritma interaktif | https://www.cs.usfca.edu/~galles/visualization/MinMax.html |
| Chess Programming Wiki | Resource untuk chess AI | https://www.chessprogramming.org/ |
| Lichess Bot API | Buat chess bot sendiri | https://lichess.org/api |
| OpenSpiel | Game AI framework Google | https://github.com/deepmind/open_spiel |

### Tugas Eksplorasi

1. Buka **Minimax Visualizer** dan trace beberapa contoh tree
2. Mainkan **Tic-Tac-Toe** melawan AI dan analisis strateginya
3. Baca tentang bagaimana **Deep Blue** mengalahkan Kasparov
4. Refleksikan: Bagaimana adversarial thinking diterapkan dalam strategi militer?

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | How Computers Play Chess | Sebastian Lague | 25:00 | https://www.youtube.com/watch?v=U4ogK0MIzqk |
| 2 | AlphaGo Documentary | DeepMind | 90:00 | https://www.youtube.com/watch?v=WXuK6gekU1Y |
| 3 | Game AI Overview | MIT OCW | 50:00 | https://www.youtube.com/watch?v=STjW3eH0Cik |
| 4 | Monte Carlo Tree Search | Two Minute Papers | 5:00 | https://www.youtube.com/watch?v=Fbs4lnGLS8M |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 5 (Adversarial Search)
- Artikel: "Deep Blue" - IBM Research
- Paper: "Mastering the Game of Go" - DeepMind (2016)

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| CS188 Practice | Game Trees | https://inst.eecs.berkeley.edu/~cs188/ |
| LeetCode | Game Problems | https://leetcode.com/tag/game-theory/ |

### Soal Latihan Mandiri

**Soal 1:** Trace Minimax untuk tree dengan terminal values [[4,6],[2,8],[1,9],[3,5]]. Root adalah MAX.

**Soal 2:** Untuk tree di Soal 1, trace Alpha-Beta dan identifikasi semua pruning!

**Soal 3:** Desain evaluation function untuk game Connect-4 dengan faktor: center control, potential lines, blocking opponent.

**Soal 4:** Dalam wargaming simulasi, dua komandan saling memilih strategi. Formulasikan sebagai zero-sum game dan tentukan optimal strategy menggunakan Minimax!

**Soal 5:** Game Backgammon memiliki dadu. Bagaimana Expectiminimax menangani ini? Berikan contoh perhitungan!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dari materi Pertemuan 05? Mengapa?
2. Bagaimana adversarial search dapat diterapkan dalam simulasi perang?
3. Apakah AI game-playing dapat dianggap "cerdas"? Mengapa?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/chess, r/gamedev, r/artificial
- Stack Overflow: tag [minimax], [alpha-beta-pruning]
- Discord: Chess programming communities

### Topik Diskusi

- Mengapa AlphaGo menggunakan Monte Carlo Tree Search bukan pure Minimax?
- Bagaimana adversarial thinking dapat membantu cybersecurity?
- Apakah game AI dapat digunakan untuk latihan strategi militer?

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Pengantar Game dalam AI selesai
- [ ] Section 2: Review Game Tree dan Formulasi selesai
- [ ] Section 3: Review Algoritma Minimax selesai
- [ ] Section 4: Review Alpha-Beta Pruning selesai
- [ ] Section 5: Review Evaluation Function dan Variasi selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS188: Game Trees | Berkeley | https://inst.eecs.berkeley.edu/~cs188/ |
| Game Theory | Coursera | https://www.coursera.org/learn/game-theory-1 |
| Chess Programming | Chess.com | https://www.chess.com/article/view/chess-engine-programming |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 5.
- Shannon, C. (1950). "Programming a Computer for Playing Chess"
- Campbell et al. (2002). "Deep Blue"

### 🎥 Channel YouTube Rekomendasi

- **Sebastian Lague** - Excellent game AI visualizations
- **The Coding Train** - Interactive coding tutorials
- **Two Minute Papers** - AI research updates
- **Computerphile** - Algorithm explanations

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. Game menjadi testbed karena: aturan jelas, state observable, outcome terukur, kompleksitas tinggi tapi tractable
2. Zero-sum: keuntungan satu pemain = kerugian lawan. Contoh: Catur (menang +1, kalah -1)
3. Poker: Two-player/multi, Imperfect info (kartu tersembunyi), Stochastic (kartu acak), bisa non-zero-sum

### Section 2
1. Gambar tree dengan root → 2 children → 4 grandchildren (terminal)
2. Chess tree size ~10^154, komputer tercepat ~10^18 ops/detik → butuh lebih dari umur alam semesta
3. MAX node: memilih nilai tertinggi dari children. MIN node: memilih nilai terendah dari children

### Section 3
1. Terminal [3,5,2,9]: MIN level picks min(3,5)=3 dan min(2,9)=2. MAX root picks max(3,2)=3
2. Asumsi lawan optimal = worst-case analysis, menjamin kita tidak kalah jika ada winning strategy
3. O(35^10) = O(2.76 × 10^15) - sangat besar!

### Section 4
1. Dengan α=-∞, β=+∞ trace step-by-step. Pruning terjadi ketika α≥β
2. Move ordering baik → lebih banyak pruning → lebih cepat. Best moves first maximize cutoffs
3. Without AB: O(35^10). With best AB: O(35^5) ≈ 52 juta. Improvement: ~50 juta kali lebih cepat!

### Section 5
1. EVAL(s) = 3×(lines dengan 2 X dan 1 kosong) + 1×(lines dengan 1 X) - sama untuk O
2. Dipanggil jutaan kali, sedikit delay = sangat lambat keseluruhan
3. Expectiminimax menambahkan CHANCE nodes yang menghitung expected value dari semua kemungkinan hasil acak

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
