# Panduan Belajar Mandiri Pertemuan 04: Pencarian Lokal dan Optimisasi

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 04  
**Topik:** Pencarian Lokal dan Optimisasi  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Menjelaskan perbedaan pencarian lokal dengan pencarian sistematis
2. Mengimplementasikan algoritma Hill Climbing dan variasinya
3. Menjelaskan dan menerapkan Simulated Annealing
4. Memahami komponen Algoritma Genetika (seleksi, crossover, mutasi)
5. Menerapkan algoritma pencarian lokal untuk masalah optimisasi pertahanan

---

## 1. Review Konsep: Pencarian Lokal vs Sistematis (45 menit)

### Ringkasan Materi

**Pencarian Lokal** berbeda fundamental dari pencarian sistematis (BFS, DFS, A*):

| Aspek | Pencarian Sistematis | Pencarian Lokal |
|-------|---------------------|-----------------|
| **Tujuan** | Menemukan path ke goal | Menemukan state terbaik |
| **Memory** | Menyimpan banyak node | Hanya state saat ini |
| **Path** | Penting (solusi = path) | Tidak penting |
| **Completeness** | Biasanya complete | Tidak dijamin |
| **Contoh** | BFS, DFS, A* | Hill Climbing, SA, GA |

**Kapan menggunakan Local Search:**
- Hanya state akhir yang penting (bukan path)
- Masalah optimisasi (maximization/minimization)
- State space sangat besar atau infinite
- Memori terbatas

**Optimization Landscape** adalah visualisasi objective function:
- **Global Maximum:** Titik tertinggi di seluruh landscape
- **Local Maximum:** Titik tertinggi di sekitarnya, tapi bukan global
- **Plateau:** Area datar dimana semua neighbor sama nilainya
- **Ridge:** Area sempit yang tinggi, sulit diikuti

![Optimization Landscape](images/ss04-01-optimization-landscape.png)

*Gambar 1.1: Optimization landscape dengan local/global maxima*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Landscape optimisasi 2D dengan local maxima, global maximum, plateau, ridge
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
TATA LETAK: Grafik garis dengan sumbu x (state space) dan sumbu y (objective function)
WARNA:
- Garis landscape: #2563eb (biru) solid tebal
- Global maximum: #10b981 (hijau) dengan bintang
- Local maxima: #f59e0b (oranye) dengan titik
- Plateau: #8b5cf6 (ungu) area datar
- Current state: #ef4444 (merah) dengan panah
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Kurva bergelombang dengan beberapa puncak dan lembah
2. Puncak tertinggi ditandai "Global Maximum" dengan bintang hijau
3. Dua puncak lebih rendah ditandai "Local Maximum"
4. Area datar di tengah ditandai "Plateau"
5. Area sempit ditandai "Ridge"
LABEL: "Global Maximum", "Local Maximum", "Plateau", "Ridge", "State Space", "f(x)"
UKURAN: 900x500 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Local Search Algorithms | Gate Smashers | 15:00 | https://www.youtube.com/watch?v=yF7rOH5Ts68 |
| 2 | Optimization Landscape Explained | 3Blue1Brown | 20:00 | https://www.youtube.com/watch?v=IHZwWFHWa-w |
| 3 | Hill Climbing Introduction | Abdul Bari | 12:00 | https://www.youtube.com/watch?v=oSdPmxRCWws |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Visualisasi Landscape | Desmos | Plot fungsi dan identifikasi local/global maxima | https://www.desmos.com/calculator |
| Optimization Demo | Algorithm Visualizer | Lihat algoritma optimisasi beraksi | https://algorithm-visualizer.org/ |

### ✍️ Latihan Pemahaman

1. Kapan pencarian lokal lebih cocok daripada A*?
2. Apa perbedaan local maximum dan global maximum?
3. Mengapa path tidak penting dalam pencarian lokal?

---

## 2. Review Konsep: Hill Climbing (45 menit)

### Ringkasan Materi

> **Hill Climbing** adalah algoritma yang secara iteratif bergerak ke arah yang meningkatkan nilai objective function, seperti mendaki bukit dalam kabut.

**Pseudocode:**
```
function HILL-CLIMBING(problem):
    current = problem.INITIAL-STATE
    while true:
        neighbor = highest-valued successor of current
        if neighbor.VALUE ≤ current.VALUE:
            return current  // stuck at local maximum
        current = neighbor
```

**Variasi Hill Climbing:**

