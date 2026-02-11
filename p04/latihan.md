# Latihan Pertemuan 04: Pencarian Lokal dan Optimisasi

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 04  
**Topik:** Pencarian Lokal dan Optimisasi  
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
Perbedaan utama antara pencarian sistematis (seperti A*) dan pencarian lokal adalah:

A. Pencarian sistematis lebih cepat  
B. Pencarian lokal menyimpan seluruh jalur ke solusi  
C. Pencarian lokal hanya menyimpan state saat ini  
D. Pencarian sistematis tidak memerlukan heuristik  
E. Pencarian lokal selalu menemukan solusi optimal

---

### Soal 2
Dalam landscape pencarian, "plateau" adalah:

A. Titik tertinggi di seluruh landscape  
B. Titik terendah di area lokal  
C. Area datar di mana semua tetangga memiliki nilai sama  
D. Puncak sempit yang memanjang  
E. Titik di mana algoritma selalu berhenti

---

### Soal 3
Algoritma Hill Climbing disebut juga:

A. Breadth-First Search  
B. Greedy Local Search  
C. Optimal Search  
D. Complete Search  
E. Exhaustive Search

---

### Soal 4
Dalam Steepest Ascent Hill Climbing, langkah yang dipilih adalah:

A. Tetangga pertama yang lebih baik  
B. Tetangga acak yang lebih baik  
C. Tetangga dengan nilai tertinggi di antara semua tetangga  
D. Tetangga dengan nilai terendah  
E. Semua tetangga yang lebih baik

---

### Soal 5
Variasi Hill Climbing yang paling efisien ketika jumlah tetangga sangat banyak adalah:

A. Steepest Ascent  
B. Stochastic Hill Climbing  
C. First-Choice Hill Climbing  
D. Random Restart Hill Climbing  
E. Iterative Deepening Hill Climbing

---

### Soal 6
Jika probabilitas Hill Climbing menemukan global optimum adalah 20%, berapa probabilitas sukses setelah 5 restart?

A. 100%  
B. 67.2%  
C. 32.8%  
D. 80%  
E. 20%

---

### Soal 7
Simulated Annealing terinspirasi dari proses:

A. Evolusi biologis  
B. Annealing dalam metalurgi  
C. Konduktivitas listrik  
D. Fotosintesis  
E. Fermentasi

---

### Soal 8
Dalam Simulated Annealing, probabilitas menerima langkah yang lebih buruk adalah:

A. Selalu 0  
B. Selalu 1  
C. e^(ΔE/T)  
D. e^(-ΔE/T)  
E. T/ΔE

---

### Soal 9
Pada Simulated Annealing, ketika temperatur T sangat tinggi:

A. Algoritma berhenti  
B. Hanya langkah yang lebih baik diterima  
C. Hampir semua langkah diterima  
D. Algoritma menjadi deterministik  
E. Probabilitas penerimaan mendekati 0

---

### Soal 10
Jadwal pendinginan exponential memiliki formula:

A. T(t) = T₀ - αt  
B. T(t) = T₀ × α^t  
C. T(t) = T₀ / ln(t+1)  
D. T(t) = T₀ + αt  
E. T(t) = T₀ / t

---

### Soal 11
Dalam Local Beam Search dengan k=4, jika setiap state memiliki 3 successor, berapa total successor yang dievaluasi per iterasi?

A. 3  
B. 4  
C. 7  
D. 12  
E. 16

---

### Soal 12
Masalah utama Local Beam Search dibandingkan dengan parallel independent search adalah:

A. Membutuhkan lebih banyak memori  
B. Lebih lambat  
C. Bisa kehilangan diversitas (semua state berkumpul di satu area)  
D. Tidak dapat menemukan solusi  
E. Memerlukan lebih banyak parameter

---

### Soal 13
Dalam Algoritma Genetika, "chromosome" merepresentasikan:

A. DNA manusia  
B. Satu solusi kandidat  
C. Fitness function  
D. Operator crossover  
E. Populasi

---

### Soal 14
Metode seleksi di mana probabilitas terpilih proporsional dengan fitness disebut:

A. Tournament Selection  
B. Random Selection  
C. Roulette Wheel Selection  
D. Elitism Selection  
E. Truncation Selection

---

### Soal 15
Dalam single-point crossover, jika titik potong di posisi 4 pada chromosome 8-bit:

A. 4 bit pertama dipertukarkan  
B. 4 bit terakhir dipertukarkan  
C. Semua bit dipertukarkan  
D. Tidak ada pertukaran  
E. Hanya bit ke-4 yang dipertukarkan

---

### Soal 16
Mutation rate dalam Algoritma Genetika biasanya:

A. Sangat tinggi (>50%)  
B. Sedang (20-40%)  
C. Rendah (1-5%)  
D. Nol (tidak ada mutasi)  
E. 100%

---

### Soal 17
Dalam representasi N-Queens menggunakan array 1D, state [2, 0, 3, 1] untuk 4-Queens berarti:

A. Ratu di kolom 2, 0, 3, 1  
B. Ratu di baris 2, 0, 3, 1 untuk kolom 0, 1, 2, 3  
C. 4 ratu di posisi yang sama  
D. Tidak ada ratu di papan  
E. Hanya 2 ratu yang ditempatkan

---

### Soal 18
Untuk TSP dengan 5 kota, representasi [0, 2, 4, 1, 3] menunjukkan:

A. Jarak antar kota  
B. Urutan kunjungan: kota 0 → 2 → 4 → 1 → 3 → 0  
C. Koordinat kota  
D. Biaya perjalanan  
E. Jumlah kota yang dikunjungi

---

### Soal 19
Operator 2-opt dalam TSP berfungsi untuk:

