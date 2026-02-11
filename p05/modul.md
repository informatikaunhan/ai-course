# Modul 05: Pencarian Adversarial - Game Playing

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 05  
**Topik:** Pencarian Adversarial - Game Playing  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Memformulasikan permainan (game) sebagai problem pencarian adversarial
2. Menjelaskan karakteristik game: deterministic, two-player, zero-sum, perfect information
3. Membangun dan menganalisis game tree beserta terminal states
4. Mengimplementasikan algoritma Minimax untuk pengambilan keputusan dalam game
5. Menganalisis kompleksitas algoritma Minimax O(b^m)
6. Menerapkan teknik Alpha-Beta Pruning untuk optimasi Minimax
7. Merancang fungsi evaluasi untuk non-terminal states
8. Menjelaskan konsep dasar Expectiminimax untuk game stokastik

---

## 1. Pendahuluan Pencarian Adversarial

### 1.1 Definisi Pencarian Adversarial

> **Pencarian Adversarial (Adversarial Search)** adalah teknik pencarian yang digunakan dalam situasi kompetitif di mana terdapat agen-agen dengan tujuan yang saling bertentangan. Setiap agen berusaha memaksimalkan keuntungannya sambil meminimalkan keuntungan lawan.

Berbeda dengan pencarian yang telah dipelajari pada Pertemuan 2-4 (Uninformed dan Informed Search), pencarian adversarial menghadapi tantangan unik:

| Aspek | Pencarian Biasa | Pencarian Adversarial |
|-------|-----------------|----------------------|
| **Agen** | Tunggal | Dua atau lebih (kompetitif) |
| **Kontrol** | Penuh atas semua aksi | Bergantian dengan lawan |
| **Prediksi** | State berikutnya pasti | Tergantung respons lawan |
| **Tujuan** | Mencapai goal state | Mengalahkan lawan |

### 1.2 Aplikasi Pencarian Adversarial

Pencarian adversarial memiliki aplikasi luas, tidak hanya dalam permainan:

**Dalam Game:**
- Permainan papan (catur, go, checkers)
- Video games dengan AI lawan
- Card games (poker, bridge)

**Dalam Konteks Pertahanan:**
- Simulasi strategi militer
- Cyber warfare (attack-defense scenarios)
- Alokasi sumber daya dalam konflik
- War gaming dan perencanaan operasi

#### Solved Problem 1 ⭐

**Soal:** Jelaskan mengapa algoritma pencarian seperti A* (Pertemuan 3) tidak langsung dapat diterapkan untuk permainan catur!

**Penyelesaian:**

*Step 1:* Identifikasi karakteristik A*
- A* mengasumsikan kontrol penuh atas semua aksi
- Path cost dapat dihitung secara deterministik
- Tidak ada agen lain yang mempengaruhi hasil

*Step 2:* Identifikasi perbedaan pada catur
- Pemain tidak memiliki kontrol penuh (giliran bergantian)
- Lawan akan memilih langkah yang menguntungkan baginya
- Tidak bisa mengasumsikan "optimal path" karena lawan akan menghalangi

*Step 3:* Kesimpulan

**Jawaban:** A* tidak dapat langsung diterapkan untuk catur karena:
1. **Kontrol bergantian**: Pemain tidak bisa memilih semua langkah dalam path menuju kemenangan
2. **Lawan rasional**: Lawan akan memilih langkah terbaik untuk dirinya, bukan langkah yang kita inginkan
3. **Adversarial nature**: Diperlukan algoritma yang mempertimbangkan respons optimal lawan

---

## 2. Karakteristik Game

### 2.1 Klasifikasi Game dalam AI

Game dapat diklasifikasikan berdasarkan beberapa dimensi:

![Klasifikasi Game dalam AI](images/p05-01-game-classification.png)

*Gambar 5.1: Klasifikasi game berdasarkan karakteristiknya*

#### 2.1.1 Deterministic vs Stochastic

> **Game Deterministik** adalah game di mana state berikutnya sepenuhnya ditentukan oleh state saat ini dan aksi yang dipilih, tanpa elemen keacakan.

> **Game Stokastik** adalah game yang melibatkan elemen keacakan seperti dadu, kartu yang diacak, atau probabilitas lainnya.

| Karakteristik | Deterministik | Stokastik |
|---------------|---------------|-----------|
| **Keacakan** | Tidak ada | Ada (dadu, kartu) |
| **Prediksi** | Pasti | Probabilistik |
| **Contoh** | Catur, Go, Checkers | Backgammon, Poker |
| **Algoritma** | Minimax | Expectiminimax |

#### 2.1.2 Perfect vs Imperfect Information

> **Perfect Information** adalah kondisi di mana semua pemain dapat melihat seluruh state game pada setiap saat.

> **Imperfect Information** adalah kondisi di mana sebagian informasi tersembunyi dari satu atau lebih pemain.

| Karakteristik | Perfect Information | Imperfect Information |
|---------------|--------------------|-----------------------|
| **Visibilitas** | Semua state terlihat | Sebagian tersembunyi |
| **Contoh** | Catur, Go | Poker, Bridge |
| **Kompleksitas** | Lebih sederhana | Lebih kompleks |

#### Solved Problem 2 ⭐

**Soal:** Klasifikasikan game-game berikut berdasarkan karakteristiknya: (a) Tic-Tac-Toe, (b) Backgammon, (c) Poker Texas Hold'em, (d) Connect Four!

**Penyelesaian:**

*Step 1:* Analisis setiap game

**(a) Tic-Tac-Toe:**
- Tidak ada elemen acak → Deterministik
- Semua posisi terlihat → Perfect Information
- **Deterministik, Perfect Information**

**(b) Backgammon:**
- Menggunakan dadu → Stokastik
- Semua posisi bidak terlihat → Perfect Information
- **Stokastik, Perfect Information**

**(c) Poker Texas Hold'em:**
- Kartu diacak → Stokastik
- Kartu lawan tersembunyi → Imperfect Information
- **Stokastik, Imperfect Information**

**(d) Connect Four:**
- Tidak ada elemen acak → Deterministik
- Semua chip terlihat → Perfect Information
- **Deterministik, Perfect Information**

**Jawaban:**

| Game | Determinism | Information |
|------|-------------|-------------|
| Tic-Tac-Toe | Deterministik | Perfect |
| Backgammon | Stokastik | Perfect |
| Poker | Stokastik | Imperfect |
| Connect Four | Deterministik | Perfect |

---

### 2.2 Zero-Sum Game

> **Zero-Sum Game** adalah game di mana total keuntungan dan kerugian semua pemain selalu berjumlah nol. Keuntungan satu pemain adalah kerugian pemain lainnya.

Secara matematis, untuk two-player zero-sum game:
$$U_1(s) + U_2(s) = 0$$

atau equivalen:
$$U_1(s) = -U_2(s)$$

di mana $U_1$ dan $U_2$ adalah utility untuk pemain 1 dan 2 pada state $s$.

**Implikasi:**
- Jika MAX menang (+1), MIN kalah (-1)
- Memaksimalkan keuntungan = Meminimalkan keuntungan lawan
- Cukup satu nilai utility untuk merepresentasikan game

#### Solved Problem 3 ⭐

**Soal:** Dalam permainan catur, jika White (MAX) menang diberi nilai +1, draw 0, dan kalah -1, buktikan bahwa ini adalah zero-sum game!

**Penyelesaian:**

*Step 1:* Definisikan utility untuk kedua pemain

