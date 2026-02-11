# Latihan Pertemuan 02: Pemecahan Masalah dengan Pencarian - Uninformed Search

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 02  
**Topik:** Pemecahan Masalah dengan Pencarian - Uninformed Search  
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
Manakah yang BUKAN merupakan komponen dari formulasi problem pencarian?
A. State Space
B. Initial State
C. Heuristic Function
D. Goal Test
E. Path Cost

### Soal 2
Pada algoritma Breadth-First Search (BFS), struktur data yang digunakan untuk menyimpan frontier adalah:
A. Stack (LIFO)
B. Queue (FIFO)
C. Priority Queue
D. Binary Search Tree
E. Hash Table

### Soal 3
Jika branching factor b = 4 dan kedalaman goal d = 3, berapa estimasi jumlah node yang di-generate oleh BFS pada worst case?
A. 12 node
B. 21 node
C. 64 node
D. 85 node
E. 256 node

### Soal 4
Algoritma pencarian mana yang memiliki space complexity paling efisien?
A. BFS dengan O(b^d)
B. DFS dengan O(bm)
C. IDS dengan O(bd)
D. UCS dengan O(b^(C*/ε))
E. Bidirectional BFS dengan O(b^(d/2))

### Soal 5
Pernyataan mana yang BENAR tentang Depth-First Search (DFS)?
A. DFS selalu complete untuk semua jenis graf
B. DFS selalu menemukan solusi optimal
C. DFS menggunakan Queue untuk menyimpan frontier
D. DFS memiliki space complexity linear terhadap kedalaman
E. DFS tidak dapat diimplementasikan secara rekursif

### Soal 6
Mengapa BFS tidak optimal ketika step cost bervariasi?
A. Karena BFS menggunakan stack
B. Karena BFS memilih node berdasarkan kedalaman, bukan biaya total
C. Karena BFS tidak complete
D. Karena BFS membutuhkan heuristik
E. Karena BFS tidak dapat menangani graf dengan cycle

### Soal 7
Pada Uniform-Cost Search (UCS), kapan goal test dilakukan?
A. Saat node di-generate (dimasukkan ke frontier)
B. Saat node di-expand (dikeluarkan dari frontier)
C. Sebelum pencarian dimulai
D. Setelah seluruh frontier kosong
E. Saat backtracking

### Soal 8
Iterative Deepening Search (IDS) menggabungkan keunggulan dari:
A. BFS (space efficiency) dan DFS (completeness)
B. BFS (completeness) dan DFS (space efficiency)
C. UCS (optimality) dan DFS (time efficiency)
D. A* (heuristic) dan BFS (simplicity)
E. Greedy (speed) dan UCS (optimality)

### Soal 9
Dalam notasi kompleksitas algoritma pencarian, apa yang dimaksud dengan parameter 'm'?
A. Jumlah node dalam state space
B. Kedalaman goal terdekat
C. Kedalaman maksimal dari search tree
D. Branching factor rata-rata
E. Biaya solusi optimal

### Soal 10
Untuk masalah 8-puzzle, berapa jumlah maksimal aksi yang dapat dilakukan dari satu state?
A. 2 aksi
B. 3 aksi
C. 4 aksi
D. 8 aksi
E. 9 aksi

### Soal 11
Apa yang dimaksud dengan "frontier" dalam konteks algoritma pencarian?
A. State yang sudah di-expand
B. State yang menjadi tujuan pencarian
C. Node yang sudah di-generate tetapi belum di-expand
D. Node yang tidak akan pernah dikunjungi
E. State awal dari pencarian

### Soal 12
Jika UCS diterapkan pada graf dengan semua edge memiliki cost yang sama (uniform), perilakunya akan identik dengan:
A. DFS
B. BFS
C. IDS
D. A*
E. Greedy Best-First Search

### Soal 13
Depth-Limited Search (DLS) dengan limit L = 0 akan:
A. Mengeksplorasi seluruh state space
B. Hanya memeriksa initial state
C. Berperilaku seperti BFS
D. Tidak pernah terminasi
E. Mengeksplorasi semua node pada level 1

### Soal 14
Manakah pernyataan yang BENAR tentang graph search vs tree search?
A. Tree search selalu lebih efisien dari graph search
B. Graph search menggunakan explored set untuk menghindari state berulang
C. Tree search tidak dapat menangani masalah dengan cycle
D. Graph search membutuhkan lebih sedikit memori
E. Keduanya menghasilkan solusi yang berbeda

### Soal 15
Pada pencarian dari Arad ke Bucharest, jika kita menggunakan BFS dan menemukan jalur Arad → Sibiu → Fagaras → Bucharest, apa yang dapat kita simpulkan?
A. Jalur ini pasti memiliki jarak terpendek
B. Jalur ini memiliki jumlah kota perantara minimum
C. Jalur ini adalah satu-satunya jalur yang valid
D. BFS gagal menemukan solusi optimal
E. Tidak ada kesimpulan yang dapat diambil

### Soal 16
Apa kelemahan utama dari algoritma DFS standar (tanpa depth limit)?
A. Membutuhkan terlalu banyak memori
B. Tidak dapat menemukan solusi yang ada (not complete) jika ada infinite path
C. Selalu menemukan solusi yang tidak optimal
D. Tidak dapat menangani graf dengan weighted edges
E. Membutuhkan heuristic function

### Soal 17
Berapa overhead (rasio) jumlah node yang di-generate IDS dibanding BFS untuk b=2 dan d=4?
A. Sekitar 1.0× (sama)
B. Sekitar 1.5×
C. Sekitar 2.0×
D. Sekitar 3.0×
E. Sekitar 4.0×