A. Menambah kota baru  
B. Menghapus kota dari rute  
C. Membalik urutan segmen rute  
D. Mengacak seluruh rute  
E. Menggandakan rute

---

### Soal 20
Algoritma yang disebut "anytime algorithm" adalah:

A. Hill Climbing  
B. Simulated Annealing  
C. Breadth-First Search  
D. Depth-First Search  
E. A* Search

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan mengapa pencarian lokal cocok untuk masalah optimisasi tetapi tidak cocok untuk masalah path-finding!

---

### Soal 2 ⭐
Sebutkan dan jelaskan empat fitur landscape yang dapat mempengaruhi kinerja algoritma pencarian lokal!

---

### Soal 3 ⭐
Jelaskan perbedaan antara Steepest Ascent, Stochastic, dan First-Choice Hill Climbing!

---

### Soal 4 ⭐
Diberikan landscape dengan nilai berikut (posisi dan nilai objective function):

| Posisi | A | B | C | D | E | F | G |
|--------|---|---|---|---|---|---|---|
| Nilai  | 5 | 8 | 6 | 9 | 7 | 9 | 4 |

Jika Hill Climbing dimulai dari posisi C, di mana algoritma akan berhenti? (Tetangga: kiri dan kanan)

---

### Soal 5 ⭐⭐
Jika satu kali Hill Climbing memiliki probabilitas 15% untuk menemukan global optimum, berapa kali restart diperlukan agar probabilitas sukses mencapai 95%?

---

### Soal 6 ⭐⭐
Dalam Simulated Annealing dengan current value = 80 dan neighbor value = 75:
a) Hitung probabilitas penerimaan pada T = 10
b) Hitung probabilitas penerimaan pada T = 1
c) Jelaskan interpretasinya!

---

### Soal 7 ⭐⭐
Dengan jadwal pendinginan exponential T(t) = 50 × 0.9^t, hitung:
a) Temperatur pada iterasi ke-5
b) Iterasi berapa temperatur turun di bawah 5

---

### Soal 8 ⭐⭐
Jelaskan mengapa Simulated Annealing dapat keluar dari local optima sedangkan Hill Climbing tidak bisa!

---

### Soal 9 ⭐⭐
Dalam Local Beam Search dengan k=3, state saat ini adalah {X, Y, Z} dengan successor:
- Dari X: X1(12), X2(8), X3(15)
- Dari Y: Y1(10), Y2(14), Y3(9)
- Dari Z: Z1(11), Z2(7), Z3(13)

Tentukan 3 state yang dipilih untuk iterasi berikutnya!

---

### Soal 10 ⭐⭐
Dalam Roulette Wheel Selection dengan populasi:
- Individu P: fitness = 40
- Individu Q: fitness = 25
- Individu R: fitness = 35

Hitung probabilitas terpilihnya masing-masing individu!

---

### Soal 11 ⭐⭐
Lakukan single-point crossover pada:
- Parent 1: [1, 0, 0, 1, 1, 0]
- Parent 2: [0, 1, 1, 0, 0, 1]
- Titik potong: setelah posisi 3

---

### Soal 12 ⭐⭐⭐
Untuk 4-Queens dengan state [1, 3, 0, 2]:
a) Gambarkan posisi ratu di papan 4×4
b) Hitung jumlah pasangan ratu yang saling menyerang (h)
c) Apakah ini solusi valid?

---

### Soal 13 ⭐⭐⭐
Diberikan TSP dengan 4 kota dan matriks jarak:

|   | A | B | C | D |
|---|---|---|---|---|
| A | 0 | 10| 15| 20|
| B | 10| 0 | 25| 30|
| C | 15| 25| 0 | 35|
| D | 20| 30| 35| 0 |

Untuk rute [A, B, C, D]:
a) Hitung total jarak
b) Terapkan 2-opt dengan membalik segmen B-C
c) Hitung jarak rute baru dan tentukan apakah lebih baik!

---

### Soal 14 ⭐⭐⭐
Rancang fitness function untuk Algoritma Genetika yang menyelesaikan masalah penjadwalan shift jaga dengan kriteria:
- Minimalisasi jumlah shift kosong
- Setiap personel maksimal 2 shift per hari
- Distribusi beban kerja merata

---

### Soal 15 ⭐⭐⭐
Bandingkan kelebihan dan kekurangan Hill Climbing, Simulated Annealing, dan Genetic Algorithm untuk masalah optimisasi dengan karakteristik:
- Ruang pencarian sangat besar
- Banyak local optima
- Evaluasi fitness mahal (computationally expensive)

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Optimisasi Rute Patroli Drone

**Latar Belakang:**

Komando Pertahanan Udara Nasional (Kohanudnas) mengoperasikan 3 drone pengintai untuk patroli wilayah perbatasan. Setiap drone harus mengunjungi sejumlah checkpoint dalam satu misi. Terdapat 8 checkpoint yang tersebar di area perbatasan dengan koordinat berikut (dalam km dari markas):

| Checkpoint | X | Y | Prioritas |
|------------|---|---|-----------|
| C1 | 10 | 20 | Tinggi |
| C2 | 30 | 15 | Sedang |
| C3 | 25 | 40 | Tinggi |
| C4 | 45 | 30 | Rendah |
| C5 | 50 | 50 | Tinggi |
| C6 | 15 | 45 | Sedang |
| C7 | 35 | 55 | Rendah |
| C8 | 55 | 25 | Sedang |

**Constraint:**
- Setiap drone memiliki jangkauan maksimal 150 km per misi
- Checkpoint prioritas tinggi harus dikunjungi lebih awal
- Markas berada di koordinat (0, 0)
- Drone harus kembali ke markas setelah misi

**Pertanyaan:**