| Hasil | U(White) | U(Black) |
|-------|----------|----------|
| White menang | +1 | -1 |
| Draw | 0 | 0 |
| Black menang | -1 | +1 |

*Step 2:* Verifikasi zero-sum untuk setiap kasus

- White menang: $U_{White} + U_{Black} = (+1) + (-1) = 0$ ✓
- Draw: $U_{White} + U_{Black} = 0 + 0 = 0$ ✓
- Black menang: $U_{White} + U_{Black} = (-1) + (+1) = 0$ ✓

**Jawaban:** Catur adalah zero-sum game karena untuk setiap kemungkinan hasil, jumlah utility kedua pemain selalu nol. Ini berarti kemenangan satu pihak selalu berarti kekalahan pihak lain dengan magnitude yang sama.

---

### 2.3 Two-Player Game Formulation

Untuk modul ini, kita fokus pada game dengan karakteristik:
- **Two-player**: Dua pemain bergantian
- **Zero-sum**: Keuntungan satu = kerugian lainnya
- **Perfect information**: Semua state terlihat
- **Deterministic**: Tidak ada elemen acak

Formulasi formal:
- $S_0$: Initial state (posisi awal)
- $Player(s)$: Fungsi yang mengembalikan pemain yang bergiliran pada state $s$
- $Actions(s)$: Aksi legal pada state $s$
- $Result(s, a)$: Transition model - state hasil dari aksi $a$ pada state $s$
- $Terminal-Test(s)$: True jika game berakhir pada state $s$
- $Utility(s, p)$: Nilai akhir game untuk pemain $p$ pada terminal state $s$

#### Solved Problem 4 ⭐⭐

**Soal:** Formulasikan permainan Tic-Tac-Toe menggunakan notasi formal di atas!

**Penyelesaian:**

*Step 1:* Definisikan komponen formal

**Initial State ($S_0$):**
- Papan 3×3 kosong
- Giliran: X (MAX)

**Player(s):**
```
Player(s) = X jika jumlah X pada papan = jumlah O
Player(s) = O jika jumlah X pada papan = jumlah O + 1
```

**Actions(s):**
- Semua sel kosong pada papan s
- $Actions(s) = \{(i,j) | s[i][j] = empty, i,j \in \{0,1,2\}\}$

**Result(s, a):**
- Papan baru dengan simbol pemain saat ini di posisi a
- $Result(s, (i,j)) = s'$ dimana $s'[i][j] = Player(s)$

**Terminal-Test(s):**
```
Terminal(s) = True jika:
  - Ada 3 simbol sama dalam baris, kolom, atau diagonal, ATAU
  - Papan penuh (9 sel terisi)
```

**Utility(s, p):**
```
Utility(s, X) = +1 jika X menang (3 X sejajar)
Utility(s, X) = -1 jika O menang (3 O sejajar)
Utility(s, X) = 0  jika draw
Utility(s, O) = -Utility(s, X)  [zero-sum]
```

**Jawaban:** Formulasi di atas mendefinisikan Tic-Tac-Toe sebagai problem pencarian adversarial dengan state space ~9! = 362,880 kemungkinan konfigurasi papan (sebelum pruning).

---

## 3. Game Tree

### 3.1 Konsep Game Tree

> **Game Tree** adalah representasi graf dari semua kemungkinan permainan, dimulai dari posisi awal hingga semua kemungkinan hasil akhir. Setiap node merepresentasikan state game, dan setiap edge merepresentasikan langkah/aksi.

![Struktur Game Tree](images/p05-02-game-tree-structure.png)

*Gambar 5.2: Struktur game tree untuk permainan dua pemain*

**Komponen Game Tree:**

| Komponen | Deskripsi |
|----------|-----------|
| **Root Node** | State awal permainan |
| **MAX Nodes** | Node dimana MAX (kita) memilih langkah |
| **MIN Nodes** | Node dimana MIN (lawan) memilih langkah |
| **Terminal Nodes** | State akhir dengan utility value |
| **Branching Factor (b)** | Jumlah rata-rata langkah legal per state |
| **Depth (m)** | Kedalaman maksimum tree |

### 3.2 Terminal State dan Utility

> **Terminal State** adalah state dimana permainan berakhir, baik karena ada pemenang, draw, atau kondisi terminasi lainnya.

Pada terminal state, fungsi Utility memberikan nilai numerik:
- Kemenangan MAX: nilai positif (misal +1)
- Kemenangan MIN: nilai negatif (misal -1)
- Draw: nilai netral (misal 0)

#### Solved Problem 5 ⭐

**Soal:** Untuk Tic-Tac-Toe, hitung branching factor rata-rata dan kedalaman maksimum game tree!

**Penyelesaian:**

*Step 1:* Hitung branching factor

Langkah pertama: 9 pilihan
Langkah kedua: 8 pilihan
Langkah ketiga: 7 pilihan
...dan seterusnya

Rata-rata branching factor:
$$b_{avg} = \frac{9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1}{9} = \frac{45}{9} = 5$$

*Step 2:* Hitung kedalaman maksimum

- Game berakhir paling cepat pada langkah ke-5 (ada pemenang)
- Game berakhir paling lambat pada langkah ke-9 (papan penuh)
- **Kedalaman maksimum: m = 9**

*Step 3:* Estimasi ukuran game tree

$$|Tree| \approx b^m = 5^9 = 1,953,125$$

Namun dengan simetri dan pruning: ~255,168 unique games

**Jawaban:** Tic-Tac-Toe memiliki branching factor rata-rata ≈ 5 dan kedalaman maksimum 9, menghasilkan game tree dengan sekitar 255,168 unique games setelah mempertimbangkan terminasi dini.

---

### 3.3 Contoh Game Tree: Tic-Tac-Toe

![Contoh Game Tree Tic-Tac-Toe](images/p05-03-tictactoe-game-tree.png)

*Gambar 5.3: Sebagian game tree untuk Tic-Tac-Toe*

#### Solved Problem 6 ⭐⭐

**Soal:** Gambarkan game tree lengkap untuk "Nim Game" sederhana dengan 3 batang dimana setiap giliran pemain mengambil 1 atau 2 batang. Pemain yang mengambil batang terakhir kalah.

**Penyelesaian:**

*Step 1:* Definisikan game
- State: jumlah batang tersisa
- Initial state: 3 batang
- Actions: ambil 1 atau ambil 2
- Terminal: 0 batang (pemain yang mengambil terakhir kalah)
- MAX bergerak pertama

*Step 2:* Bangun game tree

```
Level 0 (MAX):     [3]
                  /   \
               -1      -2
              /          \
Level 1 (MIN):  [2]        [1]
              /   \          |
           -1     -2        -1
           /        \         \
Level 2 (MAX): [1]    [0]      [0]
              |     MIN wins  MIN wins
             -1      (+1)      (+1)
              |
Level 3 (MIN): [0]
            MAX wins
              (-1)
```

*Step 3:* Tentukan utility

- State [0] dicapai oleh MAX → MAX kalah → Utility = -1 (dari perspektif MAX)
- State [0] dicapai oleh MIN → MIN kalah → Utility = +1 (dari perspektif MAX)

**Jawaban:**

| Path | Hasil | Utility (MAX) |
|------|-------|---------------|
| 3→2→1→0 | MAX ambil terakhir, kalah | -1 |
| 3→2→0 | MIN ambil terakhir, kalah | +1 |
| 3→1→0 | MIN ambil terakhir, kalah | +1 |