### Soal 18
Dalam konteks UCS, apa yang dimaksud dengan g(n)?
A. Estimasi biaya dari n ke goal
B. Total biaya dari initial state ke node n
C. Biaya heuristik
D. Kedalaman node n
E. Branching factor pada node n

### Soal 19
Algoritma pencarian mana yang paling cocok untuk sistem embedded dengan memori sangat terbatas yang perlu menemukan solusi dengan jumlah langkah minimum?
A. BFS
B. DFS
C. UCS
D. IDS
E. Bidirectional Search

### Soal 20
Jika sebuah problem memiliki solusi pada kedalaman d=5, tetapi DFS pertama kali mengeksplorasi cabang dengan kedalaman m=100 yang tidak mengandung goal, berapa perkiraan rasio waktu DFS vs BFS?
A. DFS 20× lebih cepat
B. DFS dan BFS sama
C. DFS 20× lebih lambat
D. DFS bisa sangat jauh lebih lambat (eksponensial)
E. Tidak dapat dibandingkan

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Formulasikan masalah "Menara Hanoi" dengan 3 disk sebagai problem pencarian. Tentukan:
a) State Space
b) Initial State
c) Goal State
d) Actions
e) Path Cost

### Soal 2 ⭐
Gambarkan search tree untuk graf berikut jika pencarian dimulai dari node A menggunakan BFS. Tunjukkan urutan ekspansi node!

```
    A --- B --- D
    |     |
    C --- E --- F (Goal)
```

### Soal 3 ⭐
Jelaskan perbedaan antara "complete" dan "optimal" dalam konteks evaluasi algoritma pencarian. Berikan contoh algoritma yang complete tapi tidak optimal!

### Soal 4 ⭐⭐
Terapkan algoritma DFS pada graf berikut. Tunjukkan isi stack di setiap iterasi dan tentukan jalur yang ditemukan! (Asumsikan eksplorasi secara alfabetis)

```
Start: S
Goal: G

    S --- A --- B
    |     |     |
    C --- D --- G
```

### Soal 5 ⭐⭐
Diberikan graf berbobot berikut. Terapkan algoritma UCS untuk menemukan jalur dengan biaya minimum dari S ke G. Tunjukkan isi priority queue di setiap langkah!

```
       3       2
    S ---- A ---- G
    |             ^
    2             |
    |      4      |
    B ---- C -----+
              1
```

### Soal 6 ⭐⭐
Jelaskan mengapa Iterative Deepening Search (IDS) memiliki overhead waktu yang relatif kecil meskipun mengulang eksplorasi dari awal setiap iterasi. Buktikan dengan perhitungan untuk b=3 dan d=4!

### Soal 7 ⭐⭐
Sebuah robot harus bernavigasi dalam grid 4×4. Robot berada di posisi (0,0) dan harus mencapai posisi (3,3). Robot hanya dapat bergerak ke atas, bawah, kiri, atau kanan (tidak diagonal).

a) Berapa ukuran state space?
b) Berapa branching factor maksimal dan rata-rata?
c) Algoritma mana yang Anda rekomendasikan? Jelaskan!

### Soal 8 ⭐⭐
Implementasikan fungsi `expand(node, problem)` dalam pseudocode yang menghasilkan semua child node dari suatu node. Jelaskan setiap langkahnya!

### Soal 9 ⭐⭐
Bandingkan perilaku BFS dan DFS pada binary tree sempurna dengan kedalaman 4 (total 31 node). Jika goal berada di:
a) Level 2
b) Level 4 (node paling kanan)

Hitung jumlah node yang di-expand untuk setiap kasus!

### Soal 10 ⭐⭐⭐
Buktikan bahwa BFS adalah complete dan optimal untuk masalah dengan step cost uniform! Gunakan argumen formal.

### Soal 11 ⭐⭐⭐
Modifikasi algoritma BFS untuk menghitung jarak terpendek (jumlah edge) dari satu node ke SEMUA node lain dalam graf tidak berbobot. Tuliskan pseudocode lengkap!

### Soal 12 ⭐⭐⭐
Analisis trade-off antara BFS, DFS, dan IDS untuk masalah dengan karakteristik berikut:
- Branching factor: b = 10
- Kedalaman goal: d = 6
- Kedalaman maksimal: m = 20
- Memori tersedia: dapat menyimpan maksimal 10.000 node

Algoritma mana yang feasible? Jelaskan dengan perhitungan!

### Soal 13 ⭐⭐⭐
Rancang sebuah variasi DFS yang dapat mendeteksi cycle dan menghindari infinite loop tanpa menggunakan explored set yang menyimpan semua state yang pernah dikunjungi. Jelaskan strateginya!

### Soal 14 ⭐⭐⭐
Jelaskan bagaimana Bidirectional Search bekerja dan mengapa kompleksitas waktunya adalah O(b^(d/2)) bukan O(b^d). Dalam kondisi apa Bidirectional Search tidak dapat diterapkan?

### Soal 15 ⭐⭐⭐
Sebuah game memiliki state space dengan karakteristik berikut:
- 10^12 possible states
- Branching factor rata-rata: 35
- Solusi terdekat diperkirakan pada kedalaman 20
- Setiap state membutuhkan 100 bytes untuk disimpan

Analisis apakah uninformed search dapat menyelesaikan masalah ini. Jika tidak, apa alternatifnya? (akan dibahas di Pertemuan 3)

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Perencanaan Rute Patroli UAV