**1a.** Formulasikan masalah ini sebagai masalah optimisasi. Definisikan:
- Representasi state/chromosome
- Objective function
- Constraint yang harus dipenuhi
(15 poin)

**1b.** Rancang pendekatan Hill Climbing untuk satu drone yang mengunjungi 4 checkpoint. Definisikan:
- Initial state
- Fungsi neighbor (bagaimana generate tetangga)
- Kondisi terminasi
(15 poin)

**1c.** Rancang pendekatan Simulated Annealing untuk masalah yang sama. Tentukan:
- Jadwal pendinginan yang sesuai
- Formula probabilitas penerimaan
- Parameter yang direkomendasikan (T₀, α)
(10 poin)

**1d.** Rancang pendekatan Genetic Algorithm untuk mengoptimalkan alokasi 8 checkpoint ke 3 drone. Definisikan:
- Representasi chromosome
- Fitness function yang mempertimbangkan jarak, prioritas, dan constraint jangkauan
- Operator crossover yang menjaga feasibility
- Operator mutasi
(20 poin)

**1e.** Algoritma mana yang paling sesuai untuk masalah ini? Berikan justifikasi berdasarkan karakteristik masalah dan kebutuhan operasional! (10 poin)

---

### Studi Kasus 2: Penempatan Optimal Radar Pertahanan Pantai

**Latar Belakang:**

TNI Angkatan Laut merencanakan penempatan 5 unit radar pantai untuk memantau aktivitas di Selat Malaka. Area pengawasan adalah grid 200 km × 100 km. Setiap radar memiliki:
- Radius coverage: 40 km
- Biaya instalasi berbeda tergantung lokasi (medan, infrastruktur)
- Tidak boleh ditempatkan di area terlarang (pelabuhan sipil, kawasan lindung)

**Data Area:**

| Zona | X Range | Y Range | Biaya/unit | Status |
|------|---------|---------|------------|--------|
| Z1 | 0-50 | 0-50 | Rendah | Boleh |
| Z2 | 50-100 | 0-50 | Sedang | Boleh |
| Z3 | 100-150 | 0-50 | Tinggi | Boleh |
| Z4 | 150-200 | 0-50 | Sedang | Boleh |
| Z5 | 0-50 | 50-100 | Sedang | Terlarang |
| Z6 | 50-100 | 50-100 | Rendah | Boleh |
| Z7 | 100-150 | 50-100 | Sedang | Boleh |
| Z8 | 150-200 | 50-100 | Tinggi | Terlarang |

**Objective:**
- Maksimalkan coverage area
- Minimalisasi overlap antar radar
- Minimalisasi total biaya instalasi
- Prioritaskan coverage di jalur pelayaran utama (Y = 20-30)

**Pertanyaan:**

**2a.** Formulasikan masalah ini untuk pendekatan pencarian lokal:
- Representasi state
- Objective function (utility function) dengan pembobotan yang wajar
- Definisi tetangga (neighbor)
(15 poin)

**2b.** Implementasikan pseudocode Hill Climbing untuk masalah ini, termasuk:
- Fungsi untuk menghitung coverage
- Fungsi untuk menghitung overlap
- Penanganan constraint area terlarang
(15 poin)

**2c.** Mengapa Simulated Annealing lebih cocok daripada Hill Climbing untuk masalah ini? Jelaskan dengan contoh skenario di mana Hill Climbing akan terjebak! (10 poin)

**2d.** Rancang Genetic Algorithm untuk masalah ini:
- Representasi chromosome (pertimbangkan koordinat kontinu)
- Fitness function
- Operator crossover yang sesuai untuk koordinat
- Strategi untuk menangani solusi infeasible (radar di area terlarang)
(20 poin)