Dengan strategi optimal, MAX akan kalah jika memulai dengan 3 batang (karena MIN selalu bisa memaksa MAX mengambil batang terakhir).

---

## 4. Algoritma Minimax

### 4.1 Konsep Dasar Minimax

> **Algoritma Minimax** adalah algoritma untuk menentukan langkah optimal dalam game two-player zero-sum dengan perfect information. Algoritma ini mengasumsikan bahwa kedua pemain bermain secara optimal.

**Prinsip Dasar:**
- **MAX** berusaha **memaksimalkan** nilai utility
- **MIN** berusaha **meminimalkan** nilai utility
- Nilai setiap node dihitung secara rekursif dari terminal nodes

![Konsep Algoritma Minimax](images/p05-04-minimax-concept.png)

*Gambar 5.4: Ilustrasi algoritma Minimax pada game tree*

### 4.2 Definisi Formal Minimax

Nilai Minimax untuk node $n$ didefinisikan sebagai:

$$MINIMAX(n) = \begin{cases}
Utility(n) & \text{jika } n \text{ adalah terminal} \\
\max_{a \in Actions(n)} MINIMAX(Result(n,a)) & \text{jika } Player(n) = MAX \\
\min_{a \in Actions(n)} MINIMAX(Result(n,a)) & \text{jika } Player(n) = MIN
\end{cases}$$

### 4.3 Pseudocode Minimax

```python
def minimax_decision(state):
    """Mengembalikan aksi terbaik untuk MAX pada state tertentu"""
    # Cari aksi yang menghasilkan nilai minimax tertinggi
    return argmax(actions(state), key=lambda a: min_value(result(state, a)))

def max_value(state):
    """Menghitung nilai minimax untuk node MAX"""
    if terminal_test(state):
        return utility(state)
    v = float('-inf')
    for action in actions(state):
        v = max(v, min_value(result(state, action)))
    return v

def min_value(state):
    """Menghitung nilai minimax untuk node MIN"""
    if terminal_test(state):
        return utility(state)
    v = float('+inf')
    for action in actions(state):
        v = min(v, max_value(result(state, action)))
    return v
```

#### Solved Problem 7 ⭐⭐

**Soal:** Hitung nilai Minimax untuk setiap node pada game tree berikut:

```
        A (MAX)
       /|\
      / | \
     B  C  D (MIN)
    /\  |  /\
   3  5 2 6  1
```

**Penyelesaian:**

*Step 1:* Identifikasi terminal nodes
- Terminal values: 3, 5, 2, 6, 1

*Step 2:* Hitung nilai MIN nodes (level 1)
- Node B (MIN): min(3, 5) = **3**
- Node C (MIN): **2** (single child)
- Node D (MIN): min(6, 1) = **1**

*Step 3:* Hitung nilai MAX node (root)
- Node A (MAX): max(3, 2, 1) = **3**

*Step 4:* Tentukan aksi optimal
- MAX akan memilih aksi menuju Node B

**Jawaban:**

| Node | Tipe | Nilai Minimax |
|------|------|---------------|
| A | MAX | 3 |
| B | MIN | 3 |
| C | MIN | 2 |
| D | MIN | 1 |

Aksi optimal untuk MAX adalah bergerak ke B, yang menjamin nilai minimal 3.

---

#### Solved Problem 8 ⭐⭐

**Soal:** Implementasikan algoritma Minimax dalam Python untuk game Tic-Tac-Toe!

**Penyelesaian:**

```python
import math

class TicTacToe:
    def __init__(self):
        self.board = [' ' for _ in range(9)]
        self.current_player = 'X'  # X adalah MAX
    
    def available_moves(self):
        return [i for i, spot in enumerate(self.board) if spot == ' ']
    
    def make_move(self, position, player):
        self.board[position] = player
    
    def undo_move(self, position):
        self.board[position] = ' '
    
    def check_winner(self):
        # Kombinasi kemenangan
        win_combinations = [
            [0, 1, 2], [3, 4, 5], [6, 7, 8],  # Baris
            [0, 3, 6], [1, 4, 7], [2, 5, 8],  # Kolom
            [0, 4, 8], [2, 4, 6]              # Diagonal
        ]
        for combo in win_combinations:
            if self.board[combo[0]] == self.board[combo[1]] == self.board[combo[2]] != ' ':
                return self.board[combo[0]]
        return None
    
    def is_terminal(self):
        return self.check_winner() is not None or len(self.available_moves()) == 0
    
    def utility(self):
        winner = self.check_winner()
        if winner == 'X':
            return 1   # MAX menang
        elif winner == 'O':
            return -1  # MIN menang
        else:
            return 0   # Draw

def minimax(game, is_maximizing):
    """
    Algoritma Minimax untuk Tic-Tac-Toe
    is_maximizing: True jika giliran MAX (X), False jika MIN (O)
    """
    # Base case: terminal state
    if game.is_terminal():
        return game.utility()
    
    if is_maximizing:
        best_value = float('-inf')
        for move in game.available_moves():
            game.make_move(move, 'X')
            value = minimax(game, False)
            game.undo_move(move)
            best_value = max(best_value, value)
        return best_value
    else:
        best_value = float('+inf')
        for move in game.available_moves():
            game.make_move(move, 'O')
            value = minimax(game, True)
            game.undo_move(move)
            best_value = min(best_value, value)
        return best_value

def get_best_move(game, player):
    """Mengembalikan posisi langkah terbaik untuk player"""
    best_move = None
    if player == 'X':  # MAX
        best_value = float('-inf')
        for move in game.available_moves():
            game.make_move(move, 'X')
            value = minimax(game, False)
            game.undo_move(move)
            if value > best_value:
                best_value = value
                best_move = move
    else:  # MIN
        best_value = float('+inf')
        for move in game.available_moves():
            game.make_move(move, 'O')
            value = minimax(game, True)
            game.undo_move(move)
            if value < best_value:
                best_value = value
                best_move = move
    return best_move

# Contoh penggunaan
game = TicTacToe()
print("Langkah terbaik untuk X:", get_best_move(game, 'X'))
```

**Jawaban:** Implementasi di atas menyediakan fungsi Minimax lengkap untuk Tic-Tac-Toe. Dengan algoritma ini, AI tidak akan pernah kalah jika bermain sebagai X atau O.

---

### 4.4 Analisis Kompleksitas Minimax

> **Kompleksitas Waktu Minimax:** $O(b^m)$
> - $b$ = branching factor (jumlah rata-rata langkah legal)
> - $m$ = kedalaman maksimum game tree

> **Kompleksitas Ruang:** $O(bm)$ untuk depth-first exploration

| Game | Branching Factor (b) | Depth (m) | Kompleksitas |
|------|---------------------|-----------|--------------|
| Tic-Tac-Toe | ~5 | 9 | ~10^6 |
| Checkers | ~3 | ~100 | ~10^40 |
| Chess | ~35 | ~100 | ~10^154 |
| Go | ~250 | ~150 | ~10^360 |

#### Solved Problem 9 ⭐

**Soal:** Jika sebuah game memiliki branching factor 10 dan kedalaman 6, berapa node yang harus dievaluasi oleh Minimax? Jika setiap evaluasi membutuhkan 1 μs, berapa lama waktu yang dibutuhkan?

**Penyelesaian:**

*Step 1:* Hitung jumlah node
$$N = b^m = 10^6 = 1,000,000 \text{ nodes}$$

*Step 2:* Hitung waktu total
$$T = 1,000,000 \times 1 \mu s = 1,000,000 \mu s = 1 \text{ detik}$$