| Variasi | Deskripsi | Kelebihan |
|---------|-----------|-----------|
| Steepest-Ascent | Pilih neighbor terbaik | Deterministik |
| First-Choice | Pilih neighbor pertama yang lebih baik | Lebih cepat |
| Stochastic | Pilih secara probabilistik | Menghindari pattern |
| Random-Restart | Ulang dari posisi random jika stuck | Meningkatkan success rate |

**Masalah Hill Climbing:**
- **Local Maxima:** Terjebak di puncak lokal, bukan global
- **Plateau:** Area datar, tidak tahu ke mana harus bergerak
- **Ridge:** Area sempit, sulit diikuti dengan langkah diskret

![Hill Climbing Variants](images/ss04-02-hill-climbing-variants.png)

*Gambar 2.1: Variasi Hill Climbing dan masalahnya*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram variasi Hill Climbing menunjukkan Steepest-Ascent, First-Choice, Random-Restart
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Tiga panel horizontal menunjukkan skenario berbeda
WARNA:
- Landscape: #2563eb (biru) solid
- Current state: #ef4444 (merah) titik
- Path: #10b981 (hijau) garis putus-putus
- Local maxima: #f59e0b (oranye)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Panel 1: Steepest-Ascent memilih neighbor terbaik
2. Panel 2: First-Choice memilih neighbor pertama yang lebih baik
3. Panel 3: Random-Restart dari posisi berbeda
LABEL: "Steepest-Ascent", "First-Choice", "Random-Restart"
UKURAN: 900x400 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Hill Climbing Algorithm | Abdul Bari | 12:00 | https://www.youtube.com/watch?v=oSdPmxRCWws |
| 2 | 8-Queens with Hill Climbing | AI Course | 10:00 | https://www.youtube.com/watch?v=kXnMluDzlvE |
| 3 | Local Maxima Problem | Computerphile | 8:00 | https://www.youtube.com/watch?v=cY2SPVeXjns |

### ✍️ Latihan Pemahaman

1. Mengapa Hill Climbing bisa stuck di local maximum?
2. Bagaimana Random-Restart membantu mengatasi local maxima?
3. Untuk fungsi f(x) = -(x-3)² + 10, jika mulai dari x=0, trace langkah Hill Climbing!

---

## 3. Review Konsep: Simulated Annealing (45 menit)

### Ringkasan Materi

> **Simulated Annealing (SA)** terinspirasi dari proses annealing dalam metalurgi—pemanasan logam kemudian pendinginan perlahan untuk mencapai struktur kristal optimal.

**Ide Kunci:** Mengizinkan langkah "buruk" dengan probabilitas tertentu untuk keluar dari local optima.

**Probabilitas Acceptance:**
$$P(accept) = \begin{cases} 1 & \text{if } \Delta E > 0 \\ e^{\Delta E / T} & \text{if } \Delta E \leq 0 \end{cases}$$

dimana:
- ΔE = nilai neighbor - nilai current
- T = temperature (parameter yang menurun seiring waktu)

**Pseudocode:**
```
function SIMULATED-ANNEALING(problem, schedule):
    current = problem.INITIAL-STATE
    for t = 1 to ∞:
        T = schedule(t)
        if T = 0: return current
        next = random neighbor of current
        ΔE = VALUE(next) - VALUE(current)
        if ΔE > 0:
            current = next
        else:
            current = next with probability e^(ΔE/T)
```

**Cooling Schedule:**
- **Linear:** T(t) = T₀ - αt
- **Geometric:** T(t) = T₀ × α^t (paling umum, α ≈ 0.95)
- **Logarithmic:** T(t) = T₀ / log(t + 1)

![Simulated Annealing Process](images/ss04-03-simulated-annealing.png)

*Gambar 3.1: Proses Simulated Annealing dengan cooling schedule*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram proses Simulated Annealing menunjukkan eksplorasi pada T tinggi dan eksploitasi pada T rendah
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Dua panel atas-bawah dengan grafik cooling di samping
WARNA:
- Landscape: #2563eb (biru) solid
- Path T tinggi: #ef4444 (merah) garis zigzag
- Path T rendah: #10b981 (hijau) garis smooth
- Temperature curve: #f59e0b (oranye)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Panel atas: T tinggi - path acak, banyak eksplorasi
2. Panel bawah: T rendah - path lebih fokus ke puncak
3. Grafik samping: Temperature vs Time menurun
LABEL: "High Temperature (Exploration)", "Low Temperature (Exploitation)", "Cooling Schedule"
UKURAN: 900x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Simulated Annealing Explained | Reducible | 18:00 | https://www.youtube.com/watch?v=eBmU1ONJ-os |
| 2 | SA for TSP | AI Warehouse | 12:00 | https://www.youtube.com/watch?v=SC5CX8drAtU |
| 3 | Cooling Schedule Design | MIT OCW | 15:00 | https://www.youtube.com/watch?v=6gPCJhg6TGE |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| SA Visualization | TSP Solver | Lihat SA solve TSP secara visual | https://tspvis.com/ |
| Interactive SA | Observable | Eksperimen dengan parameter SA | https://observablehq.com/@mbostock/simulated-annealing |