**2e.** Jika waktu komputasi terbatas (harus selesai dalam 10 detik), modifikasi apa yang dapat dilakukan pada masing-masing algoritma untuk menghasilkan solusi yang baik? (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | Pencarian lokal hanya menyimpan state saat ini (memori O(1)), tidak menyimpan jalur |
| 2 | **C** | Plateau adalah area datar di mana semua tetangga memiliki nilai objective function yang sama |
| 3 | **B** | Hill Climbing disebut Greedy Local Search karena selalu memilih langkah terbaik secara lokal |
| 4 | **C** | Steepest Ascent mengevaluasi SEMUA tetangga dan memilih yang nilainya tertinggi |
| 5 | **C** | First-Choice berhenti begitu menemukan tetangga pertama yang lebih baik, efisien untuk tetangga banyak |
| 6 | **B** | P(sukses) = 1 - (1-0.2)^5 = 1 - 0.8^5 = 1 - 0.328 = 0.672 = 67.2% |
| 7 | **B** | Simulated Annealing terinspirasi dari proses annealing (pemanasan dan pendinginan) dalam metalurgi |
| 8 | **C** | Untuk maximization dengan ΔE < 0, probabilitas = e^(ΔE/T). Untuk minimization: e^(-ΔE/T) |
| 9 | **C** | Pada T tinggi, e^(ΔE/T) mendekati 1, sehingga hampir semua langkah diterima (eksplorasi) |
| 10 | **B** | Jadwal exponential: T(t) = T₀ × α^t, dengan α < 1 (biasanya 0.95-0.99) |
| 11 | **D** | 4 state × 3 successor = 12 total successor yang dievaluasi |
| 12 | **C** | Karena memilih k terbaik dari SEMUA successor, bisa kehilangan diversitas |
| 13 | **B** | Chromosome dalam GA merepresentasikan satu solusi kandidat |
| 14 | **C** | Roulette Wheel Selection memilih dengan probabilitas proporsional terhadap fitness |
| 15 | **B** | Single-point crossover di posisi 4 menukar 4 bit terakhir (posisi 4-7) |
| 16 | **C** | Mutation rate biasanya rendah (1-5%) untuk menjaga diversity tanpa merusak solusi baik |
| 17 | **B** | Array 1D: index = kolom, value = baris. Jadi ratu di baris 2,0,3,1 untuk kolom 0,1,2,3 |
| 18 | **B** | Representasi permutasi menunjukkan urutan kunjungan kota, kembali ke awal |
| 19 | **C** | 2-opt membalik urutan segmen rute untuk menghilangkan crossing dan memperbaiki jarak |
| 20 | **B** | Simulated Annealing adalah anytime algorithm - bisa dihentikan kapan saja dengan solusi valid |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Mengapa pencarian lokal cocok untuk optimisasi:**
- Hanya memerlukan **state akhir** (konfigurasi optimal), bukan jalur
- Ruang pencarian optimisasi biasanya sangat besar
- Memori O(1) memungkinkan menangani masalah besar

**Mengapa tidak cocok untuk path-finding:**
- Path-finding memerlukan **urutan langkah** dari awal ke tujuan
- Pencarian lokal tidak menyimpan jalur
- Tidak ada jaminan completeness (mungkin tidak menemukan path yang ada)

---

#### Jawaban Soal 2 ⭐

**Empat fitur landscape:**

1. **Global Maximum/Minimum:** Titik optimal di seluruh landscape - tujuan yang ingin dicapai

2. **Local Maximum/Minimum:** Titik yang lebih baik dari semua tetangganya tetapi bukan yang terbaik secara global - dapat menjebak algoritma

3. **Plateau:** Area datar dengan nilai sama - algoritma kesulitan menentukan arah gerak karena tidak ada gradien

4. **Ridge:** Puncak sempit memanjang - setiap langkah ke samping menurun, sulit untuk bergerak sepanjang ridge

---

#### Jawaban Soal 3 ⭐

| Variasi | Cara Memilih Tetangga | Karakteristik |
|---------|----------------------|---------------|
| **Steepest Ascent** | Evaluasi SEMUA tetangga, pilih yang terbaik | Paling optimal per langkah, tapi lambat jika tetangga banyak |
| **Stochastic** | Pilih ACAK dari tetangga yang lebih baik | Lebih cepat, ada variasi, tidak selalu pilih terbaik |
| **First-Choice** | Pilih PERTAMA yang lebih baik (urutan acak) | Paling cepat untuk tetangga banyak, berhenti setelah menemukan satu |

---

#### Jawaban Soal 4 ⭐

**Tracing Hill Climbing dari C:**

*Step 1:* Posisi C (nilai = 6)
- Tetangga: B (8), D (9)
- D lebih tinggi → pindah ke D

*Step 2:* Posisi D (nilai = 9)
- Tetangga: C (6), E (7)
- Tidak ada yang lebih tinggi dari 9 → **BERHENTI di D**

**Jawaban:** Algoritma berhenti di **posisi D** dengan nilai 9.

*Catatan:* F juga memiliki nilai 9, tetapi tidak dapat dicapai karena harus melewati E (7) yang lebih rendah.

---

#### Jawaban Soal 5 ⭐⭐

**Diketahui:**
- p = 0.15 (probabilitas sukses satu kali)
- Target: P(sukses) ≥ 0.95

**Formula:**
$$1 - (1-p)^k \geq 0.95$$
$$1 - (0.85)^k \geq 0.95$$
$$(0.85)^k \leq 0.05$$

**Perhitungan:**
$$k \cdot \ln(0.85) \leq \ln(0.05)$$
$$k \geq \frac{\ln(0.05)}{\ln(0.85)}$$
$$k \geq \frac{-2.996}{-0.163}$$
$$k \geq 18.4$$

**Jawaban:** Diperlukan minimal **19 restart** untuk mencapai probabilitas sukses 95%.

---

#### Jawaban Soal 6 ⭐⭐

**Diketahui:**
- Current value = 80
- Neighbor value = 75
- ΔE = 75 - 80 = -5 (untuk maximization, ini langkah buruk)

**a) Probabilitas pada T = 10:**
$$P = e^{-5/10} = e^{-0.5} = 0.6065 = 60.65\%$$

**b) Probabilitas pada T = 1:**
$$P = e^{-5/1} = e^{-5} = 0.0067 = 0.67\%$$

**c) Interpretasi:**
- Pada T tinggi (10): Probabilitas 60.65% untuk menerima langkah buruk → **eksplorasi aktif**
- Pada T rendah (1): Probabilitas 0.67% untuk menerima langkah buruk → **eksploitasi**, hampir seperti Hill Climbing

---

#### Jawaban Soal 7 ⭐⭐

**Diketahui:** T(t) = 50 × 0.9^t

**a) Temperatur pada iterasi ke-5:**
$$T(5) = 50 \times 0.9^5 = 50 \times 0.59049 = 29.52$$

**b) Iterasi ketika T < 5:**
$$50 \times 0.9^t < 5$$
$$0.9^t < 0.1$$
$$t \cdot \ln(0.9) < \ln(0.1)$$
$$t > \frac{\ln(0.1)}{\ln(0.9)}$$
$$t > \frac{-2.303}{-0.105}$$
$$t > 21.85$$

**Jawaban:** Temperatur turun di bawah 5 pada **iterasi ke-22** atau lebih.

---

#### Jawaban Soal 8 ⭐⭐

**Hill Climbing tidak bisa keluar dari local optima karena:**
- Hanya menerima langkah yang lebih baik
- Di local optima, semua tetangga lebih buruk
- Algoritma langsung berhenti

**Simulated Annealing bisa keluar karena:**
- Dapat menerima langkah lebih buruk dengan probabilitas e^(ΔE/T)
- Pada temperatur tinggi, probabilitas penerimaan tinggi
- Memungkinkan "melompat" keluar dari local optima
- Seiring temperatur menurun, menjadi lebih selektif dan konvergen