**Jawaban:** Minimax harus mengevaluasi 1,000,000 nodes dan membutuhkan waktu sekitar **1 detik**.

---

#### Solved Problem 10 ⭐⭐

**Soal:** Untuk permainan catur dengan b=35 dan m=4 (melihat 4 langkah ke depan), hitung jumlah nodes yang dievaluasi. Bandingkan dengan m=8!

**Penyelesaian:**

*Step 1:* Hitung untuk m=4
$$N_4 = 35^4 = 1,500,625 \approx 1.5 \times 10^6 \text{ nodes}$$

*Step 2:* Hitung untuk m=8
$$N_8 = 35^8 = 2.25 \times 10^{12} \text{ nodes}$$

*Step 3:* Bandingkan

| Kedalaman | Nodes | Waktu (1 μs/node) |
|-----------|-------|-------------------|
| m=4 | 1.5 juta | 1.5 detik |
| m=8 | 2.25 triliun | ~26 hari |

**Jawaban:** Meningkatkan kedalaman dari 4 ke 8 meningkatkan jumlah nodes dari 1.5 juta menjadi 2.25 triliun—peningkatan 1.5 juta kali lipat! Ini menunjukkan bahwa Minimax murni tidak praktis untuk game kompleks seperti catur.

---

## 5. Fungsi Evaluasi

### 5.1 Kebutuhan Fungsi Evaluasi

Karena keterbatasan komputasi, kita tidak selalu bisa menghitung Minimax hingga terminal state. Solusinya adalah menggunakan **fungsi evaluasi** untuk memperkirakan nilai state non-terminal.

> **Fungsi Evaluasi (Evaluation Function)** adalah fungsi yang memberikan estimasi nilai state tanpa perlu mengeksplorasi hingga terminal state. Fungsi ini menggantikan utility function untuk non-terminal states.

![Cutoff dengan Fungsi Evaluasi](images/p05-05-evaluation-function-cutoff.png)

*Gambar 5.5: Penggunaan fungsi evaluasi dengan depth cutoff*

### 5.2 Properti Fungsi Evaluasi yang Baik

Fungsi evaluasi yang baik harus memenuhi:

1. **Konsisten dengan utility**: Harus setuju dengan utility untuk terminal states
2. **Cepat dihitung**: Tidak boleh terlalu kompleks
3. **Reflektif terhadap peluang menang**: Nilai tinggi = peluang menang tinggi
4. **Linear combination**: Biasanya berupa weighted sum dari features

### 5.3 Contoh Fungsi Evaluasi

#### Untuk Tic-Tac-Toe:
```python
def evaluate(board, player):
    """
    Heuristic evaluation untuk Tic-Tac-Toe
    """
    score = 0
    lines = [
        [0,1,2], [3,4,5], [6,7,8],  # Baris
        [0,3,6], [1,4,7], [2,5,8],  # Kolom
        [0,4,8], [2,4,6]            # Diagonal
    ]
    
    for line in lines:
        player_count = sum(1 for i in line if board[i] == player)
        opponent_count = sum(1 for i in line if board[i] != ' ' and board[i] != player)
        empty_count = sum(1 for i in line if board[i] == ' ')
        
        # Nilai untuk setiap konfigurasi
        if player_count == 3:
            score += 100   # Menang
        elif player_count == 2 and empty_count == 1:
            score += 10    # Hampir menang
        elif player_count == 1 and empty_count == 2:
            score += 1     # Potensi
        
        if opponent_count == 3:
            score -= 100
        elif opponent_count == 2 and empty_count == 1:
            score -= 10
        elif opponent_count == 1 and empty_count == 2:
            score -= 1
    
    return score
```

#### Untuk Catur:
$$Eval(s) = w_1 \cdot material + w_2 \cdot mobility + w_3 \cdot king\_safety + w_4 \cdot pawn\_structure + ...$$

**Material value:**
| Piece | Value |
|-------|-------|
| Pawn | 1 |
| Knight | 3 |
| Bishop | 3 |
| Rook | 5 |
| Queen | 9 |

#### Solved Problem 11 ⭐⭐

**Soal:** Rancang fungsi evaluasi sederhana untuk permainan Connect Four!

**Penyelesaian:**

*Step 1:* Identifikasi features penting
- Jumlah "ancaman" (3 berurutan dengan 1 kosong)
- Kontrol posisi tengah
- Jumlah potensi 4-berurutan

*Step 2:* Definisikan fungsi evaluasi

```python
def evaluate_connect4(board, player):
    """
    Evaluasi untuk Connect Four (7 kolom × 6 baris)
    """
    score = 0
    opponent = 'O' if player == 'X' else 'X'
    
    # Feature 1: Kontrol kolom tengah (kolom 3)
    center_count = sum(1 for row in range(6) if board[row][3] == player)
    score += center_count * 3
    
    # Feature 2: Evaluasi setiap "window" 4 posisi
    # Horizontal, Vertical, Diagonal
    
    def evaluate_window(window, player):
        score = 0
        player_count = window.count(player)
        empty_count = window.count(' ')
        opponent_count = window.count(opponent)
        
        if player_count == 4:
            score += 1000  # Menang
        elif player_count == 3 and empty_count == 1:
            score += 50    # Ancaman kuat
        elif player_count == 2 and empty_count == 2:
            score += 10    # Potensi
        
        if opponent_count == 3 and empty_count == 1:
            score -= 80    # Blok ancaman lawan
        
        return score
    
    # Evaluasi semua windows...
    # (implementasi detail untuk horizontal, vertical, diagonal)
    
    return score
```

**Jawaban:** Fungsi evaluasi Connect Four mempertimbangkan:
1. Kontrol posisi tengah (lebih fleksibel)
2. Jumlah ancaman 3-berurutan
3. Blocking ancaman lawan
4. Potensi pembentukan 4-berurutan

---

## 6. Alpha-Beta Pruning

### 6.1 Motivasi Alpha-Beta Pruning

Minimax mengevaluasi banyak node yang sebenarnya tidak mempengaruhi keputusan akhir. **Alpha-Beta Pruning** menghilangkan cabang-cabang yang tidak perlu dieksplorasi.

> **Alpha-Beta Pruning** adalah teknik optimasi untuk algoritma Minimax yang mengurangi jumlah node yang dievaluasi dengan memotong (pruning) cabang yang tidak akan mempengaruhi keputusan akhir.

**Ide Dasar:**
- **Alpha (α)**: Nilai terbaik yang sudah ditemukan MAX (lower bound)
- **Beta (β)**: Nilai terbaik yang sudah ditemukan MIN (upper bound)
- Jika α ≥ β, tidak perlu eksplorasi lebih lanjut (pruning)

### 6.2 Konsep Alpha dan Beta

![Ilustrasi Alpha-Beta Pruning](images/p05-06-alpha-beta-concept.png)

*Gambar 5.6: Konsep Alpha-Beta Pruning*

**Definisi:**
- **α (alpha)**: Nilai minimum yang dijamin dapat diperoleh MAX
- **β (beta)**: Nilai maksimum yang dijamin tidak akan dilampaui MIN

**Kondisi Pruning:**
- Pada node MIN: jika nilai ≤ α, prune sisa children (MAX tidak akan memilih path ini)
- Pada node MAX: jika nilai ≥ β, prune sisa children (MIN tidak akan memilih path ini)

### 6.3 Pseudocode Alpha-Beta Pruning