**Latar Belakang:**
Sebuah Unmanned Aerial Vehicle (UAV) / drone pengintai harus melakukan misi patroli dari Pangkalan Udara (PU) mengunjungi 4 pos pengamatan (A, B, C, D) dan kembali ke pangkalan. Setiap rute antar lokasi memiliki "skor risiko" yang mencerminkan kemungkinan deteksi oleh radar musuh.

**Data Risiko Deteksi (skala 1-10):**

| Dari/Ke | PU | A | B | C | D |
|---------|:--:|:-:|:-:|:-:|:-:|
| **PU** | - | 3 | 5 | 7 | 4 |
| **A** | 3 | - | 2 | 6 | 3 |
| **B** | 5 | 2 | - | 4 | 5 |
| **C** | 7 | 6 | 4 | - | 2 |
| **D** | 4 | 3 | 5 | 2 | - |

**Pertanyaan:**

**1a.** Formulasikan masalah ini sebagai problem pencarian. Tentukan semua komponen (state space, initial state, goal test, actions, path cost)!

**1b.** Berapa ukuran state space untuk masalah ini? Jelaskan perhitungannya!

**1c.** Algoritma uninformed search mana yang paling tepat untuk menemukan rute dengan risiko total minimum? Jelaskan alasannya!

**1d.** Terapkan algoritma yang Anda pilih untuk menemukan rute optimal. Tunjukkan langkah-langkah pencariannya!

**1e.** Jika ada batasan bahwa UAV harus mengunjungi pos C terlebih dahulu sebelum pos lainnya (karena prioritas intelijen), bagaimana ini mengubah formulasi masalah?

---

### Studi Kasus 2: Sistem Pendukung Keputusan Evakuasi

**Latar Belakang:**
Dalam skenario bencana atau konflik, sebuah tim evakuasi harus merencanakan rute dari zona darurat ke zona aman. Peta area dibagi menjadi grid 5×5 dengan beberapa sel tidak dapat dilalui (bangunan runtuh, zona berbahaya).

**Peta Area (0 = dapat dilalui, X = tidak dapat dilalui):**

```
    0   1   2   3   4
  +---+---+---+---+---+
0 | S | 0 | X | 0 | 0 |
  +---+---+---+---+---+
1 | 0 | X | X | 0 | 0 |
  +---+---+---+---+---+
2 | 0 | 0 | 0 | X | 0 |
  +---+---+---+---+---+
3 | X | X | 0 | 0 | 0 |
  +---+---+---+---+---+
4 | 0 | 0 | 0 | X | G |
  +---+---+---+---+---+

S = Start (0,0)
G = Goal (4,4)
```

**Kondisi Tambahan:**
- Tim dapat bergerak ke 4 arah (atas, bawah, kiri, kanan)
- Setiap langkah membutuhkan waktu 1 menit
- Ada keterbatasan memori pada perangkat komunikasi lapangan

**Pertanyaan:**

**2a.** Formulasikan masalah ini sebagai problem pencarian dengan semua komponennya!

**2b.** Terapkan BFS untuk menemukan jalur terpendek. Gambarkan proses pencarian dan tentukan jalur yang ditemukan!

**2c.** Terapkan DFS pada masalah yang sama. Bandingkan hasilnya dengan BFS!

**2d.** Jika perangkat komunikasi hanya dapat menyimpan 20 state dalam memori, algoritma mana yang lebih cocok: BFS, DFS, atau IDS? Jelaskan dengan analisis memori!

**2e.** Modifikasi masalah: beberapa sel memiliki "tingkat kesulitan" berbeda (waktu tempuh bervariasi). Berikan contoh peta dengan waktu tempuh bervariasi dan jelaskan mengapa UCS diperlukan!

**2f.** Dalam konteks operasi militer nyata, faktor apa saja selain jarak/waktu yang perlu dipertimbangkan dalam perencanaan rute evakuasi? Bagaimana faktor-faktor ini dapat diintegrasikan ke dalam model pencarian?

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|:-------:|------------|
| 1 | **C** | Heuristic Function adalah komponen informed search (Pertemuan 3), bukan uninformed search. Komponen problem pencarian: State Space, Initial State, Actions, Transition Model, Goal Test, Path Cost. |
| 2 | **B** | BFS menggunakan Queue (FIFO - First In First Out) untuk memastikan eksplorasi per level. |
| 3 | **D** | Total node = Σ(b^i) untuk i=0 sampai d = 1 + 4 + 16 + 64 = 85 node. |
| 4 | **C** | IDS memiliki O(bd) yang linear, paling efisien dibanding BFS O(b^d), DFS O(bm), dan UCS O(b^(C*/ε)). |
| 5 | **D** | DFS memiliki space complexity O(bm) yang linear terhadap kedalaman maksimal. DFS tidak complete dan tidak optimal. |
| 6 | **B** | BFS memilih node berdasarkan kedalaman/level, bukan biaya total, sehingga bisa menemukan solusi dengan biaya lebih tinggi terlebih dahulu. |
| 7 | **B** | Pada UCS, goal test dilakukan saat node di-expand (dikeluarkan dari frontier) untuk memastikan tidak ada jalur dengan biaya lebih rendah. |
| 8 | **B** | IDS menggabungkan completeness dan optimality dari BFS dengan space efficiency dari DFS. |
| 9 | **C** | Parameter m adalah maximum depth (kedalaman maksimal) dari search tree. |
| 10 | **C** | Kotak kosong dapat bergerak maksimal 4 arah (atas, bawah, kiri, kanan), jadi maksimal 4 aksi. |
| 11 | **C** | Frontier adalah himpunan node yang sudah di-generate tetapi belum di-expand (open list). |
| 12 | **B** | Jika semua edge cost sama, UCS akan mengeksplorasi berdasarkan jumlah edge (kedalaman), sama seperti BFS. |
| 13 | **B** | DLS dengan L=0 hanya memeriksa initial state tanpa ekspansi (node pada depth 0 tidak di-expand ke children). |
| 14 | **B** | Graph search menggunakan explored set untuk melacak state yang sudah dikunjungi dan menghindari eksplorasi berulang. |
| 15 | **B** | BFS menemukan jalur dengan jumlah edge minimum, bukan jarak terpendek (dalam km). Jalur ini memiliki jumlah kota perantara minimum. |
| 16 | **B** | DFS dapat terjebak dalam infinite path dan tidak pernah menemukan solusi meskipun solusi ada (not complete). |
| 17 | **B** | IDS: (4×2)+(3×4)+(2×8)+(1×16)+31 = 8+12+16+16+31 = 83. BFS: 1+2+4+8+16 = 31. Rasio ≈ 83/31 ≈ 2.7 ≈ 1.5× dengan formula umum. |
| 18 | **B** | g(n) adalah total path cost dari initial state ke node n dalam UCS. |
| 19 | **D** | IDS memiliki space O(bd) yang minimal, tetapi tetap complete dan optimal untuk uniform cost. |
| 20 | **D** | DFS bisa mengeksplorasi O(b^100) node sebelum backtrack, sementara BFS hanya O(b^5). Rasionya bisa sangat besar (eksponensial). |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐: Menara Hanoi

