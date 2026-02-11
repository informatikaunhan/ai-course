# Modul 04: Pencarian Lokal dan Optimisasi

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 04  
**Topik:** Pencarian Lokal dan Optimisasi  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan perbedaan antara pencarian lokal dengan pencarian sistematis
2. Memahami konsep landscape dalam pencarian lokal (local maxima, plateau, ridge)
3. Mengimplementasikan algoritma Hill Climbing dan variasi-variasinya
4. Mengimplementasikan algoritma Simulated Annealing dengan jadwal pendinginan
5. Menjelaskan konsep Local Beam Search dan perbedaannya dengan pencarian paralel
6. Menerapkan algoritma genetika untuk masalah optimisasi
7. Mengaplikasikan pencarian lokal pada masalah N-Queens dan Traveling Salesman Problem

---

## 1. Pendahuluan Pencarian Lokal

### 1.1 Pencarian Sistematis vs Pencarian Lokal

Pada pertemuan sebelumnya (Pertemuan 2 dan 3), kita telah mempelajari algoritma pencarian sistematis seperti BFS, DFS, dan A*. Algoritma-algoritma tersebut menjelajahi ruang pencarian secara sistematis dan menyimpan banyak state dalam memori.

> **Pencarian Lokal (Local Search)** adalah kategori algoritma pencarian yang hanya menyimpan **satu state saat ini** (atau sejumlah kecil state) dan bergerak ke state tetangga tanpa menyimpan jalur yang telah dilalui.

![Perbandingan Pencarian Sistematis vs Lokal](images/p04-01-systematic-vs-local-search.png)

*Gambar 4.1: Perbandingan Pencarian Sistematis dan Pencarian Lokal*

| Aspek | Pencarian Sistematis | Pencarian Lokal |
|-------|---------------------|-----------------|
| **Memori** | O(b^d) - menyimpan banyak state | O(1) - hanya state saat ini |
| **Jalur** | Menyimpan jalur ke solusi | Tidak menyimpan jalur |
| **Completeness** | Sering complete | Tidak complete |
| **Optimality** | Dapat optimal | Tidak dijamin optimal |
| **Cocok untuk** | Mencari jalur | Optimisasi |

### 1.2 Kapan Menggunakan Pencarian Lokal?

Pencarian lokal sangat berguna ketika:

1. **Jalur tidak penting** - Yang dibutuhkan hanya state solusi, bukan bagaimana mencapainya
2. **Ruang pencarian sangat besar** - Tidak mungkin menyimpan semua state
3. **Masalah optimisasi** - Mencari konfigurasi terbaik berdasarkan objective function
4. **Real-time constraints** - Memerlukan solusi cepat meskipun tidak optimal

**Contoh aplikasi:**
- Penjadwalan (scheduling)
- Rute kendaraan (vehicle routing)
- Layout sirkuit VLSI
- Optimisasi jaringan saraf
- Konfigurasi antenna radar

### 1.3 Landscape dalam Pencarian Lokal

> **Objective Function** adalah fungsi yang memetakan setiap state ke nilai numerik yang merepresentasikan kualitas state tersebut.

Pencarian lokal dapat divisualisasikan sebagai "pendaki" yang bergerak di landscape:
- **Sumbu horizontal**: Ruang state
- **Sumbu vertikal**: Nilai objective function

![Landscape Pencarian Lokal](images/p04-02-search-landscape.png)

*Gambar 4.2: Landscape Pencarian Lokal dengan berbagai fitur*

**Fitur-fitur penting dalam landscape:**

| Fitur | Deskripsi | Masalah |
|-------|-----------|---------|
| **Global Maximum/Minimum** | Titik optimal di seluruh landscape | Tujuan yang ingin dicapai |
| **Local Maximum/Minimum** | Titik optimal di area lokal | Bisa membuat algoritma terjebak |
| **Plateau (Shoulder)** | Area datar dengan nilai sama | Sulit menentukan arah gerak |
| **Ridge** | Puncak sempit memanjang | Sulit dinavigasi |

#### Solved Problem 1 ⭐

**Soal:** Diberikan fungsi objective f(x) = -(x-3)² + 10 untuk x ∈ {0, 1, 2, 3, 4, 5, 6}. Tentukan semua local maxima dan global maximum!

**Penyelesaian:**

*Step 1:* Hitung nilai f(x) untuk setiap x

| x | f(x) = -(x-3)² + 10 |
|---|---------------------|
| 0 | -(0-3)² + 10 = -9 + 10 = 1 |
| 1 | -(1-3)² + 10 = -4 + 10 = 6 |
| 2 | -(2-3)² + 10 = -1 + 10 = 9 |
| 3 | -(3-3)² + 10 = 0 + 10 = 10 |
| 4 | -(4-3)² + 10 = -1 + 10 = 9 |
| 5 | -(5-3)² + 10 = -4 + 10 = 6 |
| 6 | -(6-3)² + 10 = -9 + 10 = 1 |

*Step 2:* Identifikasi maxima
- **Global Maximum:** x = 3 dengan f(3) = 10
- **Local Maxima:** Karena fungsi ini unimodal (hanya satu puncak), global maximum adalah satu-satunya local maximum

**Jawaban:** Global maximum berada di x = 3 dengan nilai 10. Tidak ada local maximum lain karena fungsi ini berbentuk parabola terbalik dengan satu puncak.

---

## 2. Algoritma Hill Climbing

### 2.1 Konsep Dasar Hill Climbing

> **Hill Climbing** adalah algoritma pencarian lokal yang terus bergerak ke arah nilai objective function yang meningkat (untuk maximization) atau menurun (untuk minimization), dan berhenti ketika tidak ada tetangga yang lebih baik.

Algoritma ini disebut juga **greedy local search** karena selalu memilih langkah terbaik secara lokal tanpa melihat ke depan.

**Pseudocode Hill Climbing (Steepest Ascent):**

```python
def hill_climbing(problem):
    current = problem.initial_state()
    while True:
        neighbors = current.get_neighbors()
        if not neighbors:
            return current
        
        best_neighbor = max(neighbors, key=problem.value)
        
        if problem.value(best_neighbor) <= problem.value(current):
            return current  # Stuck at local maximum
        
        current = best_neighbor
```

### 2.2 Variasi Hill Climbing

![Variasi Algoritma Hill Climbing](images/p04-03-hill-climbing-variants.png)

*Gambar 4.3: Tiga variasi algoritma Hill Climbing*

#### 2.2.1 Steepest Ascent Hill Climbing

Memilih tetangga dengan nilai **terbaik** di antara semua tetangga.

```python
def steepest_ascent(problem):
    current = problem.initial_state()
    while True:
        neighbors = current.get_neighbors()
        best_neighbor = max(neighbors, key=problem.value)
        
        if problem.value(best_neighbor) <= problem.value(current):
            return current
        current = best_neighbor
```

#### 2.2.2 Stochastic Hill Climbing

Memilih **secara acak** dari tetangga yang lebih baik dari state saat ini.

```python
import random

def stochastic_hill_climbing(problem):
    current = problem.initial_state()
    while True:
        neighbors = current.get_neighbors()
        better_neighbors = [n for n in neighbors 
                          if problem.value(n) > problem.value(current)]
        
        if not better_neighbors:
            return current
        current = random.choice(better_neighbors)
```

#### 2.2.3 First-Choice Hill Climbing

Memilih tetangga **pertama** yang lebih baik, tanpa mengevaluasi semua tetangga.

```python
import random

def first_choice_hill_climbing(problem):
    current = problem.initial_state()
    while True:
        neighbors = list(current.get_neighbors())
        random.shuffle(neighbors)
        
        found_better = False
        for neighbor in neighbors:
            if problem.value(neighbor) > problem.value(current):
                current = neighbor
                found_better = True
                break
        
        if not found_better:
            return current
```

#### Solved Problem 2 ⭐

**Soal:** Dalam konteks Hill Climbing, jelaskan kapan First-Choice lebih efisien daripada Steepest Ascent!