**Analogi:** SA seperti bola yang diguncang - pada awalnya bisa melompat kemana-mana (T tinggi), lama-kelamaan menetap di lembah terdalam (T rendah).

---

#### Jawaban Soal 9 ⭐⭐

**Langkah penyelesaian:**

*Step 1:* Kumpulkan semua successor
- X1(12), X2(8), X3(15), Y1(10), Y2(14), Y3(9), Z1(11), Z2(7), Z3(13)

*Step 2:* Urutkan berdasarkan nilai (descending)
1. X3: 15
2. Y2: 14
3. Z3: 13
4. X1: 12
5. Z1: 11
6. Y1: 10
7. Y3: 9
8. X2: 8
9. Z2: 7

*Step 3:* Pilih k=3 terbaik

**Jawaban:** State yang dipilih adalah **{X3, Y2, Z3}** dengan nilai 15, 14, dan 13.

---

#### Jawaban Soal 10 ⭐⭐

**Diketahui:**
- P: fitness = 40
- Q: fitness = 25
- R: fitness = 35
- Total = 40 + 25 + 35 = 100

**Probabilitas:**
$$P(P) = \frac{40}{100} = 0.40 = 40\%$$
$$P(Q) = \frac{25}{100} = 0.25 = 25\%$$
$$P(R) = \frac{35}{100} = 0.35 = 35\%$$

**Jawaban:** P(P) = 40%, P(Q) = 25%, P(R) = 35%

---

#### Jawaban Soal 11 ⭐⭐

**Diketahui:**
- Parent 1: [1, 0, 0, 1, 1, 0]
- Parent 2: [0, 1, 1, 0, 0, 1]
- Titik potong: setelah posisi 3

**Proses:**
```
Parent 1: [1, 0, 0 | 1, 1, 0]
Parent 2: [0, 1, 1 | 0, 0, 1]
          ↑ posisi 0-2  ↑ posisi 3-5
```

**Hasil:**
- Offspring 1: [1, 0, 0] + [0, 0, 1] = **[1, 0, 0, 0, 0, 1]**
- Offspring 2: [0, 1, 1] + [1, 1, 0] = **[0, 1, 1, 1, 1, 0]**

---

#### Jawaban Soal 12 ⭐⭐⭐

**State:** [1, 3, 0, 2]

**a) Gambar posisi ratu:**
```
     0   1   2   3  (kolom)
   ┌───┬───┬───┬───┐
 0 │   │   │ Q │   │  ← state[2] = 0
   ├───┼───┼───┼───┤
 1 │ Q │   │   │   │  ← state[0] = 1
   ├───┼───┼───┼───┤
 2 │   │   │   │ Q │  ← state[3] = 2
   ├───┼───┼───┼───┤
 3 │   │ Q │   │   │  ← state[1] = 3
   └───┴───┴───┴───┘
(baris)
```

**b) Hitung pasangan menyerang:**

| Pasangan | Kolom (i,j) | Baris (state[i], state[j]) | Sama baris? | Diagonal? (|Δrow|=|Δcol|) | Menyerang? |
|----------|-------------|---------------------------|-------------|---------------------------|------------|
| (0,1) | 0,1 | 1,3 | Tidak | |1-3|=2, |0-1|=1, 2≠1 | ❌ |
| (0,2) | 0,2 | 1,0 | Tidak | |1-0|=1, |0-2|=2, 1≠2 | ❌ |
| (0,3) | 0,3 | 1,2 | Tidak | |1-2|=1, |0-3|=3, 1≠3 | ❌ |
| (1,2) | 1,2 | 3,0 | Tidak | |3-0|=3, |1-2|=1, 3≠1 | ❌ |
| (1,3) | 1,3 | 3,2 | Tidak | |3-2|=1, |1-3|=2, 1≠2 | ❌ |
| (2,3) | 2,3 | 0,2 | Tidak | |0-2|=2, |2-3|=1, 2≠1 | ❌ |

**h = 0** (tidak ada pasangan yang menyerang)

**c) Apakah solusi valid?**

**Ya, ini adalah solusi valid** karena h = 0 (tidak ada ratu yang saling menyerang).

---

#### Jawaban Soal 13 ⭐⭐⭐

**Matriks jarak:**
|   | A | B | C | D |
|---|---|---|---|---|
| A | 0 | 10| 15| 20|
| B | 10| 0 | 25| 30|
| C | 15| 25| 0 | 35|
| D | 20| 30| 35| 0 |

**a) Total jarak rute [A, B, C, D, A]:**
- A→B: 10
- B→C: 25
- C→D: 35
- D→A: 20
- **Total: 10 + 25 + 35 + 20 = 90**

**b) Terapkan 2-opt (balik segmen B-C):**
- Rute awal: [A, **B, C**, D]
- Segmen [B, C] dibalik menjadi [C, B]
- Rute baru: [A, **C, B**, D]

**c) Hitung jarak rute baru [A, C, B, D, A]:**
- A→C: 15
- C→B: 25
- B→D: 30
- D→A: 20
- **Total: 15 + 25 + 30 + 20 = 90**

**Kesimpulan:** Jarak sama (90), operasi 2-opt ini **tidak menghasilkan perbaikan**.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Fitness Function untuk Penjadwalan Shift:**