### ✍️ Latihan Pemahaman

1. Mengapa SA dapat keluar dari local optima sedangkan Hill Climbing tidak?
2. Jika T=100, current=50, neighbor=45, berapa P(accept) untuk minimization problem?
3. Bagaimana cooling schedule mempengaruhi perilaku SA?

---

## 4. Review Konsep: Algoritma Genetika (45 menit)

### Ringkasan Materi

> **Algoritma Genetika (GA)** terinspirasi dari evolusi biologi—populasi individu berevolusi melalui seleksi, crossover, dan mutasi.

**Komponen GA:**

| Komponen | Biologi | GA |
|----------|---------|-----|
| **Kromosom** | DNA | Representasi solusi |
| **Gen** | Segment DNA | Variabel/parameter |
| **Fitness** | Survival ability | Nilai objective function |
| **Seleksi** | Natural selection | Pilih parent untuk reproduksi |
| **Crossover** | Sexual reproduction | Kombinasi dua parent |
| **Mutasi** | Random mutation | Perubahan acak kecil |

**Pseudocode:**
```
function GENETIC-ALGORITHM(population, fitness):
    while not termination-condition:
        new_population = []
        for i = 1 to SIZE(population)/2:
            parent1 = SELECT(population, fitness)
            parent2 = SELECT(population, fitness)
            child1, child2 = CROSSOVER(parent1, parent2)
            child1 = MUTATE(child1)
            child2 = MUTATE(child2)
            add child1, child2 to new_population
        population = new_population
    return best individual in population
```

**Metode Seleksi:**
- **Roulette Wheel:** Probabilitas ∝ fitness
- **Tournament:** Pilih terbaik dari subset random
- **Rank-based:** Probabilitas berdasarkan ranking

**Operator Crossover:**
- **Single-point:** Potong di satu titik, tukar
- **Two-point:** Potong di dua titik, tukar bagian tengah
- **Uniform:** Setiap gen dipilih random dari salah satu parent

![Genetic Algorithm Flow](images/ss04-04-genetic-algorithm.png)

*Gambar 4.1: Alur Algoritma Genetika*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram alur Algoritma Genetika menunjukkan siklus evolusi
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks
TATA LETAK: Flowchart circular dengan langkah-langkah GA
WARNA:
- Population: #2563eb (biru)
- Selection: #10b981 (hijau)
- Crossover: #f59e0b (oranye)
- Mutation: #ef4444 (merah)
- Arrows: #6b7280 (abu-abu)
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Box "Initial Population" di atas
2. Box "Fitness Evaluation"
3. Box "Selection" dengan ikon filter
4. Box "Crossover" dengan ikon DNA bersilang
5. Box "Mutation" dengan ikon perubahan kecil
6. Box "New Population"
7. Arrow kembali ke Fitness Evaluation
LABEL: "Population", "Fitness Evaluation", "Selection", "Crossover", "Mutation", "New Generation"
UKURAN: 800x700 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Genetic Algorithm Explained | The Coding Train | 25:00 | https://www.youtube.com/watch?v=uQj5UNhCPuo |
| 2 | GA for Optimization | Computerphile | 12:00 | https://www.youtube.com/watch?v=nhT56blfRpE |
| 3 | 8-Queens with GA | AI Warehouse | 15:00 | https://www.youtube.com/watch?v=HDgcLO3Dkx4 |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Genetic Cars | BoxCar2D | Lihat GA evolusi mobil | https://rednuht.org/genetic_cars_2/ |
| TSP with GA | Shinyapps | Interactive GA untuk TSP | https://jbocinsky.shinyapps.io/ga-tsp/ |
| Genetic Walkers | Evolution Sim | Makhluk belajar berjalan | https://keiwan.itch.io/evolution |