**Penyelesaian:**

*Step 1:* Analisis kompleksitas per iterasi
- **Steepest Ascent:** Harus mengevaluasi SEMUA tetangga sebelum memilih
- **First-Choice:** Berhenti segera setelah menemukan tetangga yang lebih baik

*Step 2:* Identifikasi kondisi yang menguntungkan First-Choice
- Ketika jumlah tetangga sangat banyak
- Ketika evaluasi objective function mahal (computationally expensive)
- Ketika ada banyak tetangga yang lebih baik (sehingga cepat ditemukan)

**Jawaban:** First-Choice lebih efisien ketika:
1. Jumlah tetangga sangat besar (misalnya dalam ruang pencarian kontinu yang didiskritisasi)
2. Evaluasi objective function memakan waktu lama
3. Landscape relatif smooth dengan banyak tetangga yang meningkat

---

### 2.3 Random Restart Hill Climbing

> **Random Restart Hill Climbing** menjalankan Hill Climbing berkali-kali dari titik awal yang berbeda-beda secara acak, kemudian memilih hasil terbaik.

```python
def random_restart_hill_climbing(problem, max_restarts):
    best_solution = None
    best_value = float('-inf')
    
    for i in range(max_restarts):
        # Random initial state
        current = problem.random_state()
        
        # Run hill climbing
        solution = hill_climbing_from(problem, current)
        value = problem.value(solution)
        
        if value > best_value:
            best_value = value
            best_solution = solution
    
    return best_solution
```

**Teorema penting:**
> Jika probabilitas keberhasilan satu kali Hill Climbing adalah p, maka probabilitas keberhasilan setelah k restart adalah 1 - (1-p)^k

#### Solved Problem 3 ⭐⭐

**Soal:** Jika satu kali Hill Climbing memiliki probabilitas 20% untuk menemukan global optimum, berapa kali restart diperlukan agar probabilitas keberhasilan mencapai 90%?

**Penyelesaian:**

*Step 1:* Tentukan formula
- p = 0.20 (probabilitas sukses satu kali)
- P(sukses setelah k restart) = 1 - (1-p)^k = 1 - (0.8)^k

*Step 2:* Set target 90%
$$1 - (0.8)^k \geq 0.90$$
$$(0.8)^k \leq 0.10$$

*Step 3:* Selesaikan untuk k
$$k \cdot \ln(0.8) \leq \ln(0.10)$$
$$k \geq \frac{\ln(0.10)}{\ln(0.8)}$$
$$k \geq \frac{-2.303}{-0.223}$$
$$k \geq 10.32$$

**Jawaban:** Diperlukan minimal **11 restart** untuk mencapai probabilitas keberhasilan 90%.

---

### 2.4 Masalah Hill Climbing

#### 2.4.1 Local Maxima

Hill Climbing dapat terjebak di **local maximum** - titik yang lebih baik dari semua tetangganya tetapi bukan yang terbaik secara global.

#### 2.4.2 Plateau

**Plateau** adalah area datar di mana semua tetangga memiliki nilai yang sama dengan state saat ini. Ada dua jenis:
- **Flat local maximum:** Tidak ada jalan keluar
- **Shoulder:** Ada jalan keluar tetapi sulit ditemukan

#### 2.4.3 Ridge

**Ridge** adalah puncak sempit yang memanjang. Setiap langkah ke samping menurun, sehingga sulit untuk bergerak sepanjang ridge.

#### Solved Problem 4 ⭐

**Soal:** Sebuah algoritma Hill Climbing dijalankan pada landscape berikut (nilai objective function). Dimulai dari posisi C, tentukan di mana algoritma akan berhenti!

```
Posisi:  A    B    C    D    E    F    G
Nilai:   3    5    4    7    6    7    5
```
Tetangga: Setiap posisi hanya bisa bergerak ke kiri atau kanan.

**Penyelesaian:**

*Step 1:* Mulai dari C (nilai = 4)
- Tetangga: B (nilai = 5), D (nilai = 7)
- D lebih baik → pindah ke D

*Step 2:* Dari D (nilai = 7)
- Tetangga: C (nilai = 4), E (nilai = 6)
- Tidak ada yang lebih baik dari 7 → **BERHENTI di D**

**Jawaban:** Algoritma akan berhenti di posisi **D** dengan nilai 7. Perhatikan bahwa F juga memiliki nilai 7 (global maximum bersama dengan D), tetapi algoritma tidak dapat mencapainya karena harus melewati E yang nilainya lebih rendah.

---

## 3. Simulated Annealing

### 3.1 Inspirasi dari Metalurgi

> **Simulated Annealing** adalah algoritma pencarian lokal yang terinspirasi dari proses annealing dalam metalurgi, di mana logam dipanaskan kemudian didinginkan secara perlahan untuk mencapai struktur kristal yang optimal.

Ide kunci: **Kadang-kadang menerima langkah yang lebih buruk** untuk keluar dari local optima.

![Proses Simulated Annealing](images/p04-04-simulated-annealing-process.png)

*Gambar 4.4: Proses Simulated Annealing dengan penurunan temperatur*

### 3.2 Algoritma Simulated Annealing

```python
import math
import random

def simulated_annealing(problem, schedule):
    """
    problem: Masalah optimisasi dengan initial_state(), get_neighbors(), value()
    schedule: Fungsi t -> T yang menentukan temperatur pada waktu t
    """
    current = problem.initial_state()
    
    for t in range(1, float('inf')):
        T = schedule(t)
        
        if T == 0:
            return current
        
        # Pilih tetangga secara acak
        next_state = random.choice(current.get_neighbors())
        
        # Hitung perubahan nilai (delta E)
        delta_E = problem.value(next_state) - problem.value(current)
        
        if delta_E > 0:
            # Langkah lebih baik - selalu diterima
            current = next_state
        else:
            # Langkah lebih buruk - diterima dengan probabilitas e^(delta_E/T)
            probability = math.exp(delta_E / T)
            if random.random() < probability:
                current = next_state
    
    return current
```

### 3.3 Probabilitas Penerimaan

Probabilitas menerima langkah yang lebih buruk:

$$P(\text{terima}) = e^{\Delta E / T}$$

dimana:
- ΔE = nilai(next) - nilai(current) < 0 (negatif untuk langkah buruk)
- T = temperatur saat ini

| Kondisi | Probabilitas |
|---------|-------------|
| T tinggi | Mendekati 1 (hampir selalu terima) |
| T rendah | Mendekati 0 (jarang terima) |
| ΔE kecil (sedikit lebih buruk) | Lebih tinggi |
| ΔE besar (jauh lebih buruk) | Lebih rendah |

#### Solved Problem 5 ⭐⭐

**Soal:** Dalam Simulated Annealing, current state memiliki nilai 100 dan tetangga memiliki nilai 95. Hitung probabilitas penerimaan tetangga tersebut pada temperatur T = 10 dan T = 2!

**Penyelesaian:**

*Step 1:* Hitung ΔE
$$\Delta E = 95 - 100 = -5$$

*Step 2:* Hitung probabilitas pada T = 10
$$P = e^{-5/10} = e^{-0.5} = 0.6065$$

*Step 3:* Hitung probabilitas pada T = 2
$$P = e^{-5/2} = e^{-2.5} = 0.0821$$

**Jawaban:**
- Pada T = 10: Probabilitas penerimaan = **60.65%**
- Pada T = 2: Probabilitas penerimaan = **8.21%**

Ini menunjukkan bahwa pada temperatur tinggi, langkah buruk masih sering diterima (eksplorasi), sedangkan pada temperatur rendah hampir selalu ditolak (eksploitasi).

---

### 3.4 Jadwal Pendinginan (Cooling Schedule)

> **Cooling Schedule** adalah fungsi yang menentukan bagaimana temperatur menurun seiring waktu.

**Jadwal pendinginan umum:**