```python
def fitness(schedule, num_personnel, num_shifts, num_days):
    """
    schedule: matrix [personnel][day] = list of shifts assigned
    """
    penalty = 0
    
    # Penalty 1: Shift kosong
    empty_shifts = count_empty_shifts(schedule)
    penalty += empty_shifts * 10  # High penalty
    
    # Penalty 2: Lebih dari 2 shift per hari per personel
    for person in range(num_personnel):
        for day in range(num_days):
            shifts_count = len(schedule[person][day])
            if shifts_count > 2:
                penalty += (shifts_count - 2) * 20  # Very high penalty
    
    # Penalty 3: Distribusi tidak merata
    total_shifts_per_person = [sum(len(schedule[p][d]) 
                               for d in range(num_days)) 
                               for p in range(num_personnel)]
    avg_shifts = sum(total_shifts_per_person) / num_personnel
    
    variance = sum((s - avg_shifts)**2 for s in total_shifts_per_person)
    penalty += variance * 0.5  # Moderate penalty
    
    # Fitness = inverse of penalty
    return 1000 / (1 + penalty)
```

---

#### Jawaban Soal 15 ⭐⭐⭐

**Perbandingan untuk masalah dengan ruang besar, banyak local optima, dan evaluasi mahal:**

| Aspek | Hill Climbing | Simulated Annealing | Genetic Algorithm |
|-------|---------------|---------------------|-------------------|
| **Ruang besar** | ✅ Baik (O(1) memori) | ✅ Baik (O(1) memori) | ⚠️ Perlu populasi |
| **Banyak local optima** | ❌ Sering terjebak | ✅ Bisa escape | ✅ Bisa escape |
| **Evaluasi mahal** | ✅ Sedikit evaluasi | ⚠️ Banyak evaluasi | ❌ Sangat banyak evaluasi |
| **Kualitas solusi** | Rendah | Tinggi | Tinggi |
| **Waktu konvergensi** | Cepat | Sedang | Lambat |

**Rekomendasi:**
- **Simulated Annealing** paling sesuai karena dapat escape local optima dengan memori konstan
- Untuk evaluasi sangat mahal, pertimbangkan **Random Restart Hill Climbing** dengan jumlah restart terbatas
- **GA** hanya jika paralelisasi memungkinkan untuk mengatasi biaya evaluasi

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Optimisasi Rute Patroli Drone

**1a. Formulasi Masalah (15 poin)**

**Representasi State/Chromosome:**
```python
# Untuk 3 drone dan 8 checkpoint
# Chromosome = list of tuples (drone_id, [checkpoint_sequence])
chromosome = [
    (0, [C1, C3, C5]),      # Drone 0: C1 → C3 → C5
    (1, [C2, C4, C8]),      # Drone 1: C2 → C4 → C8
    (2, [C6, C7])           # Drone 2: C6 → C7
]

# Alternatif: flat encoding
chromosome = [0, 1, 0, 1, 0, 2, 2, 1]  
# checkpoint[i] ditangani oleh drone chromosome[i]
```

**Objective Function:**
```python
def objective(chromosome, checkpoints, markas=(0,0)):
    total_score = 0
    
    for drone_id in range(3):
        route = get_route(chromosome, drone_id)
        
        # Komponen 1: Minimalisasi jarak
        distance = calculate_distance(markas, route, markas)
        total_score -= distance * 1.0
        
        # Komponen 2: Prioritas checkpoint
        for i, checkpoint in enumerate(route):
            priority_bonus = get_priority(checkpoint) * (len(route) - i)
            total_score += priority_bonus * 2.0
    
    return total_score
```

**Constraint:**
- Jarak total per drone ≤ 150 km
- Setiap checkpoint dikunjungi tepat sekali
- Checkpoint prioritas tinggi lebih awal (soft constraint via objective)

---

**1b. Pendekatan Hill Climbing untuk Satu Drone (15 poin)**

**Initial State:** Random permutasi 4 checkpoint dari yang tersedia

**Fungsi Neighbor:**
```python
def get_neighbors(state):
    neighbors = []
    n = len(state)
    
    # Swap: tukar posisi dua checkpoint
    for i in range(n):
        for j in range(i+1, n):
            new_state = state.copy()
            new_state[i], new_state[j] = new_state[j], new_state[i]
            neighbors.append(new_state)
    
    # 2-opt: balik segmen
    for i in range(n):
        for j in range(i+2, n):
            new_state = state[:i] + state[i:j+1][::-1] + state[j+1:]
            neighbors.append(new_state)
    
    return neighbors
```

**Kondisi Terminasi:**
- Tidak ada tetangga dengan nilai lebih baik
- Atau mencapai iterasi maksimum

---

**1c. Pendekatan Simulated Annealing (10 poin)**

**Jadwal Pendinginan:** Exponential
```python
T(t) = T0 * alpha^t
# Rekomendasi: T0 = 100, alpha = 0.95
```

**Formula Probabilitas:**
$$P(\text{terima}) = e^{(\text{value}_{new} - \text{value}_{current}) / T}$$

**Parameter:**
- T₀ = 100 (cukup tinggi untuk eksplorasi awal)
- α = 0.95 (pendinginan sedang)
- Iterasi maksimum: 1000-5000

---

**1d. Genetic Algorithm untuk 3 Drone (20 poin)**

**Representasi Chromosome:**
```python
# [assignment, order] untuk setiap checkpoint
# assignment[i] = drone yang menangani checkpoint i
# order[i] = urutan kunjungan dalam drone tersebut

chromosome = {
    'assignment': [0, 1, 0, 2, 0, 1, 2, 1],
    'order': [1, 1, 2, 1, 3, 2, 2, 3]
}
```

**Fitness Function:**
```python
def fitness(chromosome, checkpoints):
    score = 0
    
    for drone in range(3):
        route = get_sorted_route(chromosome, drone)
        
        # Bonus coverage
        score += len(route) * 10
        
        # Bonus prioritas (early visit)
        for i, cp in enumerate(route):
            priority = checkpoints[cp]['priority']
            score += priority * (len(route) - i)
        
        # Penalty jarak berlebih
        distance = calculate_total_distance(route)
        if distance > 150:
            score -= (distance - 150) * 50
        else:
            score += (150 - distance) * 0.5
    
    return score
```