### ✍️ Latihan Pemahaman

1. Apa peran mutasi dalam GA? Mengapa diperlukan?
2. Jelaskan perbedaan single-point dan two-point crossover!
3. Untuk populasi dengan fitness [6, 4, 3, 2], hitung probabilitas roulette wheel!

---

## 5. Review Konsep: Aplikasi dan Perbandingan (45 menit)

### Ringkasan Materi

**Perbandingan Algoritma:**

| Kriteria | Hill Climbing | Simulated Annealing | Genetic Algorithm |
|----------|--------------|---------------------|-------------------|
| **Simplicity** | ⭐⭐⭐ | ⭐⭐ | ⭐ |
| **Escape Local Optima** | ❌ | ✅ | ✅ |
| **Memory** | O(1) | O(1) | O(pop_size) |
| **Parameter Tuning** | Minimal | Medium | Banyak |
| **Best for** | Simple landscapes | Complex landscapes | Very complex |

**Aplikasi Pertahanan:**

| Aplikasi | Algoritma Cocok | Alasan |
|----------|-----------------|--------|
| Route Optimization Konvoi | SA | Balance distance dan risk |
| Sensor Placement | GA | Multi-objective optimization |
| Resource Allocation | GA | Many constraints |
| UAV Mission Planning | SA/GA | Complex dengan time windows |

**Contoh: N-Queens Problem**

| Algoritma | Success Rate (8-Queens) | Average Steps |
|-----------|------------------------|---------------|
| Hill Climbing | 14% | 4 steps |
| Random Restart HC | ~100% | 7 restarts |
| Simulated Annealing | ~100% | Varies with schedule |
| Genetic Algorithm | ~100% | 50-100 generations |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Comparing Local Search | MIT OCW | 20:00 | https://www.youtube.com/watch?v=6gPCJhg6TGE |
| 2 | When to Use Which Algorithm | AI Explained | 15:00 | https://www.youtube.com/watch?v=EddVvhT2g-k |
| 3 | Real-World Optimization | Google Developers | 12:00 | https://www.youtube.com/watch?v=il_t1WVLNxk |

### ✍️ Latihan Pemahaman

1. Kapan sebaiknya menggunakan GA daripada SA?
2. Mengapa Hill Climbing tidak cocok untuk landscape dengan banyak local optima?
3. Algoritma mana yang paling cocok untuk optimisasi penempatan radar pertahanan?

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Kegunaan | Link |
|------|----------|------|
| N-Queens Visualizer | Lihat HC dan SA solve N-Queens | https://algorithm-visualizer.org/ |
| Genetic Cars | GA evolusi mobil 2D | https://rednuht.org/genetic_cars_2/ |
| TSP Solver | Compare berbagai algoritma TSP | https://tspvis.com/ |
| DEAP Framework | Library Python untuk GA | https://deap.readthedocs.io/ |

### Tugas Eksplorasi

1. Buka **Genetic Cars** dan jalankan simulasi, perhatikan bagaimana mobil berevolusi
2. Coba **TSP Solver** dengan SA dan GA, bandingkan hasilnya
3. Buka **N-Queens Visualizer** dan bandingkan HC vs SA
4. Refleksikan: Mengapa GA bisa menemukan desain mobil yang tidak terpikirkan manusia?

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Optimization Algorithms Series | 3Blue1Brown | 20:00 | https://www.youtube.com/watch?v=IHZwWFHWa-w |
| 2 | Metaheuristics Explained | AI Explained | 25:00 | https://www.youtube.com/watch?v=GGy-7T_4sVA |
| 3 | Real-World Applications | Two Minute Papers | 10:00 | https://www.youtube.com/watch?v=7T_0Qtp4hBs |
| 4 | Evolving Neural Networks | CodeBullet | 15:00 | https://www.youtube.com/watch?v=qv6UVOQ0F44 |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 4.1-4.2 (Local Search and Optimization)
- Artikel: "Optimization by Simulated Annealing" - Kirkpatrick et al. (1983)
- Tutorial: DEAP Documentation - Genetic Algorithm in Python

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| CS188 Practice | Local Search | https://inst.eecs.berkeley.edu/~cs188/ |
| LeetCode | Optimization Problems | https://leetcode.com/tag/simulation/ |

### Soal Latihan Mandiri

**Soal 1:** Diberikan fungsi f(x) = -x² + 6x - 5 dengan domain x ∈ {0,1,2,3,4,5}. 
a) Identifikasi global maximum
b) Trace Hill Climbing dari x=0