**a) State Space:**
Semua konfigurasi posisi 3 disk pada 3 tiang. Setiap disk bisa di salah satu dari 3 tiang, dan disk lebih besar harus di bawah disk lebih kecil.
Jumlah state valid = 3³ = 27 state (untuk 3 disk pada 3 tiang)

**b) Initial State:**
Semua 3 disk berada di tiang A, urutan dari bawah ke atas: besar, sedang, kecil.
Representasi: (A, A, A) atau {A: [3,2,1], B: [], C: []}

**c) Goal State:**
Semua 3 disk berada di tiang C dengan urutan sama.
Representasi: (C, C, C) atau {A: [], B: [], C: [3,2,1]}

**d) Actions:**
Pindahkan disk teratas dari satu tiang ke tiang lain, dengan syarat:
- Tidak boleh meletakkan disk lebih besar di atas disk lebih kecil
- Format: Move(dari, ke) di mana dari, ke ∈ {A, B, C}

**e) Path Cost:**
Setiap perpindahan memiliki cost = 1. Total cost = jumlah perpindahan.
Solusi optimal membutuhkan 2³ - 1 = 7 langkah.

---

#### Jawaban Soal 2 ⭐: BFS pada Graf

**Search Tree dan Urutan Ekspansi:**

```
Iterasi 1: Expand A
Queue: [A] → [B, C]
Explored: {A}

Iterasi 2: Expand B
Queue: [B, C] → [C, D, E]
Explored: {A, B}

Iterasi 3: Expand C
Queue: [C, D, E] → [D, E] (E sudah di queue)
Explored: {A, B, C}

Iterasi 4: Expand D
Queue: [D, E] → [E]
Explored: {A, B, C, D}

Iterasi 5: Expand E
Queue: [E] → [F]
Explored: {A, B, C, D, E}

Iterasi 6: Expand F → GOAL FOUND!
```

**Urutan ekspansi:** A → B → C → D → E → F
**Jalur ditemukan:** A → B → E → F atau A → C → E → F (keduanya 3 edge)

---

#### Jawaban Soal 3 ⭐: Complete vs Optimal

**Complete:** Algoritma dijamin menemukan solusi jika solusi ada dalam state space.

**Optimal:** Algoritma dijamin menemukan solusi dengan biaya minimum di antara semua solusi yang ada.

**Contoh algoritma complete tapi tidak optimal:** DFS dengan explored set (graph search)
- Complete karena dengan explored set tidak akan loop forever
- Tidak optimal karena bisa menemukan solusi pada cabang lebih dalam terlebih dahulu, padahal ada solusi lebih dangkal di cabang lain

Contoh lain: BFS pada graf dengan edge cost bervariasi
- Complete karena akan menemukan semua state yang reachable
- Tidak optimal karena menemukan solusi dengan edge count minimum, bukan cost minimum

---

#### Jawaban Soal 4 ⭐⭐: DFS pada Graf

| Iterasi | Pop | Stack (setelah push) | Explored |
|---------|-----|----------------------|----------|
| 0 | - | [S] | {} |
| 1 | S | [C, A] | {S} |
| 2 | A | [C, D, B] | {S, A} |
| 3 | B | [C, D, G] | {S, A, B} |
| 4 | G | **GOAL!** | {S, A, B, G} |

**Jalur ditemukan:** S → A → B → G

**Catatan:** Urutan push ke stack adalah reverse alfabetis agar pop menghasilkan urutan alfabetis.

---

#### Jawaban Soal 5 ⭐⭐: UCS pada Graf Berbobot

| Iterasi | Pop (node, g) | Priority Queue (setelah update) |
|---------|---------------|--------------------------------|
| 0 | - | [(S, 0)] |
| 1 | (S, 0) | [(B, 2), (A, 3)] |
| 2 | (B, 2) | [(A, 3), (C, 6)] |
| 3 | (A, 3) | [(G, 5), (C, 6)] |
| 4 | (G, 5) | **GOAL!** |

