# Latihan Pertemuan 05: Pencarian Adversarial - Game Playing

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 05  
**Topik:** Pencarian Adversarial - Game Playing  
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
Pencarian adversarial berbeda dari pencarian biasa (seperti A*) karena:

A. Tidak menggunakan heuristik  
B. Tidak memiliki goal state  
C. Terdapat agen lawan yang juga bermain optimal  
D. Selalu menghasilkan solusi optimal  
E. Tidak memerlukan fungsi evaluasi

---

### Soal 2
Dalam zero-sum game, jika pemain MAX mendapatkan utility +10, maka utility pemain MIN adalah:

A. +10  
B. +5  
C. 0  
D. -10  
E. Tidak dapat ditentukan

---

### Soal 3
Game yang termasuk kategori deterministik dengan perfect information adalah:

A. Poker  
B. Backgammon  
C. Catur  
D. Bridge  
E. Monopoli

---

### Soal 4
Backgammon termasuk kategori game:

A. Deterministik, Perfect Information  
B. Deterministik, Imperfect Information  
C. Stokastik, Perfect Information  
D. Stokastik, Imperfect Information  
E. Non-zero-sum game

---

### Soal 5
Dalam game tree, node yang merepresentasikan giliran lawan disebut:

A. MAX node  
B. MIN node  
C. Terminal node  
D. Chance node  
E. Root node

---

### Soal 6
Terminal state dalam game tree adalah:

A. State awal permainan  
B. State di mana permainan berakhir  
C. State dengan branching factor tertinggi  
D. State pada kedalaman 1  
E. State yang dipilih oleh MAX

---

### Soal 7
Jika branching factor adalah 5 dan kedalaman adalah 4, berapa perkiraan jumlah node yang dievaluasi oleh Minimax?

A. 20  
B. 25  
C. 125  
D. 625  
E. 3125

---

### Soal 8
Prinsip dasar algoritma Minimax adalah:

A. MAX dan MIN sama-sama memaksimalkan utility  
B. MAX memaksimalkan, MIN meminimalkan utility  
C. MAX meminimalkan, MIN memaksimalkan utility  
D. Kedua pemain memilih secara acak  
E. Hanya MAX yang membuat keputusan

---

### Soal 9
Kompleksitas waktu algoritma Minimax adalah:

A. O(b + m)  
B. O(b × m)  
C. O(b^m)  
D. O(m^b)  
E. O(log b^m)

---

### Soal 10
Fungsi evaluasi digunakan untuk:

A. Menghitung utility pada terminal state  
B. Memperkirakan nilai state non-terminal  
C. Menentukan branching factor  
D. Menghitung kedalaman tree  
E. Memilih langkah pertama

---

### Soal 11
Dalam Alpha-Beta Pruning, α (alpha) merepresentasikan:

A. Nilai maksimum yang dijamin MIN  
B. Nilai minimum yang dijamin MAX  
C. Nilai rata-rata semua node  
D. Kedalaman pencarian  
E. Branching factor

---

### Soal 12
Pruning terjadi pada MIN node ketika:

A. Nilai ≥ β  
B. Nilai ≤ α  
C. Nilai = 0  
D. α = β  
E. Nilai > α

---

### Soal 13
Kompleksitas waktu Alpha-Beta Pruning dengan perfect move ordering adalah:

A. O(b^m)  
B. O(b^(m/2))  
C. O(b^(2m))  
D. O(m × b)  
E. O(log b^m)

---

### Soal 14
Teknik yang TIDAK digunakan untuk meningkatkan move ordering adalah:

A. Killer Move Heuristic  
B. History Heuristic  
C. Iterative Deepening  
D. Transposition Table  
E. Breadth-First Search

---

### Soal 15
Expectiminimax digunakan untuk game yang memiliki karakteristik:

A. Perfect information  
B. Imperfect information  
C. Elemen stokastik (keacakan)  
D. Single player  
E. Non-zero-sum

---

### Soal 16
Pada Expectiminimax, chance node menghitung:

A. Nilai maksimum  
B. Nilai minimum  
C. Expected value (nilai harapan)  
D. Nilai random  
E. Nilai konstan

---

### Soal 17
Alpha-Beta Pruning kurang efektif pada Expectiminimax karena:

A. Tidak ada terminal state  
B. Chance nodes memerlukan evaluasi semua children  
C. Branching factor terlalu kecil  
D. Tidak ada fungsi evaluasi  
E. Game tree terlalu dangkal

---

### Soal 18
Jika sebuah game tree memiliki node MAX di root dengan tiga children (MIN nodes) yang memiliki nilai 5, 3, dan 7, maka nilai Minimax di root adalah:

A. 3  
B. 5  
C. 7  
D. 15  
E. 5 (rata-rata)

---

### Soal 19
Dalam evaluasi posisi catur, feature yang paling penting biasanya adalah:

A. Kontrol pusat  
B. Material advantage  
C. Pawn structure  
D. King safety  
E. Mobility

---

### Soal 20
Deep Blue mengalahkan Kasparov pada tahun 1997 dengan menggunakan:

A. Pure Minimax tanpa pruning  
B. Minimax dengan Alpha-Beta dan fungsi evaluasi  
C. Monte Carlo Tree Search  
D. Reinforcement Learning  
E. Neural Networks

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara pencarian adversarial dan pencarian single-agent yang telah dipelajari sebelumnya (seperti A*)!

---

### Soal 2 ⭐
Apa yang dimaksud dengan zero-sum game? Berikan dua contoh game yang termasuk zero-sum dan jelaskan mengapa!

---

### Soal 3 ⭐
Jelaskan empat karakteristik game yang menjadi fokus pembahasan algoritma Minimax standar!

---

### Soal 4 ⭐
Sebutkan dan jelaskan komponen-komponen utama dalam game tree!

---