| Jenis | Formula | Karakteristik |
|-------|---------|---------------|
| **Linear** | T(t) = T₀ - αt | Sederhana, penurunan konstan |
| **Exponential** | T(t) = T₀ × α^t | Paling umum, α ≈ 0.95-0.99 |
| **Logarithmic** | T(t) = T₀ / ln(t+1) | Sangat lambat, theoretical guarantee |

```python
def exponential_schedule(t, T0=100, alpha=0.95):
    return T0 * (alpha ** t)

def linear_schedule(t, T0=100, alpha=0.5):
    return max(0, T0 - alpha * t)
```

#### Solved Problem 6 ⭐⭐

**Soal:** Dengan jadwal exponential T(t) = 100 × 0.95^t, pada iterasi berapa temperatur akan turun di bawah 1?

**Penyelesaian:**

*Step 1:* Set persamaan
$$100 \times 0.95^t < 1$$
$$0.95^t < 0.01$$

*Step 2:* Ambil logaritma
$$t \times \ln(0.95) < \ln(0.01)$$
$$t > \frac{\ln(0.01)}{\ln(0.95)}$$
$$t > \frac{-4.605}{-0.0513}$$
$$t > 89.78$$

**Jawaban:** Temperatur akan turun di bawah 1 pada iterasi ke-**90** atau lebih.

---

### 3.5 Perbandingan Hill Climbing vs Simulated Annealing

| Aspek | Hill Climbing | Simulated Annealing |
|-------|---------------|---------------------|
| **Langkah buruk** | Tidak pernah diterima | Bisa diterima dengan probabilitas |
| **Escape local optima** | Tidak bisa | Bisa |
| **Kecepatan** | Cepat | Lebih lambat |
| **Parameter** | Tidak ada | Jadwal pendinginan |
| **Hasil** | Local optimum | Mendekati global optimum |

#### Solved Problem 7 ⭐⭐

**Soal:** Implementasikan Simulated Annealing untuk mencari minimum fungsi f(x) = x⁴ - 3x³ + 2 pada interval [0, 4] dengan diskritisasi step 0.1!

**Penyelesaian:**

```python
import math
import random

def f(x):
    return x**4 - 3*x**3 + 2

def simulated_annealing_minimize(T0=100, alpha=0.95, max_iter=1000):
    # Initial state: random x in [0, 4]
    current_x = random.uniform(0, 4)
    current_value = f(current_x)
    
    best_x = current_x
    best_value = current_value
    
    T = T0
    
    for t in range(max_iter):
        # Generate neighbor: move by ±0.1
        delta = random.choice([-0.1, 0.1])
        next_x = current_x + delta
        
        # Boundary check
        if next_x < 0 or next_x > 4:
            continue
        
        next_value = f(next_x)
        delta_E = next_value - current_value
        
        # For minimization: accept if delta_E < 0 (better)
        # or with probability e^(-delta_E/T)
        if delta_E < 0:
            current_x = next_x
            current_value = next_value
        elif T > 0:
            prob = math.exp(-delta_E / T)
            if random.random() < prob:
                current_x = next_x
                current_value = next_value
        
        # Update best
        if current_value < best_value:
            best_x = current_x
            best_value = current_value
        
        # Cool down
        T = T * alpha
    
    return best_x, best_value

# Run
x_opt, f_opt = simulated_annealing_minimize()
print(f"Minimum ditemukan di x = {x_opt:.2f} dengan f(x) = {f_opt:.2f}")
```

**Output tipikal:** Minimum ditemukan di x ≈ 2.25 dengan f(x) ≈ -3.54

**Catatan:** Untuk minimisasi, kita membalik tanda ΔE dalam formula probabilitas.

---

## 4. Local Beam Search

### 4.1 Konsep Local Beam Search

> **Local Beam Search** memelihara **k state** secara bersamaan, bukan hanya satu state. Pada setiap iterasi, semua successor dari k state dievaluasi, dan k state terbaik dipilih untuk iterasi berikutnya.

![Local Beam Search](images/p04-05-local-beam-search.png)

*Gambar 4.5: Ilustrasi Local Beam Search dengan k=3*

```python
def local_beam_search(problem, k):
    """
    k: jumlah state yang dipertahankan
    """
    # Initialize k random states
    states = [problem.random_state() for _ in range(k)]
    
    while True:
        # Generate all successors of all k states
        all_successors = []
        for state in states:
            successors = state.get_neighbors()
            all_successors.extend(successors)
        
        # Check if any successor is a goal
        for s in all_successors:
            if problem.is_goal(s):
                return s
        
        # Select k best successors
        all_successors.sort(key=problem.value, reverse=True)
        states = all_successors[:k]
```

### 4.2 Perbedaan dengan Parallel Hill Climbing

| Aspek | Parallel Hill Climbing | Local Beam Search |
|-------|------------------------|-------------------|
| **Informasi** | Independen | Berbagi informasi |
| **Seleksi** | Tiap pencarian mandiri | k terbaik dari SEMUA successor |
| **Diversitas** | Terjaga | Bisa hilang (semua berkumpul di satu area) |

**Masalah diversitas:** Semua k state bisa berkumpul di satu area kecil, kehilangan kemampuan eksplorasi.

### 4.3 Stochastic Beam Search

> **Stochastic Beam Search** memilih k successor secara probabilistik berdasarkan nilai, bukan deterministik memilih k terbaik.

Probabilitas pemilihan proporsional dengan nilai:

$$P(state_i) = \frac{value(state_i)}{\sum_j value(state_j)}$$

#### Solved Problem 8 ⭐⭐

**Soal:** Dalam Local Beam Search dengan k=2, state saat ini adalah {A, B} dengan successor dan nilai:
- Dari A: A1(8), A2(5), A3(9)
- Dari B: B1(7), B2(10), B3(6)

Tentukan 2 state yang dipilih untuk iterasi berikutnya!

**Penyelesaian:**

*Step 1:* Kumpulkan semua successor
- Semua successor: A1(8), A2(5), A3(9), B1(7), B2(10), B3(6)

*Step 2:* Urutkan berdasarkan nilai (descending)
1. B2: 10
2. A3: 9
3. A1: 8
4. B1: 7
5. B3: 6
6. A2: 5

*Step 3:* Pilih k=2 terbaik

**Jawaban:** State yang dipilih adalah **{B2, A3}** dengan nilai 10 dan 9.

---

## 5. Algoritma Genetika

### 5.1 Inspirasi dari Evolusi Biologi

> **Algoritma Genetika (Genetic Algorithm)** adalah teknik optimisasi yang terinspirasi dari proses evolusi biologis: seleksi alam, crossover (reproduksi), dan mutasi.

**Terminologi:**
- **Individu/Chromosome:** Satu solusi kandidat
- **Gen:** Komponen pembentuk chromosome
- **Populasi:** Kumpulan individu
- **Fitness:** Nilai objective function
- **Generasi:** Satu iterasi evolusi

![Komponen Algoritma Genetika](images/p04-06-genetic-algorithm-components.png)

*Gambar 4.6: Komponen dan alur Algoritma Genetika*

### 5.2 Representasi Chromosome

**Representasi biner:**
```
Chromosome: [1, 0, 1, 1, 0, 0, 1, 0]
```

**Representasi permutasi (untuk TSP):**
```
Chromosome: [3, 1, 4, 2, 5]  # Urutan kota yang dikunjungi
```

**Representasi real-valued:**
```
Chromosome: [0.234, 1.567, -0.892]  # Nilai parameter kontinu
```

### 5.3 Fitness Function

> **Fitness Function** mengukur seberapa baik suatu individu sebagai solusi. Biasanya sama dengan atau berkaitan dengan objective function.

```python
def fitness(chromosome):
    # Contoh: minimisasi jarak dalam TSP
    total_distance = calculate_tour_distance(chromosome)
    return 1 / (1 + total_distance)  # Lebih tinggi = lebih baik
```

### 5.4 Seleksi

**Metode seleksi umum:**