```python
def alpha_beta_search(state):
    """Mengembalikan aksi terbaik menggunakan alpha-beta pruning"""
    value, action = max_value(state, float('-inf'), float('+inf'))
    return action

def max_value(state, alpha, beta):
    """Menghitung nilai MAX dengan pruning"""
    if terminal_test(state):
        return utility(state), None
    
    v = float('-inf')
    best_action = None
    
    for action in actions(state):
        v2, _ = min_value(result(state, action), alpha, beta)
        if v2 > v:
            v = v2
            best_action = action
        
        # Pruning condition
        if v >= beta:
            return v, best_action  # Prune!
        
        alpha = max(alpha, v)
    
    return v, best_action

def min_value(state, alpha, beta):
    """Menghitung nilai MIN dengan pruning"""
    if terminal_test(state):
        return utility(state), None
    
    v = float('+inf')
    best_action = None
    
    for action in actions(state):
        v2, _ = max_value(result(state, action), alpha, beta)
        if v2 < v:
            v = v2
            best_action = action
        
        # Pruning condition
        if v <= alpha:
            return v, best_action  # Prune!
        
        beta = min(beta, v)
    
    return v, best_action
```

#### Solved Problem 12 ⭐⭐⭐

**Soal:** Terapkan Alpha-Beta Pruning pada game tree berikut. Tunjukkan node mana yang di-prune!

```
           A (MAX)
         /   |   \
        B    C    D (MIN)
       /\   /\   /\
      3  5 6  2 1  8
```

**Penyelesaian:**

*Step 1:* Inisialisasi
- α = -∞, β = +∞

*Step 2:* Evaluasi node B (MIN)
- Periksa child pertama: 3
- MIN value so far: 3
- β = min(+∞, 3) = 3
- Periksa child kedua: 5
- min(3, 5) = 3
- **Nilai B = 3**

*Step 3:* Update α di A
- α = max(-∞, 3) = 3

*Step 4:* Evaluasi node C (MIN)
- α = 3, β = +∞ (inherited)
- Periksa child pertama: 6
- MIN value so far: 6
- Periksa child kedua: 2
- min(6, 2) = 2
- **2 ≤ α (3)?** Ya! Tapi sudah selesai evaluasi.
- **Nilai C = 2**

*Step 5:* Node C tidak dipilih karena 2 < 3

*Step 6:* Evaluasi node D (MIN)
- α = 3, β = +∞
- Periksa child pertama: 1
- MIN value so far: 1
- **1 ≤ α (3)?** Ya!
- **PRUNE child kedua (8)!** ✂️
- **Nilai D = 1**

*Step 7:* Hasil akhir
- A = max(3, 2, 1) = **3**
- Optimal action: B

**Jawaban:**

| Node | Nilai | Pruning |
|------|-------|---------|
| A | 3 | - |
| B | 3 | Tidak |
| C | 2 | Tidak |
| D | 1 | Child 8 di-prune |

Node yang di-prune: **child dengan nilai 8 dari node D**. Total evaluasi: 5 nodes (bukan 6).

---

#### Solved Problem 13 ⭐⭐⭐

**Soal:** Implementasikan Alpha-Beta Pruning untuk Tic-Tac-Toe dalam Python dan bandingkan jumlah node yang dievaluasi dengan Minimax biasa!

**Penyelesaian:**

```python
class TicTacToeWithCounter:
    """Tic-Tac-Toe dengan counter untuk node evaluations"""
    
    def __init__(self):
        self.board = [' ' for _ in range(9)]
        self.nodes_evaluated = 0
    
    def reset_counter(self):
        self.nodes_evaluated = 0
    
    # ... (method lain sama seperti sebelumnya)

def minimax_with_count(game, is_maximizing):
    """Minimax dengan counting"""
    game.nodes_evaluated += 1
    
    if game.is_terminal():
        return game.utility()
    
    if is_maximizing:
        best = float('-inf')
        for move in game.available_moves():
            game.make_move(move, 'X')
            best = max(best, minimax_with_count(game, False))
            game.undo_move(move)
        return best
    else:
        best = float('+inf')
        for move in game.available_moves():
            game.make_move(move, 'O')
            best = min(best, minimax_with_count(game, True))
            game.undo_move(move)
        return best

def alpha_beta_with_count(game, alpha, beta, is_maximizing):
    """Alpha-Beta dengan counting"""
    game.nodes_evaluated += 1
    
    if game.is_terminal():
        return game.utility()
    
    if is_maximizing:
        best = float('-inf')
        for move in game.available_moves():
            game.make_move(move, 'X')
            best = max(best, alpha_beta_with_count(game, alpha, beta, False))
            game.undo_move(move)
            alpha = max(alpha, best)
            if beta <= alpha:
                break  # Pruning
        return best
    else:
        best = float('+inf')
        for move in game.available_moves():
            game.make_move(move, 'O')
            best = min(best, alpha_beta_with_count(game, alpha, beta, True))
            game.undo_move(move)
            beta = min(beta, best)
            if beta <= alpha:
                break  # Pruning
        return best

# Perbandingan
game = TicTacToeWithCounter()

# Minimax
game.reset_counter()
minimax_with_count(game, True)
minimax_nodes = game.nodes_evaluated

# Alpha-Beta
game.reset_counter()
alpha_beta_with_count(game, float('-inf'), float('+inf'), True)
alpha_beta_nodes = game.nodes_evaluated

print(f"Minimax nodes: {minimax_nodes}")
print(f"Alpha-Beta nodes: {alpha_beta_nodes}")
print(f"Reduction: {(1 - alpha_beta_nodes/minimax_nodes)*100:.1f}%")
```

**Hasil Perbandingan (dari posisi awal):**

| Algoritma | Nodes Evaluated | Reduction |
|-----------|-----------------|-----------|
| Minimax | ~549,946 | - |
| Alpha-Beta | ~18,297 | ~96.7% |

**Jawaban:** Alpha-Beta Pruning mengurangi jumlah node yang dievaluasi hingga ~97% pada Tic-Tac-Toe! Ini memungkinkan pencarian lebih dalam dengan waktu yang sama.

---

### 6.4 Efisiensi Alpha-Beta Pruning

> **Kompleksitas Optimal Alpha-Beta:** $O(b^{m/2})$
> - Setara dengan menggandakan kedalaman pencarian!
> - Tercapai jika node dievaluasi dalam urutan optimal

**Move Ordering:**
Efisiensi Alpha-Beta sangat bergantung pada urutan evaluasi node. Jika langkah terbaik dievaluasi terlebih dahulu, lebih banyak pruning terjadi.

| Kondisi | Kompleksitas | Penjelasan |
|---------|--------------|------------|
| Worst case | $O(b^m)$ | Tidak ada pruning |
| Random order | $O(b^{3m/4})$ | Pruning moderat |
| Perfect order | $O(b^{m/2})$ | Pruning optimal |

#### Solved Problem 14 ⭐⭐

**Soal:** Untuk catur dengan b=35, bandingkan kedalaman yang dapat dicapai dalam waktu sama antara Minimax dan Alpha-Beta dengan perfect ordering!

**Penyelesaian:**

*Step 1:* Tetapkan budget komputasi
Misalkan kita dapat mengevaluasi $N = 10^7$ nodes

*Step 2:* Kedalaman Minimax
$$b^m = 10^7$$
$$35^m = 10^7$$
$$m = \log_{35}(10^7) = \frac{7}{\log_{10}(35)} = \frac{7}{1.544} \approx 4.5$$

Kedalaman Minimax: **~4 ply**