### Soal 5 ⭐⭐
Gambarkan game tree untuk permainan Nim sederhana dengan 4 batang, dimana setiap giliran pemain dapat mengambil 1 atau 2 batang. Pemain yang mengambil batang terakhir kalah. Tentukan strategi optimal!

---

### Soal 6 ⭐⭐
Hitung nilai Minimax untuk setiap node pada game tree berikut:

```
           A (MAX)
         /    \
        B      C (MIN)
       /\     /|\
      4  6   3 5 2
```

---

### Soal 7 ⭐⭐
Jelaskan mengapa kompleksitas waktu Minimax adalah O(b^m)! Apa implikasinya untuk game dengan branching factor dan kedalaman yang besar seperti catur?

---

### Soal 8 ⭐⭐
Apa yang dimaksud dengan fungsi evaluasi? Sebutkan empat properti fungsi evaluasi yang baik!

---

### Soal 9 ⭐⭐
Rancang fungsi evaluasi sederhana untuk permainan Tic-Tac-Toe! Jelaskan features yang Anda gunakan dan bobot masing-masing!

---

### Soal 10 ⭐⭐
Jelaskan konsep Alpha dan Beta dalam Alpha-Beta Pruning! Kapan pruning terjadi pada MAX node dan kapan pada MIN node?

---

### Soal 11 ⭐⭐⭐
Terapkan Alpha-Beta Pruning pada game tree berikut. Tunjukkan nilai α dan β pada setiap langkah dan identifikasi node yang di-prune!

```
              A (MAX)
           /    |    \
          B     C     D (MIN)
         /\    /\    /\
        8  5  6  2  1  9
```

---

### Soal 12 ⭐⭐⭐
Jelaskan bagaimana iterative deepening dapat meningkatkan efisiensi Alpha-Beta Pruning! Mengapa overhead dari pencarian berulang tidak signifikan?

---

### Soal 13 ⭐⭐⭐
Bandingkan kompleksitas Minimax murni dengan Alpha-Beta Pruning untuk catur dengan b=35 dan m=6! Hitung perkiraan jumlah node yang dievaluasi untuk masing-masing!

---

### Soal 14 ⭐⭐⭐
Jelaskan algoritma Expectiminimax! Mengapa algoritma ini diperlukan untuk game seperti Backgammon? Berikan contoh perhitungan sederhana!

---

### Soal 15 ⭐⭐⭐
Dalam konteks cyber security, bagaimana pencarian adversarial dapat digunakan untuk memodelkan interaksi antara attacker dan defender? Jelaskan formulasi game-nya!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Pengambilan Keputusan Taktis Militer

**Latar Belakang:**

Sebuah unit taktis TNI AD sedang menghadapi situasi dimana mereka harus mempertahankan sebuah pos strategis dari serangan musuh. Komandan unit memiliki informasi bahwa musuh akan menyerang dalam waktu dekat dan harus memutuskan strategi pertahanan optimal.

**Skenario:**
- **Defender (TNI AD)** memiliki 3 pilihan strategi pertahanan:
  - D1: Pertahanan terpusat di pos utama
  - D2: Pertahanan tersebar dengan patroli
  - D3: Pertahanan berlapis dengan cadangan

- **Attacker (Musuh)** memiliki 3 pilihan strategi serangan:
  - A1: Serangan frontal langsung
  - A2: Serangan mengapit dari dua sisi
  - A3: Serangan infiltrasi malam hari

**Matriks Payoff (dari perspektif Defender, skala -10 hingga +10):**

| Defender \ Attacker | A1 (Frontal) | A2 (Mengapit) | A3 (Infiltrasi) |
|---------------------|--------------|---------------|-----------------|
| D1 (Terpusat) | +8 | -4 | -2 |
| D2 (Tersebar) | +2 | +6 | -3 |
| D3 (Berlapis) | +4 | +3 | +5 |

**Pertanyaan:**

**1a.** Formulasikan skenario ini sebagai two-player zero-sum game. Identifikasi siapa MAX dan siapa MIN, serta jelaskan interpretasi nilai payoff! (10 poin)

**1b.** Gambarkan game tree untuk skenario ini dengan asumsi Defender bergerak terlebih dahulu (dan Attacker melihat pilihan Defender). Tentukan nilai Minimax dan strategi optimal Defender! (15 poin)

**1c.** Bagaimana jika kedua pihak memilih secara simultan (tidak ada yang melihat pilihan lawan)? Analisis strategi yang berbeda dengan skenario sequential! (10 poin)

**1d.** Misalkan terdapat faktor ketidakpastian: cuaca buruk (probabilitas 40%) mengurangi efektivitas serangan infiltrasi sebesar 50%. Modifikasi analisis Anda menggunakan konsep Expectiminimax! (15 poin)

**1e.** Dari perspektif komandan TNI AD, rekomendasi strategi apa yang Anda berikan? Jelaskan reasoning berdasarkan analisis game theory! (10 poin)

---

### Studi Kasus 2: AI untuk Sistem Pertahanan Cyber Command and Control

**Latar Belakang:**

Badan Siber dan Sandi Negara (BSSN) sedang mengembangkan sistem AI untuk membantu pengambilan keputusan dalam pertahanan infrastruktur siber kritis nasional. Sistem ini harus mampu mengantisipasi dan merespons serangan siber secara real-time.

**Skenario:**
Terdapat 5 sistem kritis yang harus dilindungi:
- S1: Sistem Keuangan Nasional (kerugian jika diserang: 100)
- S2: Sistem Kelistrikan (kerugian: 80)
- S3: Sistem Telekomunikasi (kerugian: 60)
- S4: Sistem Transportasi (kerugian: 40)
- S5: Sistem Kesehatan (kerugian: 30)

**Kondisi:**
- **Defender** memiliki sumber daya untuk memperkuat pertahanan 2 sistem
- Sistem yang diperkuat tidak dapat diserang (100% aman)
- **Attacker** akan memilih 1 sistem untuk diserang
- Jika sistem tidak diperkuat dan diserang, kerugian terjadi sesuai nilai di atas
- Ini adalah zero-sum game (kerugian Defender = keuntungan Attacker)