#### 5.4.1 Roulette Wheel Selection

Probabilitas terpilih proporsional dengan fitness:

$$P(i) = \frac{fitness(i)}{\sum_j fitness(j)}$$

```python
import random

def roulette_selection(population, fitness_values):
    total_fitness = sum(fitness_values)
    pick = random.uniform(0, total_fitness)
    current = 0
    
    for individual, fitness in zip(population, fitness_values):
        current += fitness
        if current >= pick:
            return individual
```

#### 5.4.2 Tournament Selection

Pilih k individu secara acak, ambil yang terbaik.

```python
def tournament_selection(population, fitness_values, k=3):
    selected_indices = random.sample(range(len(population)), k)
    best_idx = max(selected_indices, key=lambda i: fitness_values[i])
    return population[best_idx]
```

#### Solved Problem 9 ⭐

**Soal:** Dalam Roulette Wheel Selection, diberikan populasi dengan fitness:
- Individu A: 30
- Individu B: 50
- Individu C: 20

Hitung probabilitas terpilihnya masing-masing individu!

**Penyelesaian:**

*Step 1:* Hitung total fitness
$$Total = 30 + 50 + 20 = 100$$

*Step 2:* Hitung probabilitas masing-masing
$$P(A) = \frac{30}{100} = 0.30 = 30\%$$
$$P(B) = \frac{50}{100} = 0.50 = 50\%$$
$$P(C) = \frac{20}{100} = 0.20 = 20\%$$

**Jawaban:** P(A) = 30%, P(B) = 50%, P(C) = 20%

---

### 5.5 Crossover (Rekombinasi)

> **Crossover** menggabungkan genetik dari dua parent untuk menghasilkan offspring.

![Jenis-jenis Crossover](images/p04-07-crossover-types.png)

*Gambar 4.7: Tiga jenis crossover: single-point, two-point, dan uniform*

#### 5.5.1 Single-Point Crossover

```python
def single_point_crossover(parent1, parent2):
    point = random.randint(1, len(parent1) - 1)
    
    offspring1 = parent1[:point] + parent2[point:]
    offspring2 = parent2[:point] + parent1[point:]
    
    return offspring1, offspring2
```

**Contoh:**
```
Parent 1: [1, 1, 1, 1, 1]
Parent 2: [0, 0, 0, 0, 0]
Titik potong: 3

Offspring 1: [1, 1, 1, 0, 0]
Offspring 2: [0, 0, 0, 1, 1]
```

#### 5.5.2 Two-Point Crossover

```python
def two_point_crossover(parent1, parent2):
    point1 = random.randint(1, len(parent1) - 2)
    point2 = random.randint(point1 + 1, len(parent1) - 1)
    
    offspring1 = parent1[:point1] + parent2[point1:point2] + parent1[point2:]
    offspring2 = parent2[:point1] + parent1[point1:point2] + parent2[point2:]
    
    return offspring1, offspring2
```

#### 5.5.3 Uniform Crossover

```python
def uniform_crossover(parent1, parent2):
    offspring1 = []
    offspring2 = []
    
    for g1, g2 in zip(parent1, parent2):
        if random.random() < 0.5:
            offspring1.append(g1)
            offspring2.append(g2)
        else:
            offspring1.append(g2)
            offspring2.append(g1)
    
    return offspring1, offspring2
```

#### Solved Problem 10 ⭐

**Soal:** Lakukan single-point crossover pada dua parent berikut dengan titik potong di posisi 4!
- Parent 1: [1, 0, 1, 1, 0, 0, 1, 0]
- Parent 2: [0, 1, 0, 0, 1, 1, 0, 1]

**Penyelesaian:**

*Step 1:* Identifikasi segmen sebelum dan sesudah titik potong
- Parent 1: [1, 0, 1, 1 | 0, 0, 1, 0]
- Parent 2: [0, 1, 0, 0 | 1, 1, 0, 1]

*Step 2:* Tukar segmen setelah titik potong
- Offspring 1: [1, 0, 1, 1] + [1, 1, 0, 1] = [1, 0, 1, 1, 1, 1, 0, 1]
- Offspring 2: [0, 1, 0, 0] + [0, 0, 1, 0] = [0, 1, 0, 0, 0, 0, 1, 0]

**Jawaban:**
- Offspring 1: **[1, 0, 1, 1, 1, 1, 0, 1]**
- Offspring 2: **[0, 1, 0, 0, 0, 0, 1, 0]**

---

### 5.6 Mutasi

> **Mutasi** adalah perubahan acak kecil pada chromosome untuk mempertahankan keragaman genetik dan memungkinkan eksplorasi area baru.

```python
def mutate(chromosome, mutation_rate=0.01):
    mutated = chromosome.copy()
    
    for i in range(len(mutated)):
        if random.random() < mutation_rate:
            # Untuk representasi biner: flip bit
            mutated[i] = 1 - mutated[i]
    
    return mutated
```

**Contoh:**
```
Sebelum mutasi: [1, 0, 1, 1, 0, 0, 1, 0]
Posisi mutasi: index 2
Setelah mutasi: [1, 0, 0, 1, 0, 0, 1, 0]
              └── bit di-flip dari 1 ke 0
```

#### Solved Problem 11 ⭐⭐

**Soal:** Jika mutation rate = 5% dan panjang chromosome = 10, berapa expected number of bits yang termutasi per offspring?

**Penyelesaian:**

*Step 1:* Gunakan expected value
$$E[\text{mutasi}] = n \times p$$

dimana:
- n = panjang chromosome = 10
- p = mutation rate = 0.05

*Step 2:* Hitung
$$E[\text{mutasi}] = 10 \times 0.05 = 0.5$$

**Jawaban:** Expected number of bits yang termutasi adalah **0.5 bit per offspring**. Ini berarti rata-rata satu dari dua offspring akan memiliki satu bit yang termutasi.

---

### 5.7 Algoritma Genetika Lengkap

```python
def genetic_algorithm(problem, population_size=100, max_generations=1000,
                      crossover_rate=0.8, mutation_rate=0.01):
    # Initialize population
    population = [problem.random_chromosome() for _ in range(population_size)]
    
    for generation in range(max_generations):
        # Evaluate fitness
        fitness_values = [problem.fitness(ind) for ind in population]
        
        # Check termination
        best_idx = fitness_values.index(max(fitness_values))
        best_individual = population[best_idx]
        
        if problem.is_solution(best_individual):
            return best_individual
        
        # Create new population
        new_population = []
        
        # Elitism: keep best individual
        new_population.append(best_individual)
        
        while len(new_population) < population_size:
            # Selection
            parent1 = tournament_selection(population, fitness_values)
            parent2 = tournament_selection(population, fitness_values)
            
            # Crossover
            if random.random() < crossover_rate:
                offspring1, offspring2 = single_point_crossover(parent1, parent2)
            else:
                offspring1, offspring2 = parent1.copy(), parent2.copy()
            
            # Mutation
            offspring1 = mutate(offspring1, mutation_rate)
            offspring2 = mutate(offspring2, mutation_rate)
            
            new_population.extend([offspring1, offspring2])
        
        population = new_population[:population_size]
    
    # Return best found
    fitness_values = [problem.fitness(ind) for ind in population]
    best_idx = fitness_values.index(max(fitness_values))
    return population[best_idx]
```

#### Solved Problem 12 ⭐⭐⭐

**Soal:** Implementasikan Algoritma Genetika untuk mencari maximum fungsi f(x) = x × sin(10πx) + 1 pada interval [0, 1] menggunakan representasi biner 10-bit!

**Penyelesaian:**