**Jalur optimal:** S → A → G dengan total cost = 3 + 2 = **5**

**Perbandingan jalur:**
- S → A → G: 3 + 2 = 5 ✓ (optimal)
- S → B → C → G: 2 + 4 + 1 = 7

---

#### Jawaban Soal 6 ⭐⭐: Overhead IDS

**Perhitungan untuk b=3, d=4:**

BFS: $N_{BFS} = \sum_{i=0}^{4} 3^i = 1 + 3 + 9 + 27 + 81 = 121$

IDS:
- Limit 0: 1
- Limit 1: 1 + 3 = 4
- Limit 2: 1 + 3 + 9 = 13
- Limit 3: 1 + 3 + 9 + 27 = 40
- Limit 4: 1 + 3 + 9 + 27 + 81 = 121

$N_{IDS} = 1 + 4 + 13 + 40 + 121 = 179$

**Rasio:** 179/121 ≈ **1.48×**

**Mengapa overhead kecil:**
Sebagian besar node (81 dari 121 = 67%) berada di level terdalam. Node di level atas yang di-regenerate berulang kali jumlahnya relatif sedikit dibanding total node.

Formula umum: $\frac{N_{IDS}}{N_{BFS}} = \frac{b}{b-1}$
Untuk b=3: 3/2 = 1.5 (sesuai perhitungan)

---

#### Jawaban Soal 7 ⭐⭐: Robot Grid 4×4

**a) Ukuran State Space:**
State = posisi (x, y) di mana x, y ∈ {0, 1, 2, 3}
Ukuran = 4 × 4 = **16 state**

**b) Branching Factor:**
- Maksimal: **4** (di tengah grid, bisa ke 4 arah)
- Minimal: **2** (di pojok)
- Rata-rata: sekitar **3** (perhitungan: 4 pojok × 2 + 8 sisi × 3 + 4 tengah × 4 = 8+24+16 = 48, rata-rata = 48/16 = 3)

**c) Rekomendasi:**
**BFS** atau **IDS** karena:
- State space kecil (16 state), memori bukan masalah
- Perlu solusi dengan langkah minimum
- BFS dijamin optimal untuk uniform step cost
- IDS juga cocok jika ingin menghemat memori

---

#### Jawaban Soal 8 ⭐⭐: Fungsi Expand

```python
def expand(node, problem):
    """
    Menghasilkan semua child node dari suatu node.
    
    Args:
        node: Node yang akan di-expand
        problem: Problem definition dengan methods:
                 - actions(state): mengembalikan list aksi valid
                 - result(state, action): mengembalikan state baru
                 - step_cost(state, action, next_state): biaya langkah
    
    Returns:
        children: List of child nodes
    """
    children = []
    state = node.state
    
    # Langkah 1: Dapatkan semua aksi yang valid dari state saat ini
    valid_actions = problem.actions(state)
    
    # Langkah 2: Untuk setiap aksi, generate child node
    for action in valid_actions:
        # Langkah 3: Hitung state baru menggunakan transition model
        next_state = problem.result(state, action)
        
        # Langkah 4: Hitung path cost ke child
        step_cost = problem.step_cost(state, action, next_state)
        child_path_cost = node.path_cost + step_cost
        
        # Langkah 5: Buat child node dengan referensi ke parent
        child = Node(
            state=next_state,
            parent=node,
            action=action,
            path_cost=child_path_cost
        )
        
        children.append(child)
    
    return children
```

---

#### Jawaban Soal 9 ⭐⭐: BFS vs DFS pada Binary Tree

Binary tree sempurna depth 4: 1 + 2 + 4 + 8 + 16 = 31 node

**a) Goal di Level 2:**

BFS:
- Expand level 0: 1 node
- Expand level 1: 2 nodes
- Expand level 2: menemukan goal setelah expand ~2-3 nodes
- **Total: ~5-6 node di-expand**

DFS:
- Jika goal di subtree kiri: ~3-7 nodes
- Jika goal di subtree kanan: expand seluruh subtree kiri dulu = 1+2+4+8 = 15, lalu ~3-7 di kanan
- **Worst case: ~18-20 nodes**

**b) Goal di Level 4 (paling kanan):**

BFS:
- Expand semua level 0-3: 1 + 2 + 4 + 8 = 15 nodes
- Expand level 4 sampai ketemu goal paling kanan: 16 nodes
- **Total: 31 nodes (semua)**

DFS (dengan urutan left-first):
- Explore seluruh subtree kiri: 1+1+1+1 = 4 (spine) + siblings
- Backtrack dan akhirnya sampai paling kanan
- **Total: ~31 nodes (semua)**

Untuk kasus (b), keduanya mengeksplorasi hampir semua node.

---

#### Jawaban Soal 10 ⭐⭐⭐: Bukti BFS Complete dan Optimal

**Bukti Completeness:**

1. **Asumsi:** b (branching factor) terbatas dan solusi ada di kedalaman d
2. **Invariant:** BFS mengeksplorasi semua node di level k sebelum level k+1
3. **Argumen:**
   - Untuk setiap level k, jumlah node terbatas (≤ b^k)
   - BFS akan menyelesaikan eksplorasi level k dalam waktu finite
   - Karena solusi di level d, BFS akan sampai ke level d
   - Saat sampai di level d, goal akan ditemukan
4. **Kesimpulan:** BFS complete jika b terbatas

**Bukti Optimality (untuk uniform step cost):**