**Pertanyaan:**

**2a.** Buat matriks payoff lengkap untuk game ini! Defender memilih kombinasi 2 sistem dari 5 (C(5,2) = 10 pilihan), Attacker memilih 1 dari 5 sistem. (15 poin)

**2b.** Terapkan algoritma Minimax untuk menentukan strategi optimal Defender dan Attacker. Tunjukkan game tree (bisa disederhanakan) dan perhitungan nilai Minimax! (20 poin)

**2c.** Rancang fungsi evaluasi untuk sistem AI yang dapat memperkirakan "kerentanan" konfigurasi pertahanan tanpa harus menghitung semua kemungkinan serangan! (15 poin)

**2d.** Jika waktu respons menjadi faktor (sistem AI harus memutuskan dalam milidetik), jelaskan bagaimana Alpha-Beta Pruning dapat diterapkan dan berapa pengurangan komputasi yang diharapkan! (10 poin)

**2e.** Dalam skenario nyata, attacker mungkin tidak selalu rasional atau memiliki informasi tidak lengkap. Bagaimana Anda memodifikasi model untuk menangani ketidakpastian ini? (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | Pencarian adversarial melibatkan agen lawan yang juga bermain optimal, berbeda dengan single-agent search |
| 2 | **D** | Dalam zero-sum game, U_MAX + U_MIN = 0, sehingga jika MAX = +10, maka MIN = -10 |
| 3 | **C** | Catur adalah deterministik (tidak ada keacakan) dan perfect information (semua bidak terlihat) |
| 4 | **C** | Backgammon menggunakan dadu (stokastik) tapi semua posisi bidak terlihat (perfect information) |
| 5 | **B** | MIN node adalah giliran lawan yang berusaha meminimalkan nilai utility |
| 6 | **B** | Terminal state adalah state dimana permainan berakhir (menang, kalah, atau draw) |
| 7 | **D** | Jumlah node = b^m = 5^4 = 625 |
| 8 | **B** | Minimax: MAX memaksimalkan utility, MIN meminimalkan utility |
| 9 | **C** | Kompleksitas waktu Minimax adalah O(b^m), eksponensial terhadap kedalaman |
| 10 | **B** | Fungsi evaluasi memperkirakan nilai state non-terminal ketika tidak bisa eksplorasi sampai terminal |
| 11 | **B** | Alpha (α) adalah nilai minimum yang dijamin dapat diperoleh MAX (lower bound) |
| 12 | **B** | Pada MIN node, pruning terjadi ketika nilai ≤ α (MAX tidak akan pilih path ini) |
| 13 | **B** | Dengan perfect ordering, Alpha-Beta mencapai O(b^(m/2)) |
| 14 | **E** | BFS tidak digunakan untuk move ordering; yang lain adalah teknik move ordering yang valid |
| 15 | **C** | Expectiminimax digunakan untuk game dengan elemen stokastik seperti dadu |
| 16 | **C** | Chance node menghitung expected value (E[V] = Σ P(r) × V(r)) |
| 17 | **B** | Chance nodes memerlukan semua nilai children untuk menghitung expected value, sehingga tidak bisa di-prune |
| 18 | **C** | MAX memilih nilai tertinggi dari children, yaitu max(5, 3, 7) = 7 |
| 19 | **B** | Material advantage (perbedaan nilai bidak) adalah feature paling penting dalam evaluasi catur |
| 20 | **B** | Deep Blue menggunakan Minimax dengan Alpha-Beta Pruning dan fungsi evaluasi yang sophisticated |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Perbedaan Pencarian Adversarial vs Single-Agent:**

| Aspek | Single-Agent (A*) | Adversarial (Minimax) |
|-------|-------------------|----------------------|
| **Agen** | Tunggal | Dua atau lebih (kompetitif) |
| **Kontrol** | Penuh atas semua aksi | Bergantian dengan lawan |
| **Tujuan** | Mencapai goal state | Mengalahkan lawan |
| **Prediksi** | State berikutnya pasti | Tergantung respons lawan |
| **Path** | Mencari path optimal | Mencari strategi optimal |

---

#### Jawaban Soal 2 ⭐

**Zero-Sum Game:**
Game dimana total keuntungan dan kerugian semua pemain selalu berjumlah nol. Keuntungan satu pemain adalah kerugian pemain lainnya.

$$U_{MAX}(s) + U_{MIN}(s) = 0$$

**Contoh 1: Catur**
- Menang (+1), Draw (0), Kalah (-1)
- Jika White menang (+1), Black kalah (-1): Total = 0 ✓

**Contoh 2: Tic-Tac-Toe**
- X menang (+1): O kalah (-1): Total = 0 ✓
- Draw: keduanya 0: Total = 0 ✓

---

#### Jawaban Soal 3 ⭐

**Empat Karakteristik Game untuk Minimax Standar:**

1. **Two-player**: Dua pemain yang bergantian bergerak

2. **Zero-sum**: Keuntungan satu pemain = kerugian lainnya (U₁ + U₂ = 0)

3. **Perfect Information**: Semua pemain dapat melihat seluruh state game (tidak ada informasi tersembunyi)

4. **Deterministic**: Tidak ada elemen keacakan; state berikutnya sepenuhnya ditentukan oleh state saat ini dan aksi yang dipilih

---

#### Jawaban Soal 4 ⭐

**Komponen Game Tree:**

| Komponen | Deskripsi |
|----------|-----------|
| **Root Node** | State awal permainan |
| **MAX Nodes** | Node dimana MAX (kita) memilih langkah; memaksimalkan nilai |
| **MIN Nodes** | Node dimana MIN (lawan) memilih langkah; meminimalkan nilai |
| **Terminal Nodes** | State akhir dengan nilai utility yang sudah ditentukan |
| **Edges** | Merepresentasikan aksi/langkah yang mungkin |
| **Branching Factor (b)** | Jumlah rata-rata langkah legal per state |
| **Depth (m)** | Kedalaman maksimum dari root ke terminal |

---

#### Jawaban Soal 5 ⭐⭐

**Game Tree Nim (4 batang, ambil 1 atau 2, yang mengambil terakhir kalah):**

```
Level 0 (MAX):        [4]
                    /     \
                 -1        -2
                /            \
Level 1 (MIN):  [3]          [2]
              /   \         /   \
           -1     -2     -1     -2
           /        \     |       \
Level 2 (MAX): [2]    [1] [1]     [0]
             /  \      |   |     MIN kalah
          -1   -2    -1  -1      (+1)
          /      \    |    |
Level 3 (MIN): [1]  [0] [0]  [0]
              |   MAX   MAX  MAX
             -1  kalah kalah kalah
              |  (-1)  (-1)  (-1)
Level 4 (MAX): [0]
            MAX kalah
              (-1)
```

**Analisis Minimax (dari bawah ke atas):**

- Level 4: [0] dicapai MAX → MAX kalah → utility = -1
- Level 3: 
  - [1] → MIN ambil 1 → [0] → MAX kalah → utility = -1
  - [0] dicapai MIN → MIN kalah → utility = +1
- Level 2:
  - [2]: MIN pilih min(-1, +1) = -1 (ambil 1)
  - [1]: MIN pilih -1 (ambil 1)
- Level 1:
  - [3]: MAX pilih max(-1, +1) = +1 (ambil 2 → [1])
  - [2]: MAX pilih max(-1, +1) = +1 (ambil 2 → [0])
- Level 0:
  - [4]: MIN pilih min(+1, +1) = +1

**Strategi Optimal:**
- Dari posisi 4 batang, MAX (yang bergerak pertama) akan **kalah** jika lawan bermain optimal
- Nilai Minimax root = -1 (dari perspektif MAX sebagai first player)

---

#### Jawaban Soal 6 ⭐⭐

**Perhitungan Minimax:**

```
           A (MAX)
         /    \
        B      C (MIN)
       /\     /|\
      4  6   3 5 2
```

**Step 1: Hitung nilai MIN nodes**
- Node B (MIN): min(4, 6) = **4**
- Node C (MIN): min(3, 5, 2) = **2**

**Step 2: Hitung nilai MAX node (root)**
- Node A (MAX): max(4, 2) = **4**

**Hasil:**

| Node | Tipe | Nilai Minimax |
|------|------|---------------|
| A | MAX | **4** |
| B | MIN | 4 |
| C | MIN | 2 |

**Aksi optimal:** MAX memilih path ke B (nilai 4)

---

#### Jawaban Soal 7 ⭐⭐

**Penjelasan Kompleksitas O(b^m):**

Minimax menggunakan depth-first search yang mengeksplorasi seluruh game tree:
- Pada setiap level, ada b children untuk setiap node
- Tree memiliki kedalaman m
- Total node = 1 + b + b² + ... + b^m ≈ O(b^m)

**Implikasi untuk Catur:**
- Branching factor b ≈ 35
- Kedalaman typical game m ≈ 80-100

Jumlah node = 35^80 ≈ 10^123 nodes

Ini **jauh melebihi** jumlah atom di alam semesta (~10^80)!

**Solusi:**
1. Depth cutoff dengan fungsi evaluasi
2. Alpha-Beta Pruning
3. Transposition tables
4. Opening book dan endgame databases

---

#### Jawaban Soal 8 ⭐⭐

**Fungsi Evaluasi:**
Fungsi yang memberikan estimasi nilai state tanpa perlu mengeksplorasi hingga terminal state. Menggantikan utility function untuk non-terminal states.

**Empat Properti Fungsi Evaluasi yang Baik:**

1. **Konsisten dengan Utility**: Harus setuju dengan utility untuk terminal states
   - Jika Eval(win) = +∞ dan Eval(lose) = -∞

2. **Cepat Dihitung**: Tidak boleh terlalu kompleks karena akan dipanggil ribuan kali

3. **Reflektif terhadap Peluang Menang**: Nilai tinggi harus berkorelasi dengan probabilitas kemenangan yang tinggi

4. **Linear Combination**: Biasanya berupa weighted sum dari features
   - Eval(s) = w₁f₁(s) + w₂f₂(s) + ... + wₙfₙ(s)

---

#### Jawaban Soal 9 ⭐⭐

**Fungsi Evaluasi untuk Tic-Tac-Toe:**

```python
def evaluate(board, player):
    score = 0
    opponent = 'O' if player == 'X' else 'X'
    
    # Semua baris, kolom, diagonal (8 lines)
    lines = [
        [0,1,2], [3,4,5], [6,7,8],  # Baris
        [0,3,6], [1,4,7], [2,5,8],  # Kolom
        [0,4,8], [2,4,6]            # Diagonal
    ]
    
    for line in lines:
        player_count = count(board, line, player)
        opponent_count = count(board, line, opponent)
        empty_count = count(board, line, ' ')
        
        # Feature 1: Kemenangan (bobot: 100)
        if player_count == 3:
            score += 100
        
        # Feature 2: Ancaman (2 berurutan + 1 kosong, bobot: 10)
        if player_count == 2 and empty_count == 1:
            score += 10
        
        # Feature 3: Potensi (1 + 2 kosong, bobot: 1)
        if player_count == 1 and empty_count == 2:
            score += 1
        
        # Feature 4: Blok ancaman lawan (bobot: -10)
        if opponent_count == 2 and empty_count == 1:
            score -= 10
        
        # Feature 5: Kekalahan (bobot: -100)
        if opponent_count == 3:
            score -= 100
    
    # Feature 6: Kontrol pusat (bobot: 3)
    if board[4] == player:
        score += 3
    
    return score
```

**Features dan Bobot:**

| Feature | Bobot | Alasan |
|---------|-------|--------|
| Kemenangan | +100 | Tujuan utama |
| Ancaman (2+1) | +10 | Hampir menang |
| Potensi (1+2) | +1 | Peluang berkembang |
| Blok ancaman | -10 | Mencegah kekalahan |
| Kekalahan | -100 | Hindari |
| Kontrol pusat | +3 | Fleksibilitas tinggi |

---

#### Jawaban Soal 10 ⭐⭐

**Konsep Alpha dan Beta:**

| Parameter | Definisi | Inisialisasi |
|-----------|----------|--------------|
| **α (Alpha)** | Nilai minimum yang dijamin MAX dapat peroleh | -∞ |
| **β (Beta)** | Nilai maksimum yang dijamin MIN tidak akan terlampaui | +∞ |

**Kondisi Pruning:**

**Pada MAX node:**
- Jika nilai saat ini ≥ β
- **Prune!** (MIN tidak akan memilih path ini karena sudah punya pilihan lebih baik)

**Pada MIN node:**
- Jika nilai saat ini ≤ α
- **Prune!** (MAX tidak akan memilih path ini karena sudah punya pilihan lebih baik)

**Aturan Update:**
- Di MAX node: α = max(α, nilai_child)
- Di MIN node: β = min(β, nilai_child)

---

#### Jawaban Soal 11 ⭐⭐⭐

**Alpha-Beta Pruning pada Game Tree:**

```
              A (MAX)
           /    |    \
          B     C     D (MIN)
         /\    /\    /\
        8  5  6  2  1  9
```

**Langkah-langkah:**

**Inisialisasi:** α = -∞, β = +∞

**Step 1: Evaluasi B**
- B adalah MIN node dengan α = -∞, β = +∞
- Cek child 8: current_min = 8, β = min(+∞, 8) = 8
- Cek child 5: current_min = min(8, 5) = 5, β = min(8, 5) = 5
- **Nilai B = 5**

**Step 2: Update α di A**
- α = max(-∞, 5) = **5**

**Step 3: Evaluasi C**
- C adalah MIN node dengan α = 5, β = +∞
- Cek child 6: current_min = 6, β = min(+∞, 6) = 6
- Cek child 2: current_min = min(6, 2) = 2
- **2 ≤ α (5)?** Ya! Tapi sudah selesai evaluasi semua children.
- **Nilai C = 2** (tidak dipilih karena 2 < 5)

**Step 4: Evaluasi D**
- D adalah MIN node dengan α = 5, β = +∞
- Cek child 1: current_min = 1
- **1 ≤ α (5)?** Ya!
- **PRUNE child 9!** ✂️
- **Nilai D = 1**

**Step 5: Hasil di A**
- A = max(5, 2, 1) = **5**

**Ringkasan:**

| Node | Nilai | α | β | Pruning |
|------|-------|---|---|---------|
| B | 5 | 5 | 5 | Tidak |
| C | 2 | 5 | 2 | Tidak (sudah selesai) |
| D | 1 | 5 | 1 | **Child 9 di-prune** |
| A | **5** | 5 | - | - |

**Node yang di-prune:** Child dengan nilai 9 dari node D

---

#### Jawaban Soal 12 ⭐⭐⭐

**Iterative Deepening untuk Alpha-Beta:**

**Konsep:**
Lakukan pencarian dengan kedalaman 1, 2, 3, ... secara berurutan. Gunakan hasil dari kedalaman sebelumnya untuk mengurutkan langkah pada kedalaman berikutnya.

**Cara Meningkatkan Efisiensi:**

1. **Better Move Ordering**: Langkah terbaik dari depth d-1 kemungkinan besar juga terbaik untuk depth d. Ini meningkatkan pruning.

2. **Anytime Behavior**: Selalu punya jawaban terbaik saat waktu habis.

```python
def iterative_deepening_ab(game, max_time):
    best_move = None
    for depth in range(1, MAX_DEPTH):
        if time_expired(max_time):
            break
        # Urutkan langkah berdasarkan hasil depth sebelumnya
        sorted_moves = order_by_previous_search(game, best_move)
        best_move = alpha_beta_search(game, depth, sorted_moves)
    return best_move
```

**Mengapa Overhead Tidak Signifikan:**

Waktu untuk kedalaman 1 sampai d-1:
$$T_{1..d-1} = 1 + b + b^2 + ... + b^{d-1} = \frac{b^d - 1}{b - 1}$$

Waktu untuk kedalaman d:
$$T_d = b^d$$

Rasio overhead:
$$\frac{T_{1..d-1}}{T_d} = \frac{b^d - 1}{(b-1) \cdot b^d} \approx \frac{1}{b-1}$$

Untuk b = 35 (catur): overhead ≈ 1/34 ≈ 3%

**Kesimpulan:** Overhead iterative deepening hanya sekitar 3% untuk catur, tapi benefit dari better ordering jauh lebih besar!

---

#### Jawaban Soal 13 ⭐⭐⭐

**Perbandingan Minimax vs Alpha-Beta untuk Catur (b=35, m=6):**

**Minimax murni:**
$$N_{minimax} = b^m = 35^6 = 1,838,265,625 \approx 1.84 \times 10^9 \text{ nodes}$$

**Alpha-Beta dengan perfect ordering:**
$$N_{alpha-beta} = b^{m/2} = 35^3 = 42,875 \text{ nodes}$$

**Alpha-Beta dengan random ordering (rata-rata):**
$$N_{random} = b^{3m/4} = 35^{4.5} \approx 2,251,875 \text{ nodes}$$

**Perbandingan:**

| Algoritma | Nodes | Waktu (1μs/node) |
|-----------|-------|------------------|
| Minimax | 1.84 miliar | ~31 menit |
| Alpha-Beta (random) | 2.25 juta | ~2.3 detik |
| Alpha-Beta (optimal) | 42,875 | ~0.04 detik |

**Pengurangan:**
- Random ordering: 99.88% lebih sedikit dari Minimax
- Perfect ordering: 99.998% lebih sedikit dari Minimax

---

#### Jawaban Soal 14 ⭐⭐⭐

**Algoritma Expectiminimax:**

Variasi Minimax untuk game dengan elemen stokastik. Menambahkan "chance nodes" yang menghitung expected value.

$$EXPECTIMINIMAX(n) = \begin{cases}
Utility(n) & \text{jika terminal} \\
\max_a EXPECTIMINIMAX(Result(n,a)) & \text{jika MAX} \\
\min_a EXPECTIMINIMAX(Result(n,a)) & \text{jika MIN} \\
\sum_r P(r) \cdot EXPECTIMINIMAX(Result(n,r)) & \text{jika CHANCE}
\end{cases}$$

**Mengapa Diperlukan untuk Backgammon:**
- Backgammon menggunakan dadu
- Hasil langkah tidak deterministik
- Perlu memperhitungkan semua kemungkinan hasil dadu dan probabilitasnya

**Contoh Perhitungan:**

Skenario: MAX melempar dadu (1-6) sebelum bergerak
- Jika hasil ≤ 3 (P=0.5): pilihan nilai {5, 3}
- Jika hasil > 3 (P=0.5): pilihan nilai {8, 2}

```
         MAX
           |
       CHANCE
       /     \
    P=0.5   P=0.5
     /         \
   MAX         MAX
   / \         / \
  5   3       8   2
```

**Perhitungan:**
1. MAX (kiri): max(5, 3) = 5
2. MAX (kanan): max(8, 2) = 8
3. CHANCE: E[V] = 0.5 × 5 + 0.5 × 8 = 2.5 + 4 = **6.5**

---

#### Jawaban Soal 15 ⭐⭐⭐

**Pencarian Adversarial dalam Cyber Security:**

**Formulasi Game:**

| Komponen | Deskripsi |
|----------|-----------|
| **Players** | Defender (MAX), Attacker (MIN dari perspektif Defender) |
| **States** | Konfigurasi keamanan sistem |
| **Actions (Defender)** | Patching, firewall rules, monitoring, resource allocation |
| **Actions (Attacker)** | Exploit selection, target choice, attack timing |
| **Utility** | Defender: minimize damage; Attacker: maximize damage |

**Model sebagai Zero-Sum Game:**

$$U_{Defender}(outcome) = -U_{Attacker}(outcome)$$

**Contoh Payoff Matrix:**

| Defender \ Attacker | Exploit A | Exploit B | Exploit C |
|---------------------|-----------|-----------|-----------|
| Patch A | 0 | -50 | -30 |
| Patch B | -80 | 0 | -30 |
| Patch C | -80 | -50 | 0 |

**Minimax Analysis:**
- Defender pilih Patch A: Attacker pilih B (damage -50)
- Defender pilih Patch B: Attacker pilih A (damage -80)
- Defender pilih Patch C: Attacker pilih B (damage -50)

**Optimal:** Patch A atau C (minimax value = -50)

**Aplikasi:**
1. **Predictive Defense**: Anticipate rational attacker moves
2. **Resource Allocation**: Optimal patching priorities
3. **Threat Modeling**: Identify most likely attack vectors
4. **Risk Assessment**: Quantify worst-case scenarios

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Pengambilan Keputusan Taktis Militer

**1a. Formulasi sebagai Zero-Sum Game (10 poin)**

**Players:**
- **MAX = Defender (TNI AD)**: Berusaha memaksimalkan keberhasilan pertahanan
- **MIN = Attacker (Musuh)**: Berusaha meminimalkan keberhasilan pertahanan (= memaksimalkan keberhasilan serangan)

**Zero-Sum Property:**
$$U_{Defender}(outcome) = -U_{Attacker}(outcome)$$

**Interpretasi Nilai Payoff:**
- **Positif (+)**: Defender berhasil, serangan digagalkan
- **Negatif (-)**: Attacker berhasil, pertahanan jebol
- **Magnitude**: Tingkat keberhasilan/kegagalan

Contoh: D1 vs A1 = +8 berarti pertahanan terpusat sangat efektif melawan serangan frontal.

---

**1b. Game Tree dan Minimax (15 poin)**

Asumsi: Defender bergerak dulu, Attacker melihat dan merespons.

```
                    ROOT (Defender/MAX)
                   /        |        \
                 D1        D2        D3
                 |          |          |
              [Attacker]  [Attacker]  [Attacker]
              /  |  \     /  |  \     /  |  \
            A1  A2  A3   A1  A2  A3   A1  A2  A3
            +8  -4  -2   +2  +6  -3   +4  +3  +5
```

**Langkah Minimax:**

**Step 1: Hitung nilai MIN nodes (Attacker response)**
- D1 → Attacker pilih: min(+8, -4, -2) = **-4** (pilih A2)
- D2 → Attacker pilih: min(+2, +6, -3) = **-3** (pilih A3)
- D3 → Attacker pilih: min(+4, +3, +5) = **+3** (pilih A2)

**Step 2: Hitung nilai MAX node (Defender choice)**
- ROOT = max(-4, -3, +3) = **+3**

**Strategi Optimal:**
- **Defender optimal: D3 (Pertahanan Berlapis)**
- **Attacker response: A2 (Serangan Mengapit)**
- **Nilai game: +3** (Defender advantage)

---

**1c. Analisis Simultaneous Move (10 poin)**

Jika kedua pihak memilih secara simultan (tidak melihat pilihan lawan), ini menjadi **normal-form game** bukan extensive-form.

**Analisis Maximin (Defender) dan Minimax (Attacker):**

**Defender Maximin:**
- D1: min row = min(+8, -4, -2) = -4
- D2: min row = min(+2, +6, -3) = -3
- D3: min row = min(+4, +3, +5) = +3
- **Maximin = max(-4, -3, +3) = +3 → D3**

**Attacker Minimax:**
- A1: max col = max(+8, +2, +4) = +8
- A2: max col = max(-4, +6, +3) = +6
- A3: max col = max(-2, -3, +5) = +5
- **Minimax = min(+8, +6, +5) = +5 → A3**

**Dalam simultaneous game:**
- Defender: D3 (menjamin minimal +3)
- Attacker: A3 (menjamin maksimal -5 untuk Defender)

**Perbedaan:**
- Sequential (Defender first): Attacker dapat merespons optimal → D3-A2 (+3)
- Simultaneous: Kedua belah pihak memilih berdasarkan worst-case → D3-A3 (+5)

Defender **lebih diuntungkan** dalam simultaneous game (+5 vs +3)!

---

**1d. Expectiminimax dengan Ketidakpastian Cuaca (15 poin)**

**Modifikasi:**
- Cuaca buruk (P=0.4): Efektivitas A3 berkurang 50%
- Cuaca baik (P=0.6): A3 normal

**Payoff A3 yang dimodifikasi:**

| Kondisi | Probabilitas | D1 vs A3 | D2 vs A3 | D3 vs A3 |
|---------|--------------|----------|----------|----------|
| Cuaca Baik | 0.6 | -2 | -3 | +5 |
| Cuaca Buruk | 0.4 | -1 | -1.5 | +7.5 |

**Expected value A3:**
- D1 vs A3: 0.6×(-2) + 0.4×(-1) = -1.2 - 0.4 = **-1.6**
- D2 vs A3: 0.6×(-3) + 0.4×(-1.5) = -1.8 - 0.6 = **-2.4**
- D3 vs A3: 0.6×(+5) + 0.4×(+7.5) = 3 + 3 = **+6**

**Matriks Payoff Baru:**

| Defender \ Attacker | A1 | A2 | A3 (Expected) |
|---------------------|-----|-----|---------------|
| D1 | +8 | -4 | -1.6 |
| D2 | +2 | +6 | -2.4 |
| D3 | +4 | +3 | +6 |

**Minimax baru:**
- D1 → min(+8, -4, -1.6) = -4
- D2 → min(+2, +6, -2.4) = -2.4
- D3 → min(+4, +3, +6) = **+3**

**Hasil:** D3 tetap optimal dengan nilai +3, tetapi now A3 menjadi kurang menarik bagi Attacker.

---

**1e. Rekomendasi untuk Komandan TNI AD (10 poin)**

**Rekomendasi: Strategi D3 (Pertahanan Berlapis dengan Cadangan)**

**Reasoning:**

1. **Robustness**: D3 memberikan nilai positif terhadap SEMUA strategi serangan (+4, +3, +5), tidak seperti D1 dan D2 yang memiliki nilai negatif.

2. **Worst-case optimal**: Nilai terburuk D3 adalah +3 (vs D1: -4, D2: -3). Ini adalah strategi **maximin**.

3. **Flexibility**: Pertahanan berlapis dapat beradaptasi terhadap berbagai jenis serangan.

4. **Weather resilience**: Dengan ketidakpastian cuaca, D3 semakin menguntungkan karena A3 menjadi kurang efektif.

5. **Deception**: Dengan cadangan tersembunyi, attacker tidak yakin dengan kekuatan pertahanan sebenarnya.

**Peringatan:**
- D3 memerlukan lebih banyak resources (3 lapis pertahanan)
- Koordinasi antar lapis harus baik
- Komunikasi internal menjadi kritis

---

#### Studi Kasus 2: AI untuk Sistem Pertahanan Cyber Command and Control

**2a. Matriks Payoff Lengkap (15 poin)**

**Defender: C(5,2) = 10 kombinasi**
**Attacker: 5 pilihan**

Kerugian (dari perspektif Defender):
- S1: -100, S2: -80, S3: -60, S4: -40, S5: -30

Jika sistem diperkuat dan diserang: 0 (aman)

| Defender \ Attacker | Attack S1 | Attack S2 | Attack S3 | Attack S4 | Attack S5 |
|---------------------|-----------|-----------|-----------|-----------|-----------|
| {S1, S2} | 0 | 0 | -60 | -40 | -30 |
| {S1, S3} | 0 | -80 | 0 | -40 | -30 |
| {S1, S4} | 0 | -80 | -60 | 0 | -30 |
| {S1, S5} | 0 | -80 | -60 | -40 | 0 |
| {S2, S3} | -100 | 0 | 0 | -40 | -30 |
| {S2, S4} | -100 | 0 | -60 | 0 | -30 |
| {S2, S5} | -100 | 0 | -60 | -40 | 0 |
| {S3, S4} | -100 | -80 | 0 | 0 | -30 |
| {S3, S5} | -100 | -80 | 0 | -40 | 0 |
| {S4, S5} | -100 | -80 | -60 | 0 | 0 |

---

**2b. Algoritma Minimax (20 poin)**

**Step 1: Hitung nilai MIN (Attacker optimal response) untuk setiap Defender strategy**

| Defender | Attacker Optimal | Kerugian |
|----------|------------------|----------|
| {S1, S2} | S3 | -60 |
| {S1, S3} | S2 | -80 |
| {S1, S4} | S2 | -80 |
| {S1, S5} | S2 | -80 |
| {S2, S3} | S1 | -100 |
| {S2, S4} | S1 | -100 |
| {S2, S5} | S1 | -100 |
| {S3, S4} | S1 | -100 |
| {S3, S5} | S1 | -100 |
| {S4, S5} | S1 | -100 |

**Step 2: Hitung nilai MAX (Defender optimal)**

$$\text{Defender Optimal} = \max(-60, -80, -80, -80, -100, ...) = -60$$

**Strategi Optimal:**
- **Defender: {S1, S2}** (lindungi sistem dengan kerugian tertinggi)
- **Attacker: S3** (serang sistem tidak terlindungi dengan kerugian tertinggi)
- **Nilai game: -60**

**Game Tree (Simplified):**

```
                     ROOT (Defender/MAX)
                    /         |        \
               {S1,S2}    {S1,S3}   ... {S4,S5}
                  |           |           |
              [Attacker]  [Attacker]  [Attacker]
              MIN=-60     MIN=-80     MIN=-100
```

---

**2c. Fungsi Evaluasi (15 poin)**

**Rancangan Fungsi Evaluasi:**

```python
def evaluate_defense_config(defended_systems, all_systems):
    """
    Evaluasi konfigurasi pertahanan tanpa enumerasi semua serangan
    """
    score = 0
    
    # Feature 1: Total nilai terlindungi (bobot: 0.4)
    protected_value = sum(s.value for s in defended_systems)
    score += 0.4 * protected_value
    
    # Feature 2: Nilai exposed tertinggi (bobot: -0.3)
    exposed = [s for s in all_systems if s not in defended_systems]
    max_exposed = max(s.value for s in exposed) if exposed else 0
    score -= 0.3 * max_exposed
    
    # Feature 3: Coverage ratio (bobot: 0.2)
    total_value = sum(s.value for s in all_systems)
    coverage = protected_value / total_value
    score += 0.2 * coverage * 100
    
    # Feature 4: Criticality balance (bobot: 0.1)
    # Bonus jika melindungi sistem paling kritis
    if all_systems[0] in defended_systems:  # S1
        score += 10
    if all_systems[1] in defended_systems:  # S2
        score += 8
    
    return score
```

**Features:**

| Feature | Bobot | Rationale |
|---------|-------|-----------|
| Nilai terlindungi | 0.4 | Maksimalkan nilai yang dilindungi |
| Max exposed | -0.3 | Minimalkan kerugian worst-case |
| Coverage ratio | 0.2 | Persentase nilai terlindungi |
| Criticality bonus | 0.1 | Prioritaskan sistem kritis |

**Contoh perhitungan untuk {S1, S2}:**
- Protected value = 100 + 80 = 180 → 0.4 × 180 = 72
- Max exposed = 60 (S3) → -0.3 × 60 = -18
- Coverage = 180/310 = 0.58 → 0.2 × 58 = 11.6
- Criticality bonus = 10 + 8 = 18

**Total = 72 - 18 + 11.6 + 18 = 83.6**

---

**2d. Alpha-Beta Pruning Application (10 poin)**

**Setup:**
- Defender: 10 pilihan
- Attacker: 5 pilihan per Defender choice
- Total nodes tanpa pruning: 10 × 5 = 50 evaluations

**Dengan Alpha-Beta:**

```
Defender pilih {S1,S2}:
  α = -∞
  Attacker choices: S3→-60, (update α=-60), S4→-40, S5→-30
  Best for Defender so far: -60
  α = -60

Defender pilih {S1,S3}:
  Attacker pilih S2→-80
  -80 ≤ α (-60)? No, continue
  ... evaluasi lainnya
  MIN = -80 (tidak dipilih)

Defender pilih {S2,S3}:
  Attacker pilih S1→-100
  -100 < α (-60)? Yes, tapi kita di MIN node, perlu lihat semua
  Namun setelah S1 memberikan -100, 
  Defender tidak akan memilih ini (karena -100 < -60)
  
  Untuk strategi Defender berikutnya yang dimulai dengan 
  Attacker pilih S1 → -100:
  Jika -100 sudah ditemukan, kita bisa PRUNE!
```

**Pengurangan Komputasi:**

Dengan ordering yang baik (mulai dari {S1, S2}):
- α = -60 setelah evaluasi pertama
- Semua strategi yang tidak melindungi S1 akan memberikan -100 saat Attacker pilih S1
- Dapat langsung prune setelah evaluasi S1

**Estimasi pengurangan:** 
- Tanpa pruning: 50 evaluations
- Dengan pruning: ~25-30 evaluations (40-50% reduction)

Untuk game lebih kompleks, pengurangan bisa mencapai O(√N).

---

**2e. Menangani Ketidakpastian Attacker (10 poin)**

**Modifikasi untuk Attacker Non-Rasional:**

**1. Probabilistic Attacker Model:**
```python
def attacker_choice_probability(system, attack_history):
    """
    Model probabilitas attacker memilih target
    """
    # Base probability proporsional dengan nilai
    base_prob = system.value / total_value
    
    # Adjust berdasarkan historical patterns
    if system in frequently_attacked:
        prob *= 1.2
    
    # Adjust untuk "random" behavior
    noise = random.uniform(0.8, 1.2)
    
    return base_prob * noise
```

**2. Expectiminimax dengan Uncertainty:**
Alih-alih MIN node, gunakan CHANCE node:

$$E[V] = \sum_{attack} P(attack) \times damage(attack)$$

**3. Robust Optimization:**
Optimalkan untuk distribusi serangan yang tidak pasti:

$$\text{Minimize} \quad \max_{P \in \mathcal{P}} \sum_a P(a) \times loss(defense, a)$$

dimana $\mathcal{P}$ adalah set distribusi yang mungkin.

**4. Bounded Rationality Model:**
Asumsikan attacker "cukup rasional" dengan probability ε untuk error:

- P(optimal attack) = 1 - ε
- P(random attack) = ε / (n-1) untuk attack lain

**5. Learning Component:**
```python
class AdaptiveDefense:
    def __init__(self):
        self.attack_history = []
        self.attacker_model = UniformDistribution()
    
    def update_model(self, observed_attack):
        self.attack_history.append(observed_attack)
        self.attacker_model = fit_distribution(self.attack_history)
    
    def choose_defense(self):
        # Use current attacker model for expectiminimax
        return expectiminimax(self.attacker_model)
```

**Kesimpulan:**
Model harus:
1. Maintain distribution over attacker strategies
2. Update berdasarkan observasi
3. Hedge against uncertainty (robust optimization)
4. Balance between minimax (pessimistic) dan expected value (realistic)

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
- Studi Kasus 1: 60 poin
- Studi Kasus 2: 70 poin
- Total: 130 poin

### Total Keseluruhan: 285 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