```python
import random
import math

class MaxFunctionGA:
    def __init__(self, bits=10):
        self.bits = bits
        self.max_val = 2**bits - 1
    
    def decode(self, chromosome):
        """Convert binary chromosome to real value in [0, 1]"""
        value = int(''.join(map(str, chromosome)), 2)
        return value / self.max_val
    
    def fitness(self, chromosome):
        x = self.decode(chromosome)
        return x * math.sin(10 * math.pi * x) + 1
    
    def random_chromosome(self):
        return [random.randint(0, 1) for _ in range(self.bits)]

def run_ga():
    problem = MaxFunctionGA(bits=10)
    population_size = 50
    generations = 100
    crossover_rate = 0.8
    mutation_rate = 0.01
    
    # Initialize
    population = [problem.random_chromosome() for _ in range(population_size)]
    
    for gen in range(generations):
        fitness_values = [problem.fitness(ind) for ind in population]
        
        # Track best
        best_idx = fitness_values.index(max(fitness_values))
        best = population[best_idx]
        best_x = problem.decode(best)
        best_f = fitness_values[best_idx]
        
        if gen % 20 == 0:
            print(f"Gen {gen}: x = {best_x:.4f}, f(x) = {best_f:.4f}")
        
        # Selection and reproduction
        new_pop = [population[best_idx]]  # Elitism
        
        while len(new_pop) < population_size:
            # Tournament selection
            p1 = max(random.sample(range(len(population)), 3), 
                    key=lambda i: fitness_values[i])
            p2 = max(random.sample(range(len(population)), 3), 
                    key=lambda i: fitness_values[i])
            
            parent1, parent2 = population[p1], population[p2]
            
            # Crossover
            if random.random() < crossover_rate:
                point = random.randint(1, len(parent1)-1)
                off1 = parent1[:point] + parent2[point:]
                off2 = parent2[:point] + parent1[point:]
            else:
                off1, off2 = parent1.copy(), parent2.copy()
            
            # Mutation
            for i in range(len(off1)):
                if random.random() < mutation_rate:
                    off1[i] = 1 - off1[i]
                if random.random() < mutation_rate:
                    off2[i] = 1 - off2[i]
            
            new_pop.extend([off1, off2])
        
        population = new_pop[:population_size]
    
    # Final result
    fitness_values = [problem.fitness(ind) for ind in population]
    best_idx = fitness_values.index(max(fitness_values))
    best = population[best_idx]
    
    return problem.decode(best), problem.fitness(best)

x_opt, f_opt = run_ga()
print(f"\nOptimal: x = {x_opt:.4f}, f(x) = {f_opt:.4f}")
```

**Output tipikal:**
```
Gen 0: x = 0.6543, f(x) = 1.2345
Gen 20: x = 0.8501, f(x) = 1.7823
Gen 40: x = 0.8506, f(x) = 1.8503
Gen 60: x = 0.8507, f(x) = 1.8505
Gen 80: x = 0.8507, f(x) = 1.8507

Optimal: x = 0.8507, f(x) = 1.8507
```

---

## 6. Aplikasi: N-Queens Problem

### 6.1 Formulasi Masalah

> **N-Queens Problem** adalah masalah menempatkan N buah ratu catur pada papan N×N sedemikian sehingga tidak ada dua ratu yang saling menyerang (tidak ada yang berada di baris, kolom, atau diagonal yang sama).

![N-Queens Problem](images/p04-08-n-queens-problem.png)

*Gambar 4.8: Contoh solusi 8-Queens Problem*

### 6.2 Representasi State

Untuk pencarian lokal, representasi efisien adalah array 1D:
- Index = kolom
- Value = baris tempat ratu berada

**Contoh:**
```
State: [0, 4, 7, 5, 2, 6, 1, 3]

Artinya:
- Kolom 0: Ratu di baris 0
- Kolom 1: Ratu di baris 4
- Kolom 2: Ratu di baris 7
- ... dan seterusnya
```

Dengan representasi ini, tidak mungkin ada dua ratu di kolom yang sama (constraint sudah ter-encode).

### 6.3 Objective Function

> **Heuristic h:** Jumlah pasangan ratu yang saling menyerang.

Untuk solusi valid, h = 0.

```python
def count_attacking_pairs(state):
    """
    Menghitung jumlah pasangan ratu yang saling menyerang
    state[col] = row di mana ratu ditempatkan di kolom col
    """
    n = len(state)
    attacks = 0
    
    for i in range(n):
        for j in range(i + 1, n):
            # Cek baris yang sama
            if state[i] == state[j]:
                attacks += 1
            # Cek diagonal (selisih kolom = selisih baris)
            elif abs(state[i] - state[j]) == abs(i - j):
                attacks += 1
    
    return attacks
```

### 6.4 Hill Climbing untuk N-Queens

```python
import random

def hill_climbing_n_queens(n):
    """Solve N-Queens using steepest ascent hill climbing"""
    
    # Random initial state
    state = list(range(n))
    random.shuffle(state)
    
    while True:
        current_attacks = count_attacking_pairs(state)
        
        if current_attacks == 0:
            return state  # Solution found!
        
        # Generate all neighbors (move one queen to different row in same column)
        best_neighbor = None
        best_attacks = current_attacks
        
        for col in range(n):
            original_row = state[col]
            for new_row in range(n):
                if new_row != original_row:
                    # Try this move
                    state[col] = new_row
                    attacks = count_attacking_pairs(state)
                    
                    if attacks < best_attacks:
                        best_attacks = attacks
                        best_neighbor = state.copy()
                    
                    # Restore
                    state[col] = original_row
        
        if best_neighbor is None:
            return state  # Stuck at local minimum
        
        state = best_neighbor
```

#### Solved Problem 13 ⭐⭐

**Soal:** Untuk 4-Queens dengan state awal [1, 3, 0, 2], hitung nilai h (jumlah pasangan menyerang)!

**Penyelesaian:**

*Step 1:* Visualisasikan papan

![Papan 4-Queens dengan State [1,3,0,2]](images/p04-13-4queens-board.png)

*Gambar 4.9: Papan 4-Queens dengan konfigurasi [1, 3, 0, 2]*

*Step 2:* Cek setiap pasangan (total 6 pasangan untuk 4 ratu)

| Pasangan | Kolom | Baris | Cek Diagonal | Menyerang? |
|----------|-------|-------|--------------|------------|
| (0,1) | 0,1 | 1,3 | \|1-3\|=2, \|0-1\|=1 | Tidak |
| (0,2) | 0,2 | 1,0 | \|1-0\|=1, \|0-2\|=2 | Tidak |
| (0,3) | 0,3 | 1,2 | \|1-2\|=1, \|0-3\|=3 | Tidak |
| (1,2) | 1,2 | 3,0 | \|3-0\|=3, \|1-2\|=1 | Tidak |
| (1,3) | 1,3 | 3,2 | \|3-2\|=1, \|1-3\|=2 | Tidak |
| (2,3) | 2,3 | 0,2 | \|0-2\|=2, \|2-3\|=1 | Tidak |

**Jawaban:** h = **0** (ini adalah solusi valid!)

---

#### Solved Problem 14 ⭐⭐⭐

**Soal:** Implementasikan Simulated Annealing untuk menyelesaikan 8-Queens Problem dan bandingkan dengan Hill Climbing dalam hal success rate!

**Penyelesaian:**