*Step 3:* Kedalaman Alpha-Beta (perfect ordering)
$$b^{m/2} = 10^7$$
$$35^{m/2} = 10^7$$
$$m/2 = 4.5$$
$$m = 9$$

Kedalaman Alpha-Beta: **~9 ply**

**Jawaban:** Dengan budget komputasi yang sama, Alpha-Beta dengan perfect ordering dapat mencapai kedalaman **2x lebih dalam** (9 ply vs 4 ply) dibandingkan Minimax murni.

---

### 6.5 Teknik Move Ordering

Untuk mendekati efisiensi optimal, beberapa teknik move ordering digunakan:

1. **Killer Move Heuristic**: Simpan langkah yang menyebabkan cutoff sebelumnya
2. **History Heuristic**: Lacak langkah yang sering menyebabkan cutoff
3. **Iterative Deepening**: Gunakan hasil pencarian dangkal untuk mengurutkan langkah
4. **Transposition Table**: Cache hasil evaluasi untuk posisi yang sama

#### Solved Problem 15 ⭐⭐

**Soal:** Jelaskan bagaimana iterative deepening dapat meningkatkan efisiensi Alpha-Beta Pruning!

**Penyelesaian:**

*Step 1:* Konsep Iterative Deepening
- Lakukan pencarian dengan kedalaman 1, 2, 3, ... hingga batas waktu
- Simpan langkah terbaik dari setiap iterasi

*Step 2:* Integrasi dengan Alpha-Beta

```python
def iterative_deepening_alpha_beta(game, max_time):
    best_move = None
    depth = 1
    start_time = time.time()
    
    while time.time() - start_time < max_time:
        # Gunakan hasil depth-1 untuk ordering
        move_scores = []
        for move in sorted_moves(game, best_move):
            game.make_move(move, game.current_player)
            score = alpha_beta(game, depth, -inf, +inf, False)
            game.undo_move(move)
            move_scores.append((move, score))
        
        # Sort untuk iterasi berikutnya
        move_scores.sort(key=lambda x: x[1], reverse=True)
        best_move = move_scores[0][0]
        depth += 1
    
    return best_move
```

*Step 3:* Keuntungan
1. **Better ordering**: Langkah terbaik dari depth d-1 kemungkinan terbaik untuk depth d
2. **Anytime algorithm**: Selalu punya jawaban meski waktu habis
3. **Overhead minimal**: Waktu untuk depth 1..d-1 ≪ waktu untuk depth d

**Jawaban:** Iterative Deepening meningkatkan Alpha-Beta dengan:
1. Menyediakan ordering yang baik berdasarkan hasil pencarian sebelumnya
2. Menghasilkan anytime behavior (selalu punya langkah terbaik saat ini)
3. Overhead total hanya ~11% lebih banyak dari single-depth search

---

## 7. Expectiminimax: Game Stokastik

### 7.1 Motivasi

Untuk game dengan elemen keacakan (seperti dadu), Minimax standar tidak cukup karena hasil aksi tidak deterministik.

> **Expectiminimax** adalah variasi Minimax yang menangani game stokastik dengan menambahkan "chance nodes" untuk merepresentasikan hasil acak.

![Expectiminimax dengan Chance Nodes](images/p05-07-expectiminimax-tree.png)

*Gambar 5.7: Game tree dengan chance nodes untuk Expectiminimax*

### 7.2 Definisi Formal Expectiminimax

$$EXPECTIMINIMAX(n) = \begin{cases}
Utility(n) & \text{jika } n \text{ terminal} \\
\max_a EXPECTIMINIMAX(Result(n,a)) & \text{jika } Player(n) = MAX \\
\min_a EXPECTIMINIMAX(Result(n,a)) & \text{jika } Player(n) = MIN \\
\sum_r P(r) \cdot EXPECTIMINIMAX(Result(n,r)) & \text{jika } n \text{ adalah chance node}
\end{cases}$$

di mana $P(r)$ adalah probabilitas hasil acak $r$.

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Dalam game sederhana, MAX melempar dadu (1-6) sebelum bergerak. Jika hasil ≤ 3, MAX punya 2 pilihan dengan nilai {5, 3}. Jika hasil > 3, MAX punya 2 pilihan dengan nilai {8, 2}. Hitung nilai Expectiminimax!

**Penyelesaian:**

*Step 1:* Gambar game tree

```
         MAX
           |
       CHANCE (dadu)
       /       \
    P=0.5     P=0.5
     /           \
   MAX          MAX
   / \          / \
  5   3        8   2
```

*Step 2:* Hitung nilai MAX nodes (leaf-level MAX)
- MAX (hasil ≤ 3): max(5, 3) = **5**
- MAX (hasil > 3): max(8, 2) = **8**

*Step 3:* Hitung expected value di CHANCE node
$$E[V] = P(\leq 3) \times 5 + P(> 3) \times 8$$
$$E[V] = 0.5 \times 5 + 0.5 \times 8 = 2.5 + 4 = 6.5$$

**Jawaban:** Nilai Expectiminimax untuk game ini adalah **6.5**. MAX dapat mengharapkan rata-rata utility 6.5 dari permainan ini.

---

#### Solved Problem 17 ⭐⭐

**Soal:** Jelaskan mengapa Alpha-Beta Pruning kurang efektif pada Expectiminimax!

**Penyelesaian:**

*Step 1:* Analisis struktur Expectiminimax
- Chance nodes menghitung expected value (rata-rata tertimbang)
- Expected value bergantung pada SEMUA children

*Step 2:* Mengapa pruning terbatas

Pada chance node, kita menghitung:
$$E[V] = \sum_i P_i \times V_i$$

Untuk mengetahui E[V], kita HARUS mengetahui SEMUA $V_i$.

*Step 3:* Batasan pruning

| Kondisi | Minimax | Expectiminimax |
|---------|---------|----------------|
| MAX node | Prune jika v ≥ β | Sama |
| MIN node | Prune jika v ≤ α | Sama |
| CHANCE node | N/A | Tidak bisa prune! |

**Jawaban:** Alpha-Beta Pruning kurang efektif pada Expectiminimax karena:
1. **Chance nodes tidak bisa di-prune**: Expected value memerlukan semua nilai children
2. **Bounds lebih lemah**: Ketidakpastian membuat bounds α dan β kurang restrictive
3. **Kompleksitas tetap tinggi**: $O(b^m n^m)$ di mana n = jumlah outcomes per chance node

---

## 8. Aplikasi dalam Konteks Pertahanan

### 8.1 War Gaming dan Simulasi Strategi

Algoritma pencarian adversarial digunakan dalam:
- Simulasi konflik militer
- Perencanaan operasi
- Training decision making

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Sebuah skenario pertahanan pulau melibatkan dua pihak: Defender (memilih posisi 3 unit pertahanan) dan Attacker (memilih jalur serangan dari 2 opsi). Rancang formulasi game dan tentukan strategi optimal!

**Posisi pertahanan:** A, B, C (pilih 3 dari 5 lokasi: Utara, Timur, Selatan, Barat, Tengah)
**Jalur serangan:** Utara atau Selatan
**Payoff:** Defender menang jika ≥2 unit di jalur serangan, else Attacker menang

**Penyelesaian:**

*Step 1:* Formulasi game

- **Players:** Defender (MAX), Attacker (MIN)
- **Defender actions:** Kombinasi 3 dari 5 lokasi = C(5,3) = 10 pilihan
- **Attacker actions:** 2 jalur (Utara, Selatan)
- **Utility:** +1 (Defender wins), -1 (Attacker wins)