**Crossover:**
```python
def crossover(parent1, parent2):
    # Uniform crossover untuk assignment
    child_assignment = []
    for i in range(8):
        if random.random() < 0.5:
            child_assignment.append(parent1['assignment'][i])
        else:
            child_assignment.append(parent2['assignment'][i])
    
    # Order inheritance dari parent dengan fitness lebih tinggi
    child_order = parent1['order'] if fitness(parent1) > fitness(parent2) \
                  else parent2['order']
    
    return {'assignment': child_assignment, 'order': child_order}
```

**Mutasi:**
```python
def mutate(chromosome, rate=0.1):
    if random.random() < rate:
        # Ubah assignment satu checkpoint
        i = random.randint(0, 7)
        chromosome['assignment'][i] = random.randint(0, 2)
    
    if random.random() < rate:
        # Ubah order
        i = random.randint(0, 7)
        max_order = chromosome['order'].count(chromosome['assignment'][i])
        chromosome['order'][i] = random.randint(1, max_order + 1)
    
    return chromosome
```

---

**1e. Rekomendasi Algoritma (10 poin)**

**Rekomendasi: Genetic Algorithm**

**Justifikasi:**
1. **Masalah multi-vehicle:** GA dapat mengoptimalkan alokasi ke 3 drone secara bersamaan
2. **Multiple constraint:** Fitness function dapat menangani jarak, prioritas, dan coverage
3. **Ruang pencarian besar:** Kombinasi assignment dan ordering memerlukan eksplorasi luas
4. **Operasional:** Dapat dijalankan offline sebelum misi untuk mendapatkan solusi berkualitas

**Alternatif:** Jika waktu terbatas, gunakan **Simulated Annealing** dengan representasi yang sama.

---

#### Studi Kasus 2: Penempatan Radar Pertahanan Pantai

**2a. Formulasi untuk Pencarian Lokal (15 poin)**

**Representasi State:**
```python
# State = list of 5 radar positions (x, y)
state = [(25, 30), (75, 25), (125, 40), (170, 35), (60, 75)]
```

**Objective Function:**
```python
def objective(state, grid_points, shipping_lane_y=(20,30)):
    coverage_score = 0
    overlap_penalty = 0
    cost_penalty = 0
    lane_bonus = 0
    
    # Coverage: count unique grid points covered
    covered = set()
    for radar in state:
        for point in grid_points:
            if distance(radar, point) <= 40:
                covered.add(point)
    coverage_score = len(covered) / len(grid_points) * 100
    
    # Overlap penalty
    for i in range(5):
        for j in range(i+1, 5):
            overlap_area = calculate_overlap(state[i], state[j], radius=40)
            overlap_penalty += overlap_area * 0.1
    
    # Cost based on zone
    for radar in state:
        zone_cost = get_zone_cost(radar)
        cost_penalty += zone_cost
    
    # Shipping lane bonus
    for radar in state:
        if shipping_lane_y[0] <= radar[1] <= shipping_lane_y[1]:
            lane_bonus += 10
    
    # Weighted sum (weights can be tuned)
    return (0.4 * coverage_score + 
            0.3 * lane_bonus - 
            0.2 * overlap_penalty - 
            0.1 * cost_penalty)
```

**Definisi Tetangga:**
```python
def get_neighbors(state, step=5):
    neighbors = []
    for i in range(5):
        for dx, dy in [(step,0), (-step,0), (0,step), (0,-step),
                       (step,step), (step,-step), (-step,step), (-step,-step)]:
            new_state = state.copy()
            new_x = state[i][0] + dx
            new_y = state[i][1] + dy
            
            # Boundary check
            if 0 <= new_x <= 200 and 0 <= new_y <= 100:
                # Forbidden zone check
                if not is_forbidden(new_x, new_y):
                    new_state[i] = (new_x, new_y)
                    neighbors.append(new_state)
    
    return neighbors
```

---

**2b. Pseudocode Hill Climbing (15 poin)**

```python
def hill_climbing_radar(max_iter=1000):
    # Initialize: random valid positions
    current = []
    for _ in range(5):
        while True:
            x = random.uniform(0, 200)
            y = random.uniform(0, 100)
            if not is_forbidden(x, y):
                current.append((x, y))
                break
    
    current_value = objective(current)
    
    for iteration in range(max_iter):
        neighbors = get_neighbors(current)
        
        # Filter out infeasible neighbors
        valid_neighbors = [n for n in neighbors 
                          if all(not is_forbidden(r[0], r[1]) for r in n)]
        
        if not valid_neighbors:
            break
        
        best_neighbor = max(valid_neighbors, key=objective)
        best_value = objective(best_neighbor)
        
        if best_value <= current_value:
            break  # Local optimum reached
        
        current = best_neighbor
        current_value = best_value
    
    return current, current_value

def calculate_coverage(state, grid_resolution=5):
    """Calculate percentage of area covered"""
    covered_points = 0
    total_points = 0
    
    for x in range(0, 201, grid_resolution):
        for y in range(0, 101, grid_resolution):
            total_points += 1
            for radar in state:
                if distance((x, y), radar) <= 40:
                    covered_points += 1
                    break
    
    return covered_points / total_points * 100

def calculate_overlap(radar1, radar2, radius=40):
    """Calculate overlap area between two radars"""
    d = distance(radar1, radar2)
    if d >= 2 * radius:
        return 0
    if d == 0:
        return math.pi * radius**2
    
    # Intersection area formula
    r = radius
    area = 2 * r**2 * math.acos(d/(2*r)) - 0.5 * d * math.sqrt(4*r**2 - d**2)
    return area

def is_forbidden(x, y):
    """Check if position is in forbidden zone"""
    # Z5: (0-50, 50-100)
    if 0 <= x <= 50 and 50 <= y <= 100:
        return True
    # Z8: (150-200, 50-100)
    if 150 <= x <= 200 and 50 <= y <= 100:
        return True
    return False
```