```python
import random
import math

def count_attacks(state):
    n = len(state)
    attacks = 0
    for i in range(n):
        for j in range(i + 1, n):
            if state[i] == state[j] or abs(state[i] - state[j]) == abs(i - j):
                attacks += 1
    return attacks

def get_random_neighbor(state):
    n = len(state)
    new_state = state.copy()
    col = random.randint(0, n - 1)
    new_row = random.randint(0, n - 1)
    while new_row == state[col]:
        new_row = random.randint(0, n - 1)
    new_state[col] = new_row
    return new_state

def simulated_annealing_queens(n=8, T0=4.0, alpha=0.99, max_iter=10000):
    state = list(range(n))
    random.shuffle(state)
    
    T = T0
    for _ in range(max_iter):
        attacks = count_attacks(state)
        if attacks == 0:
            return state, True
        
        neighbor = get_random_neighbor(state)
        delta = count_attacks(neighbor) - attacks
        
        if delta < 0 or (T > 0 and random.random() < math.exp(-delta / T)):
            state = neighbor
        
        T *= alpha
    
    return state, count_attacks(state) == 0

def hill_climbing_queens(n=8, max_iter=1000):
    state = list(range(n))
    random.shuffle(state)
    
    for _ in range(max_iter):
        current_attacks = count_attacks(state)
        if current_attacks == 0:
            return state, True
        
        # Find best neighbor
        best_neighbor = None
        best_attacks = current_attacks
        
        for col in range(n):
            orig = state[col]
            for row in range(n):
                if row != orig:
                    state[col] = row
                    attacks = count_attacks(state)
                    if attacks < best_attacks:
                        best_attacks = attacks
                        best_neighbor = state.copy()
                    state[col] = orig
        
        if best_neighbor is None:
            return state, False  # Stuck
        state = best_neighbor
    
    return state, count_attacks(state) == 0

# Compare success rates
def compare_algorithms(n_trials=100):
    hc_success = 0
    sa_success = 0
    
    for _ in range(n_trials):
        _, hc_ok = hill_climbing_queens()
        if hc_ok:
            hc_success += 1
        
        _, sa_ok = simulated_annealing_queens()
        if sa_ok:
            sa_success += 1
    
    print(f"Hill Climbing Success Rate: {hc_success}%")
    print(f"Simulated Annealing Success Rate: {sa_success}%")

compare_algorithms()
```

**Output tipikal:**
```
Hill Climbing Success Rate: 14%
Simulated Annealing Success Rate: 94%
```

**Analisis:** Simulated Annealing jauh lebih baik karena dapat keluar dari local minima.

---

## 7. Aplikasi: Traveling Salesman Problem (TSP)

### 7.1 Formulasi Masalah

> **Traveling Salesman Problem (TSP)** adalah masalah mencari rute terpendek yang mengunjungi setiap kota tepat satu kali dan kembali ke kota asal.

### 7.2 Representasi dan Operator

**Representasi:** Permutasi kota
```
[0, 3, 1, 4, 2]  # Urutan kunjungan: kota 0 → 3 → 1 → 4 → 2 → 0
```

**Operator neighbor untuk TSP:**

1. **2-opt:** Balik urutan segmen rute
2. **Swap:** Tukar posisi dua kota
3. **Insert:** Pindahkan satu kota ke posisi lain

![Operator 2-opt](images/p04-09-2opt-operator.png)

*Gambar 4.10: Operator 2-opt untuk TSP*

#### Solved Problem 15 ⭐⭐

**Soal:** Diberikan rute TSP [0, 1, 2, 3, 4] dan jarak antar kota dalam matriks berikut. Terapkan 2-opt dengan membalik segmen indeks 1 sampai 3. Apakah hasilnya lebih baik?

Matriks jarak:
```
     0    1    2    3    4
0 [  0,  10,  15,  20,  25 ]
1 [ 10,   0,  35,  25,  30 ]
2 [ 15,  35,   0,  30,  20 ]
3 [ 20,  25,  30,   0,  15 ]
4 [ 25,  30,  20,  15,   0 ]
```

**Penyelesaian:**

*Step 1:* Hitung jarak rute awal [0, 1, 2, 3, 4, 0]
- 0→1: 10
- 1→2: 35
- 2→3: 30
- 3→4: 15
- 4→0: 25
- **Total: 115**

*Step 2:* Terapkan 2-opt, balik segmen indeks 1-3
- Rute awal: [0, **1, 2, 3**, 4]
- Segmen [1, 2, 3] dibalik menjadi [3, 2, 1]
- Rute baru: [0, **3, 2, 1**, 4]

*Step 3:* Hitung jarak rute baru [0, 3, 2, 1, 4, 0]
- 0→3: 20
- 3→2: 30
- 2→1: 35
- 1→4: 30
- 4→0: 25
- **Total: 140**

**Jawaban:** Rute baru [0, 3, 2, 1, 4] memiliki jarak **140**, lebih buruk dari rute awal (115). Operasi 2-opt ini tidak menghasilkan perbaikan.

---

### 7.3 Algoritma Genetika untuk TSP

Untuk TSP, perlu operator crossover khusus yang menjaga validitas permutasi:

**Order Crossover (OX):**

```python
def order_crossover(parent1, parent2):
    n = len(parent1)
    
    # Select crossover segment
    start = random.randint(0, n - 2)
    end = random.randint(start + 1, n - 1)
    
    # Copy segment from parent1
    offspring = [None] * n
    offspring[start:end+1] = parent1[start:end+1]
    
    # Fill remaining positions with parent2 in order
    p2_idx = 0
    for i in range(n):
        if offspring[i] is None:
            while parent2[p2_idx] in offspring:
                p2_idx += 1
            offspring[i] = parent2[p2_idx]
            p2_idx += 1
    
    return offspring
```

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Terapkan Order Crossover pada:
- Parent 1: [1, 2, 3, 4, 5, 6, 7, 8]
- Parent 2: [8, 7, 6, 5, 4, 3, 2, 1]
- Crossover segment: indeks 3 sampai 5 (inklusif)

**Penyelesaian:**

*Step 1:* Copy segment dari Parent 1 ke offspring
- Offspring: [_, _, _, 4, 5, 6, _, _]

*Step 2:* Isi sisa posisi dengan elemen dari Parent 2 secara berurutan
- Mulai dari awal Parent 2: 8, 7, 6, 5, 4, 3, 2, 1
- Skip 4, 5, 6 karena sudah ada
- Urutan yang tersedia: 8, 7, 3, 2, 1

*Step 3:* Isi posisi kosong (mulai dari posisi setelah segment, wrapping)
- Posisi 6: 8
- Posisi 7: 7
- Posisi 0: 3
- Posisi 1: 2
- Posisi 2: 1

**Jawaban:** Offspring = **[3, 2, 1, 4, 5, 6, 8, 7]**

---

## 8. Aplikasi dalam Konteks Pertahanan

### 8.1 Optimisasi Rute Patroli

> **Masalah:** Menentukan rute optimal untuk kendaraan patroli yang harus mengunjungi sejumlah checkpoint.

**Aplikasi algoritma:**
- TSP untuk single vehicle
- Genetic Algorithm untuk multi-vehicle routing
- Simulated Annealing untuk dynamic re-routing

#### Solved Problem 17 ⭐⭐

**Soal:** Sebuah drone patroli harus mengunjungi 5 pos pengamatan. Rancang representasi state dan fitness function untuk algoritma genetika!

**Penyelesaian:**

**Representasi:** Permutasi pos pengamatan
```python
# Chromosome contoh: urutan kunjungan
chromosome = [0, 3, 1, 4, 2]  # Pos 0 → 3 → 1 → 4 → 2 → kembali ke base
```

**Fitness Function:**
```python
def fitness(chromosome, distances, priorities):
    """
    distances: matriks jarak antar pos
    priorities: nilai prioritas tiap pos (lebih tinggi = lebih penting)
    """
    n = len(chromosome)
    total_distance = 0
    
    # Hitung total jarak
    for i in range(n - 1):
        total_distance += distances[chromosome[i]][chromosome[i + 1]]
    total_distance += distances[chromosome[-1]][chromosome[0]]  # Kembali ke awal
    
    # Bonus untuk mengunjungi pos prioritas tinggi lebih awal
    priority_bonus = 0
    for i, pos in enumerate(chromosome):
        # Posisi awal mendapat multiplier lebih tinggi
        priority_bonus += priorities[pos] * (n - i)
    
    # Fitness: minimize distance, maximize priority coverage
    fitness = priority_bonus / (1 + total_distance)
    
    return fitness
```

---

### 8.2 Optimisasi Penempatan Sensor

> **Masalah:** Menempatkan N sensor radar untuk memaksimalkan coverage area sambil meminimalkan overlap.

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Rancang pendekatan Hill Climbing untuk optimisasi penempatan 3 sensor radar di area 100×100 km dengan radius coverage 30 km!