*Step 2:* Analisis payoff untuk beberapa konfigurasi

| Defender Config | Utara Attack | Selatan Attack |
|-----------------|--------------|----------------|
| U, T, S | +1 (2 at U path) | +1 (2 at S path) |
| U, T, B | +1 | -1 |
| U, B, Tengah | 0 (tergantung definisi) | -1 |
| ... | ... | ... |

*Step 3:* Minimax analysis (simplified)

Defender bertindak pertama, Attacker melihat dan memilih:

Untuk setiap konfigurasi Defender, Attacker pilih min(Utara, Selatan).

**Optimal strategy:**
- Defender harus memilih konfigurasi yang memaksimalkan minimum payoff
- Konfigurasi optimal: Menempatkan unit sehingga kedua jalur terlindungi

**Jawaban:** Strategi optimal Defender adalah menempatkan unit sehingga setidaknya 2 unit melindungi setiap jalur potensial. Contoh: {Utara, Selatan, Tengah} - memberikan 2 unit efektif untuk kedua jalur serangan (dengan asumsi Tengah dapat memperkuat kedua arah).

---

### 8.2 Cyber Attack-Defense

#### Solved Problem 19 ⭐⭐

**Soal:** Dalam skenario cyber defense, Defender memilih 2 sistem untuk diperkuat dari 4 sistem (A, B, C, D). Attacker memilih 1 sistem untuk diserang. Jika sistem diserang sudah diperkuat, Defender menang (+10). Jika tidak, kerugian bervariasi: A=-50, B=-30, C=-20, D=-10. Tentukan strategi optimal kedua pihak!

**Penyelesaian:**

*Step 1:* Buat payoff matrix

Defender pilih 2 dari 4: C(4,2) = 6 konfigurasi

| Defender \ Attacker | Attack A | Attack B | Attack C | Attack D |
|---------------------|----------|----------|----------|----------|
| {A, B} | +10 | +10 | -20 | -10 |
| {A, C} | +10 | -30 | +10 | -10 |
| {A, D} | +10 | -30 | -20 | +10 |
| {B, C} | -50 | +10 | +10 | -10 |
| {B, D} | -50 | +10 | -20 | +10 |
| {C, D} | -50 | -30 | +10 | +10 |

*Step 2:* Minimax analysis

Untuk setiap Defender strategy, Attacker pilih minimum:
- {A, B}: min(10, 10, -20, -10) = -20
- {A, C}: min(10, -30, 10, -10) = -30
- {A, D}: min(10, -30, -20, 10) = -30
- {B, C}: min(-50, 10, 10, -10) = -50
- {B, D}: min(-50, 10, -20, 10) = -50
- {C, D}: min(-50, -30, 10, 10) = -50

*Step 3:* Defender optimal

Defender memilih max(-20, -30, -30, -50, -50, -50) = **-20** dengan strategi **{A, B}**

**Jawaban:**
- **Defender optimal:** Lindungi sistem A dan B (kerugian maksimal -20)
- **Attacker optimal:** Serang sistem C (jika Defender optimal)
- **Nilai game:** -20 (Defender akan kalah 20 dalam worst case)

**Insight:** Defender harus memprioritaskan aset dengan kerugian tertinggi (A dan B).

---

## 9. Studi Kasus Komprehensif

### Solved Problem 20 ⭐⭐⭐

**Soal:** Implementasikan AI untuk game Connect Four dengan Minimax dan Alpha-Beta Pruning. Gunakan fungsi evaluasi yang mempertimbangkan posisi, ancaman, dan kontrol tengah!

**Penyelesaian:**

```python
import numpy as np

class ConnectFour:
    def __init__(self):
        self.rows = 6
        self.cols = 7
        self.board = np.zeros((self.rows, self.cols), dtype=int)
        # 0 = kosong, 1 = Player 1 (MAX), 2 = Player 2 (MIN)
    
    def valid_moves(self):
        """Kolom yang masih bisa diisi"""
        return [c for c in range(self.cols) if self.board[0][c] == 0]
    
    def drop_piece(self, col, player):
        """Jatuhkan piece ke kolom"""
        for row in range(self.rows - 1, -1, -1):
            if self.board[row][col] == 0:
                self.board[row][col] = player
                return row
        return -1
    
    def undo_move(self, col):
        """Batalkan langkah terakhir di kolom"""
        for row in range(self.rows):
            if self.board[row][col] != 0:
                self.board[row][col] = 0
                return
    
    def check_winner(self):
        """Cek pemenang: 0=belum, 1=P1 wins, 2=P2 wins, 3=draw"""
        # Check horizontal, vertical, diagonal
        for row in range(self.rows):
            for col in range(self.cols):
                if self.board[row][col] != 0:
                    player = self.board[row][col]
                    # Horizontal
                    if col + 3 < self.cols:
                        if all(self.board[row][col+i] == player for i in range(4)):
                            return player
                    # Vertical
                    if row + 3 < self.rows:
                        if all(self.board[row+i][col] == player for i in range(4)):
                            return player
                    # Diagonal /
                    if row + 3 < self.rows and col + 3 < self.cols:
                        if all(self.board[row+i][col+i] == player for i in range(4)):
                            return player
                    # Diagonal \
                    if row - 3 >= 0 and col + 3 < self.cols:
                        if all(self.board[row-i][col+i] == player for i in range(4)):
                            return player
        
        if len(self.valid_moves()) == 0:
            return 3  # Draw
        return 0  # Game continues
    
    def evaluate(self, player):
        """Fungsi evaluasi heuristik"""
        score = 0
        opponent = 3 - player
        
        # Feature 1: Kontrol kolom tengah
        center_col = self.cols // 2
        center_count = sum(1 for row in range(self.rows) 
                         if self.board[row][center_col] == player)
        score += center_count * 3
        
        # Feature 2: Evaluasi semua window of 4
        def evaluate_window(window):
            s = 0
            p_count = sum(1 for x in window if x == player)
            o_count = sum(1 for x in window if x == opponent)
            empty = sum(1 for x in window if x == 0)
            
            if p_count == 4:
                s += 1000
            elif p_count == 3 and empty == 1:
                s += 50
            elif p_count == 2 and empty == 2:
                s += 10
            
            if o_count == 3 and empty == 1:
                s -= 80
            
            return s
        
        # Horizontal windows
        for row in range(self.rows):
            for col in range(self.cols - 3):
                window = [self.board[row][col+i] for i in range(4)]
                score += evaluate_window(window)
        
        # Vertical windows
        for row in range(self.rows - 3):
            for col in range(self.cols):
                window = [self.board[row+i][col] for i in range(4)]
                score += evaluate_window(window)
        
        # Diagonal windows (kedua arah)
        for row in range(self.rows - 3):
            for col in range(self.cols - 3):
                window = [self.board[row+i][col+i] for i in range(4)]
                score += evaluate_window(window)
        
        for row in range(3, self.rows):
            for col in range(self.cols - 3):
                window = [self.board[row-i][col+i] for i in range(4)]
                score += evaluate_window(window)
        
        return score

def alpha_beta(game, depth, alpha, beta, maximizing, player):
    """Alpha-Beta Pruning untuk Connect Four"""
    winner = game.check_winner()
    
    if winner == player:
        return 10000 + depth
    elif winner == 3 - player:
        return -10000 - depth
    elif winner == 3:  # Draw
        return 0
    
    if depth == 0:
        return game.evaluate(player)
    
    if maximizing:
        value = float('-inf')
        for col in game.valid_moves():
            game.drop_piece(col, player)
            value = max(value, alpha_beta(game, depth-1, alpha, beta, False, player))
            game.undo_move(col)
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('+inf')
        opponent = 3 - player
        for col in game.valid_moves():
            game.drop_piece(col, opponent)
            value = min(value, alpha_beta(game, depth-1, alpha, beta, True, player))
            game.undo_move(col)
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value

def get_best_move(game, player, depth=5):
    """Cari langkah terbaik dengan Alpha-Beta"""
    best_col = None
    best_value = float('-inf')
    
    for col in game.valid_moves():
        game.drop_piece(col, player)
        value = alpha_beta(game, depth-1, float('-inf'), float('+inf'), False, player)
        game.undo_move(col)
        
        if value > best_value:
            best_value = value
            best_col = col
    
    return best_col, best_value

# Demo
game = ConnectFour()
best_col, value = get_best_move(game, player=1, depth=5)
print(f"Best move for Player 1: Column {best_col} (value: {value})")
```