---

**2c. Mengapa SA Lebih Cocok (10 poin)**

**SA lebih cocok karena:**

1. **Landscape kompleks:** Banyak local optima karena tradeoff coverage vs overlap vs cost
2. **Koordinat kontinu:** Banyak konfigurasi yang mirip nilainya

**Skenario Hill Climbing terjebak:**

Misalkan konfigurasi awal memberikan coverage 75% dengan 5 radar tersebar merata. Hill Climbing akan terjebak karena:
- Menggeser satu radar mengurangi coverage di area lama
- Menambah coverage di area baru mungkin tidak cukup mengkompensasi
- Semua langkah lokal tampak "menurun"

Padahal, jika kita berani menggeser 2-3 radar bersamaan (yang tidak bisa dilakukan Hill Climbing dalam satu langkah), kita bisa mendapat coverage 85% dengan pengaturan yang lebih efisien.

**SA dapat keluar** dengan menerima langkah "buruk" sementara untuk mencapai konfigurasi yang lebih baik.

---

**2d. Genetic Algorithm (20 poin)**

**Representasi Chromosome:**
```python
# Real-valued encoding untuk koordinat
chromosome = [x1, y1, x2, y2, x3, y3, x4, y4, x5, y5]
# 10 genes untuk 5 radar
```

**Fitness Function:**
```python
def fitness(chromosome):
    radars = [(chromosome[2*i], chromosome[2*i+1]) for i in range(5)]
    
    # Check feasibility
    for radar in radars:
        if is_forbidden(radar[0], radar[1]):
            return 0  # Invalid solution
    
    coverage = calculate_coverage(radars)
    overlap = sum(calculate_overlap(radars[i], radars[j]) 
                  for i in range(5) for j in range(i+1, 5))
    cost = sum(get_zone_cost(r) for r in radars)
    lane_coverage = sum(1 for r in radars if 20 <= r[1] <= 30)
    
    return 40 * coverage + 10 * lane_coverage - 5 * overlap - 2 * cost
```

**Crossover (BLX-α untuk koordinat kontinu):**
```python
def blx_crossover(parent1, parent2, alpha=0.5):
    child = []
    for i in range(len(parent1)):
        p1, p2 = parent1[i], parent2[i]
        min_val = min(p1, p2)
        max_val = max(p1, p2)
        range_val = max_val - min_val
        
        # Extend range by alpha
        low = min_val - alpha * range_val
        high = max_val + alpha * range_val
        
        # Generate child gene
        child.append(random.uniform(low, high))
    
    return child
```

**Strategi Infeasible Solution:**
```python
def repair(chromosome):
    """Move radar out of forbidden zones"""
    radars = [(chromosome[2*i], chromosome[2*i+1]) for i in range(5)]
    
    for i, radar in enumerate(radars):
        if is_forbidden(radar[0], radar[1]):
            # Move to nearest valid position
            new_pos = find_nearest_valid(radar)
            chromosome[2*i] = new_pos[0]
            chromosome[2*i+1] = new_pos[1]
    
    return chromosome

def find_nearest_valid(pos):
    """Find nearest position outside forbidden zones"""
    # Check boundaries of forbidden zones
    candidates = []
    
    # Z5 boundaries
    if 0 <= pos[0] <= 50:
        candidates.append((pos[0], 49.9))  # Just below Z5
    
    # Z8 boundaries
    if 150 <= pos[0] <= 200:
        candidates.append((pos[0], 49.9))  # Just below Z8
    
    # Find closest
    return min(candidates, key=lambda c: distance(pos, c))
```

**Mutasi:**
```python
def mutate(chromosome, rate=0.1, sigma=10):
    for i in range(len(chromosome)):
        if random.random() < rate:
            # Gaussian mutation
            chromosome[i] += random.gauss(0, sigma)
            
            # Boundary enforcement
            if i % 2 == 0:  # x coordinate
                chromosome[i] = max(0, min(200, chromosome[i]))
            else:  # y coordinate
                chromosome[i] = max(0, min(100, chromosome[i]))
    
    return repair(chromosome)
```

---

**2e. Modifikasi untuk Waktu Terbatas (10 poin)**

**Hill Climbing:**
- Gunakan **First-Choice** untuk evaluasi lebih sedikit
- Batasi jumlah tetangga yang digenerate
- Gunakan step size lebih besar untuk konvergensi cepat

**Simulated Annealing:**
- Gunakan jadwal pendinginan **lebih cepat** (α = 0.8-0.85)
- Mulai dengan T₀ lebih rendah
- Batasi iterasi maksimum berdasarkan waktu
- Implementasi **anytime**: simpan solusi terbaik setiap iterasi

**Genetic Algorithm:**
- **Kurangi population size** (20-30 individu)
- Gunakan **elitism** untuk menjaga solusi terbaik
- Batasi generasi berdasarkan waktu
- Implementasi **steady-state GA**: ganti individu terburuk satu per satu

**Rekomendasi untuk 10 detik:** 
- **Simulated Annealing** dengan T₀=50, α=0.9, max_iter berdasarkan waktu
- Atau **Random Restart HC** dengan 5-10 restart

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
- Studi Kasus 1: 70 poin
- Studi Kasus 2: 70 poin
- Total: 140 poin

### Total Keseluruhan: 295 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