**Soal 2:** Dalam SA dengan T=50, current=30, neighbor=25, hitung P(accept) untuk maximization problem!

**Soal 3:** Desain representasi kromosom untuk masalah penempatan 5 radar di area 10x10 grid dengan constraint jarak minimum!

**Soal 4:** Sebuah konvoi TNI harus mengunjungi 8 checkpoint. Formulasikan sebagai problem local search dan tentukan algoritma terbaik!

**Soal 5:** Bandingkan kompleksitas memori dan waktu antara Hill Climbing, SA, dan GA untuk problem dengan n variabel!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dari materi Pertemuan 04? Mengapa?
2. Bagaimana algoritma local search dapat diterapkan untuk optimisasi operasi militer?
3. Menurut Anda, kapan sebaiknya menggunakan pendekatan deterministik (A*) vs stokastik (SA/GA)?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/MachineLearning, r/optimization
- Stack Overflow: tag [simulated-annealing], [genetic-algorithm]
- Discord: AI/ML community servers

### Topik Diskusi

- Bagaimana GA bisa "menemukan" solusi yang tidak terpikirkan manusia?
- Apakah etis menggunakan "evolution" untuk mengoptimasi sistem senjata?
- Bagaimana memilih parameter cooling schedule yang optimal?

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Pencarian Lokal vs Sistematis selesai
- [ ] Section 2: Review Hill Climbing selesai
- [ ] Section 3: Review Simulated Annealing selesai
- [ ] Section 4: Review Algoritma Genetika selesai
- [ ] Section 5: Review Aplikasi dan Perbandingan selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| Optimization Methods | MIT OCW | https://ocw.mit.edu/courses/15-053-optimization-methods-in-management-science-spring-2013/ |
| Metaheuristics | Coursera | https://www.coursera.org/learn/discrete-optimization |
| Evolutionary Computation | edX | https://www.edx.org/course/evolutionary-computation |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 4.
- Kirkpatrick et al. (1983). "Optimization by Simulated Annealing"
- Holland, J.H. (1992). "Genetic Algorithms"

### 🎥 Channel YouTube Rekomendasi

- **The Coding Train** - GA tutorials with visualization
- **Computerphile** - Algorithm explanations
- **3Blue1Brown** - Mathematical visualizations
- **CodeBullet** - Fun AI experiments

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. Pencarian lokal lebih cocok ketika: path tidak penting, hanya solusi akhir; state space sangat besar; memori terbatas
2. Local maximum: titik tertinggi di sekitarnya tapi bukan tertinggi secara global. Global maximum: titik tertinggi di seluruh landscape
3. Karena tujuannya adalah menemukan state terbaik, bukan urutan langkah untuk mencapainya

### Section 2
1. Hill Climbing hanya menerima langkah yang meningkatkan nilai, jadi jika semua neighbor lebih buruk, akan berhenti meskipun belum global optimum
2. Random-Restart mencoba dari titik awal berbeda, sehingga meningkatkan peluang menemukan basin yang mengarah ke global optimum
3. f(0)=1, f(1)=6, f(2)=9, f(3)=10, f(4)=9. Dari x=0→1→2→3, berhenti di x=3 (global max)

### Section 3
1. SA mengizinkan langkah "buruk" dengan probabilitas e^(ΔE/T), memungkinkan escape dari local optima
2. Untuk minimization: ΔE = current - neighbor = 50-45 = +5 (bagus!), P=1. Atau jika neighbor lebih buruk: P = e^(-5/100) = 0.951
3. T tinggi → lebih banyak eksplorasi (terima langkah buruk). T rendah → lebih fokus eksploitasi (hanya terima langkah baik)

### Section 4
1. Mutasi mempertahankan diversity dan mencegah konvergensi prematur ke local optimum
2. Single-point: satu titik potong, tukar bagian kanan. Two-point: dua titik potong, tukar bagian tengah
3. Total fitness = 15. P(1)=6/15=0.4, P(2)=4/15=0.27, P(3)=3/15=0.2, P(4)=2/15=0.13

### Section 5
1. GA cocok untuk: banyak local optima, multi-objective, representasi kompleks, parallel processing tersedia
2. Hill Climbing akan terjebak di local optima pertama yang ditemukan, tanpa kemampuan escape
3. GA paling cocok karena multi-objective (coverage, interference, terrain) dan banyak constraint

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