**Jawaban:** Implementasi di atas menyediakan AI Connect Four yang dapat bermain dengan baik menggunakan Alpha-Beta Pruning dengan kedalaman 5. Fungsi evaluasi mempertimbangkan kontrol tengah, ancaman, dan potensi kemenangan.

---

#### Solved Problem 21 ⭐⭐

**Soal:** Analisis kompleksitas ruang dan waktu untuk Connect Four AI dengan kedalaman pencarian 8!

**Penyelesaian:**

*Step 1:* Parameter Connect Four
- Branching factor (b) ≈ 7 (maksimal 7 kolom)
- Kedalaman (m) = 8
- Board size = 6 × 7 = 42 posisi

*Step 2:* Kompleksitas tanpa pruning
$$T_{minimax} = O(b^m) = O(7^8) = O(5,764,801) \approx 5.8 \times 10^6$$

*Step 3:* Kompleksitas dengan Alpha-Beta (random ordering)
$$T_{alpha-beta} = O(b^{3m/4}) = O(7^6) = O(117,649) \approx 1.2 \times 10^5$$

*Step 4:* Kompleksitas dengan Alpha-Beta (perfect ordering)
$$T_{optimal} = O(b^{m/2}) = O(7^4) = O(2,401)$$

*Step 5:* Kompleksitas ruang
$$S = O(b \times m) = O(7 \times 8) = O(56)$$

**Jawaban:**

| Metode | Time Complexity | Nodes |
|--------|-----------------|-------|
| Minimax | O(7⁸) | ~5.8 juta |
| Alpha-Beta (random) | O(7⁶) | ~118 ribu |
| Alpha-Beta (optimal) | O(7⁴) | ~2.4 ribu |

Space complexity: O(56) untuk stack rekursif.

---

#### Solved Problem 22 ⭐

**Soal:** Jelaskan mengapa Connect Four "solved" dan apa artinya bagi algoritma AI!

**Penyelesaian:**

*Step 1:* Apa artinya "solved"?
- Game dikatakan "solved" jika hasil optimal dari posisi awal diketahui
- Connect Four di-solved oleh Victor Allis (1988)

*Step 2:* Hasil

> Connect Four adalah **first-player win** jika kedua pemain bermain optimal.

Strategi winning untuk first player:
1. Mulai di kolom tengah
2. Ikuti strategi yang sudah dikomputasi

*Step 3:* Implikasi untuk AI
- AI sempurna dapat dibuat dengan database posisi
- Praktisnya, Alpha-Beta dengan evaluasi cukup untuk bermain sangat kuat
- "Solving" memerlukan komputasi exhaustive (dilakukan sekali)

**Jawaban:** Connect Four adalah "solved game" dengan first-player win. Ini berarti:
1. AI sempurna dapat dibuat dengan lookup table
2. Untuk praktis, Alpha-Beta dengan depth 10+ sudah sangat kuat
3. Perfect play tidak diperlukan untuk mengalahkan manusia casual

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Dalam permainan Othello, branching factor rata-rata adalah ~10 dan kedalaman maksimum ~60. Berapa banyak node yang harus dievaluasi Minimax?

**Jawaban:** $10^{60}$ nodes - tidak praktis untuk dihitung secara lengkap. Diperlukan depth cutoff dan fungsi evaluasi.

---

### Problem S2 ⭐⭐
**Soal:** Mengapa center control penting dalam fungsi evaluasi untuk board games?

**Jawaban:** Kontrol posisi tengah memberikan:
1. Lebih banyak opsi gerakan (mobility)
2. Lebih banyak kemungkinan membentuk kombinasi menang
3. Fleksibilitas taktis lebih tinggi

---

### Problem S3 ⭐⭐
**Soal:** Bagaimana menangani game dengan informasi tidak sempurna seperti Poker?

**Jawaban:** Teknik yang digunakan termasuk:
1. Monte Carlo sampling untuk mengasumsikan distribusi kartu lawan
2. Regret minimization
3. Nash equilibrium computation
4. Ekspektasi atas semua kemungkinan kartu tersembunyi

---

### Problem S4 ⭐⭐⭐
**Soal:** Jelaskan mengapa DeepMind's AlphaGo menggunakan Monte Carlo Tree Search (MCTS) bukan pure Minimax!

**Jawaban:** 
1. Go memiliki branching factor ~250, terlalu besar untuk Minimax
2. MCTS menggunakan sampling dan tidak perlu fungsi evaluasi yang akurat
3. Neural network memberikan policy dan value yang memandu search
4. MCTS dapat memberikan "anytime" result

---

### Problem S5 ⭐⭐
**Soal:** Dalam konteks cyber warfare, bagaimana pencarian adversarial dapat digunakan untuk predict attacker behavior?

**Jawaban:**
1. Model attacker sebagai rational agent (MAX untuk attacker)
2. Defender sebagai MIN mencoba meminimalkan damage
3. Gunakan Minimax untuk memprediksi serangan yang paling rasional
4. Anticipate attacker moves untuk proactive defense
5. Keterbatasan: attacker mungkin tidak selalu rasional

---

## Ringkasan

| Konsep | Deskripsi |
|--------|-----------|
| **Pencarian Adversarial** | Pencarian dalam situasi kompetitif dengan agen lawan |
| **Zero-Sum Game** | Game di mana total utility semua pemain = 0 |
| **Game Tree** | Representasi semua kemungkinan permainan |
| **Minimax** | Algoritma untuk mencari langkah optimal dengan asumsi lawan optimal |
| **Kompleksitas Minimax** | O(b^m) - eksplorasi semua node |
| **Alpha-Beta Pruning** | Optimasi Minimax dengan memotong cabang tidak relevan |
| **Alpha (α)** | Lower bound - nilai minimum yang dijamin MAX |
| **Beta (β)** | Upper bound - nilai maksimum yang dijamin MIN |
| **Kompleksitas Alpha-Beta** | O(b^(m/2)) optimal, O(b^(3m/4)) rata-rata |
| **Fungsi Evaluasi** | Heuristik untuk estimasi nilai non-terminal state |
| **Move Ordering** | Teknik mengurutkan langkah untuk pruning lebih baik |
| **Expectiminimax** | Variasi Minimax untuk game dengan elemen stokastik |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 5: Adversarial Search**
2. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. Chapter 6.
3. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press.
4. CS188 Berkeley AI Materials: https://inst.eecs.berkeley.edu/~cs188/

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