1. **Asumsi:** Setiap aksi memiliki cost = c (uniform)
2. **Lemma:** Untuk node n di level k, path_cost(n) = k × c
3. **Argumen:**
   - BFS menemukan solusi di level d terlebih dahulu
   - Semua solusi di level d memiliki cost = d × c
   - Solusi di level d' > d memiliki cost = d' × c > d × c
   - Karena BFS menemukan solusi level d sebelum level d', solusi yang ditemukan memiliki cost minimum
4. **Kesimpulan:** BFS optimal untuk uniform step cost

---

#### Jawaban Soal 11 ⭐⭐⭐: BFS untuk Single-Source Shortest Path

```python
def bfs_all_distances(graph, source):
    """
    Menghitung jarak terpendek dari source ke semua node.
    
    Args:
        graph: adjacency list {node: [neighbors]}
        source: node awal
    
    Returns:
        distances: dict {node: distance from source}
    """
    # Inisialisasi jarak: -1 berarti belum dikunjungi
    distances = {node: -1 for node in graph}
    distances[source] = 0
    
    # Queue untuk BFS
    queue = [source]
    
    while queue:
        current = queue.pop(0)  # Dequeue (FIFO)
        current_dist = distances[current]
        
        # Explore semua neighbor
        for neighbor in graph[current]:
            if distances[neighbor] == -1:  # Belum dikunjungi
                distances[neighbor] = current_dist + 1
                queue.append(neighbor)
    
    return distances

# Contoh penggunaan:
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

distances = bfs_all_distances(graph, 'A')
# Output: {'A': 0, 'B': 1, 'C': 1, 'D': 2, 'E': 2, 'F': 2}
```

---

#### Jawaban Soal 12 ⭐⭐⭐: Analisis Trade-off dengan Constraint Memori

**Parameter:**
- b = 10, d = 6, m = 20
- Memori: 10.000 node

**Analisis:**

**BFS:**
- Space: O(b^d) = 10^6 = 1.000.000 node
- **TIDAK FEASIBLE** (melebihi 10.000 node)

**DFS:**
- Space: O(bm) = 10 × 20 = 200 node
- **FEASIBLE** secara memori
- Tapi tidak complete dan tidak optimal

**IDS:**
- Space: O(bd) = 10 × 6 = 60 node
- **FEASIBLE** dan **OPTIMAL** untuk uniform cost
- Time: O(b^d) = 10^6 operations (acceptable)

**Kesimpulan:** 
- **IDS adalah pilihan terbaik** karena feasible dalam memori, complete, dan optimal
- DFS feasible tapi bisa gagal menemukan solusi atau menemukan solusi suboptimal
- BFS tidak feasible karena memori

---

#### Jawaban Soal 13 ⭐⭐⭐: DFS dengan Cycle Detection tanpa Full Explored Set

**Strategi: Path-based Cycle Detection**

```python
def dfs_with_path_cycle_detection(problem):
    """
    DFS yang hanya menyimpan node di path saat ini untuk detect cycle.
    Space: O(m) bukan O(|V|)
    """
    def recursive_dfs(node, path_states):
        # Goal test
        if problem.goal_test(node.state):
            return node.path()
        
        # Expand
        for action in problem.actions(node.state):
            child = node.child(problem, action)
            
            # Cycle detection: cek apakah state sudah ada di path saat ini
            if child.state not in path_states:
                path_states.add(child.state)
                result = recursive_dfs(child, path_states)
                if result is not None:
                    return result
                path_states.remove(child.state)  # Backtrack
        
        return None
    
    initial = Node(problem.initial_state)
    path_states = {initial.state}
    return recursive_dfs(initial, path_states)
```

**Keunggulan:**
- Space hanya O(m) untuk menyimpan path saat ini
- Dapat mendeteksi cycle dalam path saat ini
- Menghindari infinite loop pada cycle

**Kelemahan:**
- Masih bisa mengeksplorasi state yang sama melalui path berbeda
- Tidak se-efisien graph search untuk state space dengan banyak path ke state yang sama

---

#### Jawaban Soal 14 ⭐⭐⭐: Bidirectional Search

**Cara Kerja:**
1. Jalankan dua pencarian secara bersamaan:
   - Forward search dari initial state
   - Backward search dari goal state
2. Bergantian expand satu node dari masing-masing frontier
3. Berhenti ketika kedua frontier "bertemu" (ada state yang muncul di keduanya)

**Mengapa O(b^(d/2)):**
- Unidirectional BFS: explore sampai depth d → O(b^d) nodes
- Bidirectional: masing-masing explore sampai depth d/2
- Forward: O(b^(d/2)) nodes
- Backward: O(b^(d/2)) nodes
- Total: 2 × O(b^(d/2)) = O(b^(d/2))

**Contoh numerik:** b=10, d=6
- Unidirectional: 10^6 = 1.000.000
- Bidirectional: 2 × 10^3 = 2.000
- **Speedup: 500×**

**Kondisi tidak dapat diterapkan:**
1. Goal state tidak diketahui secara eksplisit (hanya goal test)
2. Actions tidak reversible (tidak bisa backward search)
3. Banyak goal states (sulit memulai backward search)
4. State space tidak terhubung baik dari kedua arah

---

#### Jawaban Soal 15 ⭐⭐⭐: Analisis Feasibility untuk Game

**Parameter:**
- State space: 10^12 states
- b = 35
- d = 20
- Memory per state: 100 bytes

**Analisis Uninformed Search:**

**BFS/UCS:**
- Space: O(b^d) = 35^20 ≈ 10^31 states
- Memory: 10^31 × 100 bytes = 10^33 bytes = 10^24 GB
- **IMPOSSIBLE** (lebih besar dari semua storage di dunia)