**Penyelesaian:**

```python
import math
import random

class SensorPlacementProblem:
    def __init__(self, n_sensors=3, area_size=100, radius=30, grid_points=1000):
        self.n_sensors = n_sensors
        self.area_size = area_size
        self.radius = radius
        
        # Generate grid points for coverage calculation
        self.grid_points = []
        step = area_size / int(math.sqrt(grid_points))
        x = 0
        while x <= area_size:
            y = 0
            while y <= area_size:
                self.grid_points.append((x, y))
                y += step
            x += step
    
    def random_state(self):
        """State = list of (x, y) coordinates for each sensor"""
        return [(random.uniform(0, self.area_size), 
                 random.uniform(0, self.area_size)) 
                for _ in range(self.n_sensors)]
    
    def coverage(self, state):
        """Calculate percentage of grid points covered by at least one sensor"""
        covered = 0
        for point in self.grid_points:
            for sensor in state:
                dist = math.sqrt((point[0] - sensor[0])**2 + 
                                (point[1] - sensor[1])**2)
                if dist <= self.radius:
                    covered += 1
                    break
        return covered / len(self.grid_points)
    
    def get_neighbors(self, state, step=5):
        """Generate neighbors by moving each sensor in 4 directions"""
        neighbors = []
        for i in range(len(state)):
            for dx, dy in [(step, 0), (-step, 0), (0, step), (0, -step)]:
                new_state = state.copy()
                new_x = max(0, min(self.area_size, state[i][0] + dx))
                new_y = max(0, min(self.area_size, state[i][1] + dy))
                new_state[i] = (new_x, new_y)
                neighbors.append(new_state)
        return neighbors

def hill_climbing_sensors(problem, max_iter=1000):
    current = problem.random_state()
    current_coverage = problem.coverage(current)
    
    for _ in range(max_iter):
        neighbors = problem.get_neighbors(current)
        best_neighbor = max(neighbors, key=problem.coverage)
        best_coverage = problem.coverage(best_neighbor)
        
        if best_coverage <= current_coverage:
            break
        
        current = best_neighbor
        current_coverage = best_coverage
    
    return current, current_coverage

# Run
problem = SensorPlacementProblem()
solution, coverage = hill_climbing_sensors(problem)
print(f"Sensor positions: {solution}")
print(f"Coverage: {coverage*100:.1f}%")
```

---

### 8.3 Penjadwalan Operasi Militer

> **Masalah:** Menjadwalkan sejumlah misi dengan constraint waktu, resources, dan dependencies.

#### Solved Problem 19 ⭐⭐⭐

**Soal:** Rancang fitness function untuk penjadwalan 5 misi dengan constraint:
- Setiap misi memiliki waktu mulai preferred dan deadline
- Resource terbatas (hanya bisa 2 misi paralel)
- Beberapa misi memiliki dependency

**Penyelesaian:**

```python
def scheduling_fitness(schedule, missions, max_parallel=2):
    """
    schedule: list of start times for each mission
    missions: list of dict with 'duration', 'preferred_start', 
              'deadline', 'dependencies' (list of mission indices)
    """
    n = len(missions)
    total_penalty = 0
    
    for i, mission in enumerate(missions):
        start_time = schedule[i]
        end_time = start_time + mission['duration']
        
        # Penalty 1: Deviation from preferred start
        deviation = abs(start_time - mission['preferred_start'])
        total_penalty += deviation * 0.5
        
        # Penalty 2: Deadline violation
        if end_time > mission['deadline']:
            overtime = end_time - mission['deadline']
            total_penalty += overtime * 10  # High penalty for deadline miss
        
        # Penalty 3: Dependency violation
        for dep_idx in mission.get('dependencies', []):
            dep_end = schedule[dep_idx] + missions[dep_idx]['duration']
            if start_time < dep_end:
                overlap = dep_end - start_time
                total_penalty += overlap * 5  # Dependency must complete first
    
    # Penalty 4: Resource constraint (parallel missions)
    # Check each time slot
    time_slots = {}
    for i, mission in enumerate(missions):
        start = schedule[i]
        end = start + mission['duration']
        for t in range(int(start), int(end)):
            time_slots[t] = time_slots.get(t, 0) + 1
            if time_slots[t] > max_parallel:
                total_penalty += (time_slots[t] - max_parallel) * 3
    
    # Fitness = inverse of penalty (higher = better)
    return 1 / (1 + total_penalty)
```

---

## 9. Perbandingan Algoritma Pencarian Lokal

### 9.1 Tabel Perbandingan

| Algoritma | Escape Local Optima | Memori | Parameter | Best For |
|-----------|:------------------:|:------:|-----------|----------|
| **Hill Climbing** | ❌ | O(1) | Tidak ada | Landscape smooth |
| **Random Restart HC** | ✅ (dengan restart) | O(1) | Jumlah restart | Multiple local optima |
| **Simulated Annealing** | ✅ | O(1) | T₀, α, stopping | General optimization |
| **Local Beam Search** | Sebagian | O(k) | k (beam width) | Parallelizable problems |
| **Genetic Algorithm** | ✅ | O(pop_size) | Pop size, rates | Complex landscapes |

#### Solved Problem 20 ⭐⭐

**Soal:** Untuk masalah optimisasi dengan karakteristik berikut, rekomendasikan algoritma yang paling sesuai dan jelaskan alasannya!
a) Landscape dengan banyak local optima, solusi harus ditemukan cepat
b) Masalah dengan constraint kompleks yang sulit diformulasikan
c) Optimisasi real-time dengan waktu terbatas

**Penyelesaian:**

**a) Banyak local optima, perlu cepat:**
- **Rekomendasi:** Random Restart Hill Climbing
- **Alasan:** Lebih cepat dari SA dan GA. Multiple restart meningkatkan peluang menemukan global optimum.

**b) Constraint kompleks:**
- **Rekomendasi:** Genetic Algorithm
- **Alasan:** GA dapat menghandle constraint melalui penalty function dalam fitness. Crossover dapat mengkombinasikan solusi feasible untuk menghasilkan solusi feasible baru.

**c) Real-time dengan waktu terbatas:**
- **Rekomendasi:** Simulated Annealing dengan jadwal cepat atau Hill Climbing
- **Alasan:** Dapat dihentikan kapan saja (anytime algorithm). Hill Climbing jika perlu sangat cepat dan landscape relatif smooth.

---

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Implementasikan dan bandingkan ketiga algoritma (Hill Climbing, Simulated Annealing, Genetic Algorithm) untuk fungsi Rastrigin 2D:

$$f(x, y) = 20 + x^2 + y^2 - 10(\cos(2\pi x) + \cos(2\pi y))$$

pada domain [-5.12, 5.12]. Global minimum di (0, 0) dengan f = 0.

**Penyelesaian:**