**DFS:**
- Space: O(bm) ≈ 35 × 20 = 700 states = 70 KB ✓
- Time: O(b^m) ≈ 35^20 ≈ 10^31 operations
- Jika 10^9 ops/sec: 10^22 detik ≈ 10^14 tahun
- **IMPOSSIBLE** secara waktu

**IDS:**
- Space: O(bd) = 35 × 20 = 700 states ✓
- Time: O(b^d) ≈ 35^20 ≈ 10^31 operations
- **IMPOSSIBLE** secara waktu

**Kesimpulan:**
Uninformed search **TIDAK DAPAT** menyelesaikan masalah ini karena:
- Time complexity eksponensial terlalu besar
- State space terlalu besar untuk exhaustive search

**Alternatif (Pertemuan 3 dan seterusnya):**
1. **Informed Search (A*)**: Menggunakan heuristic untuk memangkas search space
2. **Local Search**: Hill climbing, simulated annealing (Pertemuan 4)
3. **Monte Carlo Tree Search**: Untuk game (Pertemuan 5)
4. **Machine Learning**: Learn evaluation function

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Perencanaan Rute Patroli UAV

**1a. Formulasi Problem:**

| Komponen | Deskripsi |
|----------|-----------|
| **State Space** | (lokasi_saat_ini, {pos_dikunjungi}) misalnya (PU, {}), (A, {A}), (B, {A,B}), ... |
| **Initial State** | (PU, {}) - di pangkalan, belum ada pos dikunjungi |
| **Goal Test** | lokasi = PU AND {A,B,C,D} ⊆ pos_dikunjungi |
| **Actions** | Terbang ke pos yang belum dikunjungi, atau kembali ke PU jika semua sudah dikunjungi |
| **Path Cost** | Total skor risiko dari semua segmen perjalanan |

**1b. Ukuran State Space:**

State = (lokasi, subset dari {A,B,C,D})
- Lokasi: 5 pilihan (PU, A, B, C, D)
- Subset: 2^4 = 16 kemungkinan

Namun tidak semua kombinasi valid (harus konsisten dengan perjalanan).
- State reachable dari initial:
  - Level 0: (PU, {}) = 1
  - Level 1: (A, {A}), (B, {B}), (C, {C}), (D, {D}) = 4
  - Level 2: 4 × 3 = 12
  - Level 3: 12 × 2 = 24
  - Level 4: 24 × 1 = 24
  - Level 5 (return): 24

**Total state reachable ≈ 1 + 4 + 12 + 24 + 24 + 24 = 89 states**

**1c. Algoritma yang Tepat:**

**Uniform-Cost Search (UCS)** karena:
- Edge cost (risiko) bervariasi
- Perlu menemukan jalur dengan total risiko minimum
- UCS menjamin optimalitas
- State space cukup kecil untuk UCS

**1d. Penerapan UCS:**

Memulai dengan (PU, {}, cost=0)

| Langkah | Expand | g(n) | Priority Queue |
|---------|--------|------|----------------|
| 1 | (PU, {}) | 0 | [(A,{A},3), (D,{D},4), (B,{B},5), (C,{C},7)] |
| 2 | (A, {A}) | 3 | [(D,{D},4), (B,{B},5), (B,{A,B},5), (D,{A,D},6), ...] |
| ... | ... | ... | ... |

**Rute optimal yang ditemukan:** PU → A → B → D → C → PU
Risiko: 3 + 2 + 5 + 2 + 7 = **19** (atau jalur serupa dengan total sama)

Verifikasi beberapa jalur:
- PU→A→B→D→C→PU: 3+2+5+2+7 = 19
- PU→A→D→C→B→PU: 3+3+2+4+5 = 17 ✓
- PU→D→A→B→C→PU: 4+3+2+4+7 = 20

**Jalur optimal: PU → A → D → C → B → PU dengan risiko total = 17**

**1e. Modifikasi dengan Constraint:**

Jika C harus dikunjungi pertama:
- **Initial State:** (PU, {})
- **Constraint:** Aksi pertama harus ke C
- **Modifikasi:** Ubah initial state menjadi (C, {C}) dengan cost awal = 7

Atau modifikasi actions:
```
if pos_dikunjungi == {}:
    return [GoTo(C)]  # Hanya boleh ke C dulu
else:
    return [GoTo(x) for x in belum_dikunjungi]
```

---

#### Studi Kasus 2: Sistem Pendukung Keputusan Evakuasi

**2a. Formulasi Problem:**

| Komponen | Deskripsi |
|----------|-----------|
| **State Space** | Semua posisi (x, y) yang dapat dilalui dalam grid 5×5 |
| **Initial State** | (0, 0) - posisi S |
| **Goal Test** | State = (4, 4) - posisi G |
| **Actions** | {UP, DOWN, LEFT, RIGHT} yang valid (dalam batas dan bukan X) |
| **Transition Model** | Result((x,y), UP) = (x-1, y) jika valid |
| **Path Cost** | Jumlah langkah (setiap langkah = 1 menit) |

**2b. BFS untuk Jalur Terpendek:**

```
Peta dengan koordinat:
    0   1   2   3   4
  +---+---+---+---+---+
0 | S | . | X | . | . |
  +---+---+---+---+---+
1 | . | X | X | . | . |
  +---+---+---+---+---+
2 | . | . | . | X | . |
  +---+---+---+---+---+
3 | X | X | . | . | . |
  +---+---+---+---+---+
4 | . | . | . | X | G |
  +---+---+---+---+---+
```

**Proses BFS:**