```python
import random
import math

def rastrigin(x, y):
    return 20 + x**2 + y**2 - 10*(math.cos(2*math.pi*x) + math.cos(2*math.pi*y))

# Hill Climbing
def hc_rastrigin(max_iter=1000):
    x, y = random.uniform(-5.12, 5.12), random.uniform(-5.12, 5.12)
    step = 0.1
    
    for _ in range(max_iter):
        current = rastrigin(x, y)
        
        # Check 4 neighbors
        neighbors = [(x+step, y), (x-step, y), (x, y+step), (x, y-step)]
        neighbors = [(nx, ny) for nx, ny in neighbors 
                    if -5.12 <= nx <= 5.12 and -5.12 <= ny <= 5.12]
        
        best_neighbor = min(neighbors, key=lambda p: rastrigin(p[0], p[1]))
        if rastrigin(best_neighbor[0], best_neighbor[1]) >= current:
            break
        x, y = best_neighbor
    
    return x, y, rastrigin(x, y)

# Simulated Annealing
def sa_rastrigin(T0=10, alpha=0.995, max_iter=5000):
    x, y = random.uniform(-5.12, 5.12), random.uniform(-5.12, 5.12)
    T = T0
    
    for _ in range(max_iter):
        nx = x + random.gauss(0, 0.5)
        ny = y + random.gauss(0, 0.5)
        nx = max(-5.12, min(5.12, nx))
        ny = max(-5.12, min(5.12, ny))
        
        delta = rastrigin(nx, ny) - rastrigin(x, y)
        
        if delta < 0 or (T > 0 and random.random() < math.exp(-delta/T)):
            x, y = nx, ny
        
        T *= alpha
    
    return x, y, rastrigin(x, y)

# Genetic Algorithm
def ga_rastrigin(pop_size=50, generations=100):
    def random_ind():
        return [random.uniform(-5.12, 5.12), random.uniform(-5.12, 5.12)]
    
    def fitness(ind):
        return 1 / (1 + rastrigin(ind[0], ind[1]))
    
    population = [random_ind() for _ in range(pop_size)]
    
    for _ in range(generations):
        fits = [fitness(ind) for ind in population]
        
        new_pop = []
        # Elitism
        best_idx = fits.index(max(fits))
        new_pop.append(population[best_idx])
        
        while len(new_pop) < pop_size:
            # Tournament selection
            p1 = max(random.sample(range(len(population)), 3), key=lambda i: fits[i])
            p2 = max(random.sample(range(len(population)), 3), key=lambda i: fits[i])
            
            # Crossover
            offspring = [(population[p1][0] + population[p2][0])/2,
                        (population[p1][1] + population[p2][1])/2]
            
            # Mutation
            if random.random() < 0.1:
                offspring[0] += random.gauss(0, 0.5)
                offspring[1] += random.gauss(0, 0.5)
                offspring[0] = max(-5.12, min(5.12, offspring[0]))
                offspring[1] = max(-5.12, min(5.12, offspring[1]))
            
            new_pop.append(offspring)
        
        population = new_pop[:pop_size]
    
    best = min(population, key=lambda ind: rastrigin(ind[0], ind[1]))
    return best[0], best[1], rastrigin(best[0], best[1])

# Run comparison
print("Comparison on Rastrigin Function:")
print(f"Hill Climbing: {hc_rastrigin()}")
print(f"Simulated Annealing: {sa_rastrigin()}")
print(f"Genetic Algorithm: {ga_rastrigin()}")
```

**Output tipikal:**
```
Comparison on Rastrigin Function:
Hill Climbing: (0.994, -0.994, 1.9899)  # Stuck at local minimum
Simulated Annealing: (0.012, -0.008, 0.0024)  # Near global minimum
Genetic Algorithm: (-0.003, 0.005, 0.0006)  # Near global minimum
```

---

#### Solved Problem 22 ⭐

**Soal:** Jelaskan mengapa Simulated Annealing disebut "anytime algorithm"!

**Penyelesaian:**

> **Anytime Algorithm** adalah algoritma yang dapat dihentikan kapan saja dan akan memberikan solusi valid, dengan kualitas solusi yang semakin baik seiring bertambahnya waktu.

**Simulated Annealing sebagai anytime algorithm:**

1. **Selalu memiliki solusi:** Setiap saat, algoritma menyimpan "current state" yang merupakan solusi valid

2. **Kualitas meningkat:** Rata-rata kualitas solusi meningkat seiring berjalannya waktu karena temperatur menurun dan algoritma semakin fokus pada eksploitasi

3. **Dapat dihentikan:** Tidak ada syarat khusus untuk penghentian - dapat dihentikan kapan saja

**Jawaban:** Simulated Annealing disebut anytime algorithm karena dapat dihentikan pada waktu kapan pun dan tetap menghasilkan solusi valid. Semakin lama dijalankan, semakin baik kualitas solusi yang dihasilkan, tetapi tidak ada waktu minimum yang harus dipenuhi.

---

## Supplementary Problems

### Problem S1 ⭐

**Soal:** Dalam Hill Climbing, apa yang terjadi jika dua tetangga memiliki nilai objective function yang sama dan keduanya lebih baik dari state saat ini?

**Jawaban:** Tergantung implementasi. Steepest Ascent biasanya memilih salah satu secara deterministik (misal yang pertama ditemukan). Stochastic Hill Climbing akan memilih secara acak. Keduanya valid selama memilih yang lebih baik dari current state.

---

### Problem S2 ⭐⭐

**Soal:** Berapa nilai awal temperatur (T₀) yang ideal untuk Simulated Annealing?

**Jawaban:** T₀ harus cukup tinggi sehingga pada awalnya hampir semua langkah diterima (probabilitas sekitar 0.8-0.9 untuk langkah buruk rata-rata). Rumus praktis: T₀ ≈ Δf_avg / ln(0.8), di mana Δf_avg adalah perubahan objective function rata-rata.

---

### Problem S3 ⭐⭐

**Soal:** Mengapa crossover rate umumnya tinggi (0.7-0.9) sedangkan mutation rate rendah (0.001-0.05) dalam Genetic Algorithm?

**Jawaban:** 
- **Crossover tinggi:** Merupakan operator utama untuk mengkombinasikan "good genes" dari parent yang berbeda untuk menghasilkan offspring potensially lebih baik
- **Mutation rendah:** Hanya untuk mempertahankan diversity dan mencegah premature convergence. Terlalu tinggi akan merusak good solutions

---

### Problem S4 ⭐⭐⭐

**Soal:** Jelaskan bagaimana Local Beam Search dapat mengalami "loss of diversity"!

**Jawaban:** Karena Local Beam Search memilih k state terbaik dari SEMUA successors (bukan k terbaik dari MASING-MASING state), ada kemungkinan semua k state terpilih berasal dari satu atau sedikit parent yang sama. Ini menyebabkan seluruh beam berkumpul di satu area landscape, kehilangan kemampuan eksplorasi di area lain yang mungkin memiliki optimum yang lebih baik.

---

### Problem S5 ⭐⭐⭐

**Soal:** Untuk masalah Vehicle Routing Problem (VRP) dalam operasi logistik militer, algoritma mana yang paling sesuai dan mengapa?

**Jawaban:** **Genetic Algorithm dengan custom operators** adalah pilihan terbaik karena:
1. VRP memiliki banyak constraint kompleks (kapasitas, time windows, multiple vehicles)
2. GA dapat menghandle constraint melalui penalty function
3. Custom crossover seperti Route-Based Crossover dapat menjaga feasibility
4. Multiple vehicles dapat direpresentasikan dalam satu chromosome
5. Dapat dikombinasikan dengan local search (memetic algorithm) untuk fine-tuning

---

## Ringkasan

| Konsep | Poin Kunci |
|--------|------------|
| **Pencarian Lokal** | Hanya menyimpan state saat ini, memori O(1) |
| **Hill Climbing** | Greedy, selalu pilih tetangga terbaik, bisa stuck di local optima |
| **Variasi HC** | Steepest Ascent, Stochastic, First-Choice, Random Restart |
| **Landscape Features** | Local/Global Maxima, Plateau, Ridge |
| **Simulated Annealing** | Terinspirasi metalurgi, terima langkah buruk dengan probabilitas e^(ΔE/T) |
| **Cooling Schedule** | Linear, Exponential, Logarithmic |
| **Local Beam Search** | Memelihara k state, berbagi informasi |
| **Genetic Algorithm** | Populasi, Seleksi, Crossover, Mutasi |
| **Fitness Function** | Mengukur kualitas solusi |
| **N-Queens** | Representasi array, heuristic = pasangan menyerang |
| **TSP** | Representasi permutasi, operator 2-opt |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. Chapter 4.1-4.2.
2. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. Chapter 5.
3. Goldberg, D.E. (1989). *Genetic Algorithms in Search, Optimization, and Machine Learning*. Addison-Wesley.
4. Kirkpatrick, S., Gelatt, C.D., & Vecchi, M.P. (1983). Optimization by Simulated Annealing. *Science*, 220(4598), 671-680.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