| Level | Cells Explored | Queue |
|-------|----------------|-------|
| 0 | (0,0) | [(0,1), (1,0)] |
| 1 | (0,1), (1,0) | [(2,0)] |
| 2 | (2,0) | [(2,1)] |
| 3 | (2,1) | [(2,2)] |
| 4 | (2,2) | [(3,2)] |
| 5 | (3,2) | [(3,3)] |
| 6 | (3,3) | [(3,4), (4,3)] |
| 7 | (3,4), (4,3) | [(4,4)] |
| 8 | (4,4) | **GOAL!** |

**Jalur BFS:** (0,0)→(1,0)→(2,0)→(2,1)→(2,2)→(3,2)→(3,3)→(3,4)→(4,4)
**Panjang: 8 langkah**

**2c. DFS pada Masalah yang Sama:**

DFS mungkin menemukan jalur berbeda tergantung urutan eksplorasi:
- Jika prioritas: DOWN > RIGHT > UP > LEFT
- Path: (0,0)→(1,0)→(2,0)→(2,1)→(2,2)→(3,2)→(3,3)→(3,4)→(4,4)
- Kebetulan sama dengan BFS

- Jika prioritas: RIGHT > DOWN > UP > LEFT
- Path: (0,0)→(0,1) → stuck! backtrack → (1,0)→... 
- Bisa lebih panjang atau sama

**Perbandingan:**
| Aspek | BFS | DFS |
|-------|-----|-----|
| Jalur | Optimal (8 langkah) | Bisa sama atau lebih panjang |
| Node expanded | ~15 | Bervariasi |
| Memory | Lebih banyak | Lebih sedikit |

**2d. Analisis Memori (limit 20 states):**

**BFS:**
- Worst case frontier: seluruh level → bisa > 20 states
- Grid 5×5 dengan obstacles: level terbesar ~5 states
- **Marginal** - mungkin feasible tapi tight

**DFS:**
- Space: O(depth) ≈ 8-10 states
- **Feasible** dengan memori terbatas

**IDS:**
- Space: O(d) ≈ 8-10 states
- **Feasible** dan **optimal**

**Rekomendasi: IDS** karena:
- Memori hanya ~10 states (< 20)
- Masih menjamin jalur optimal
- Complete

**2e. Modifikasi dengan Waktu Tempuh Bervariasi:**

```
Peta dengan waktu tempuh:
    0   1   2   3   4
  +---+---+---+---+---+
0 | S |2s | X |1s |1s |
  +---+---+---+---+---+
1 |1s | X | X |1s |1s |
  +---+---+---+---+---+
2 |1s |3s |1s | X |2s |  (s = menit/detik)
  +---+---+---+---+---+
3 | X | X |1s |1s |1s |
  +---+---+---+---+---+
4 |2s |2s |1s | X | G |
  +---+---+---+---+---+
```

Dengan waktu bervariasi:
- BFS path (8 steps) mungkin bukan tercepat
- UCS akan mempertimbangkan total waktu
- Contoh: jalur alternatif melalui sel "1s" mungkin lebih cepat dari jalur melalui sel "3s"

**UCS diperlukan** karena step cost (waktu) tidak uniform.

**2f. Faktor Tambahan dalam Operasi Militer Nyata:**

1. **Risiko/Ancaman:**
   - Zona tembakan musuh
   - Area dengan ranjau
   - Visibilitas dari posisi musuh

2. **Kapasitas/Kondisi Tim:**
   - Jumlah korban yang dibawa
   - Kondisi medis anggota tim
   - Beban logistik

3. **Medan/Lingkungan:**
   - Jenis terrain (aspal, tanah, air)
   - Kondisi cuaca
   - Penerangan

4. **Faktor Waktu:**
   - Deadline evakuasi
   - Jadwal patroli musuh
   - Golden hour untuk korban medis

5. **Komunikasi:**
   - Zona dead spot radio
   - Kebutuhan koordinasi dengan unit lain

**Integrasi ke Model Pencarian:**

```python
def total_cost(state, action, next_state):
    base_time = terrain_time[next_state]
    risk_factor = threat_level[next_state]
    fatigue = distance_traveled / team_capacity
    
    # Multi-objective optimization
    return (
        w1 * base_time + 
        w2 * risk_factor + 
        w3 * fatigue
    )
```

Di mana w1, w2, w3 adalah bobot yang mencerminkan prioritas misi (kecepatan vs keamanan vs stamina).

Pendekatan lanjutan: **Multi-objective search** atau **Pareto-optimal paths** untuk trade-off antara berbagai objektif.

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin  
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 135 poin

### Studi Kasus
- Studi Kasus 1: 60 poin
- Studi Kasus 2: 60 poin
- Total: 120 poin

### Total Keseluruhan: 295 poin

---

## Refleksi Pembelajaran

Setelah mengerjakan latihan ini, mahasiswa diharapkan dapat:

1. ✅ Memformulasikan berbagai masalah nyata sebagai problem pencarian
2. ✅ Memilih algoritma yang tepat berdasarkan karakteristik masalah
3. ✅ Menganalisis kompleksitas dan trade-off antar algoritma
4. ✅ Menerapkan algoritma uninformed search secara manual
5. ✅ Mengidentifikasi keterbatasan uninformed search untuk masalah kompleks
6. ✅ Mengintegrasikan konteks pertahanan ke dalam pemodelan pencarian

**Persiapan Pertemuan 3:** Pelajari konsep heuristik dan bagaimana informed search (Greedy, A*) dapat mengatasi keterbatasan uninformed search!

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
