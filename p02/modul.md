# Modul 02: Pemecahan Masalah dengan Pencarian - Uninformed Search

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 02  
**Topik:** Pemecahan Masalah dengan Pencarian - Uninformed Search  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Memformulasikan masalah nyata sebagai problem pencarian dengan mendefinisikan state space, initial state, goal test, actions, dan path cost
2. Menjelaskan perbedaan antara representasi search tree dan search graph
3. Menganalisis algoritma pencarian berdasarkan kriteria completeness, optimality, time complexity, dan space complexity
4. Mengimplementasikan algoritma Breadth-First Search (BFS) dan menganalisis kompleksitasnya
5. Mengimplementasikan algoritma Depth-First Search (DFS) beserta variasinya (depth-limited dan iterative deepening)
6. Mengimplementasikan algoritma Uniform-Cost Search (UCS) menggunakan priority queue
7. Membandingkan dan memilih algoritma pencarian yang tepat untuk berbagai jenis masalah

---

## 1. Pendahuluan: Pencarian sebagai Inti Kecerdasan Artifisial

Dalam Pertemuan 1, kita telah mempelajari bahwa **agen cerdas** beroperasi dalam suatu lingkungan dan mengambil keputusan untuk mencapai tujuannya. Pertanyaan fundamental yang muncul adalah: *bagaimana agen menemukan urutan aksi yang tepat untuk mencapai tujuan?*

Jawabannya adalah melalui **pencarian (search)**. Pencarian merupakan salah satu teknik paling fundamental dalam kecerdasan artifisial karena banyak masalah dapat diformulasikan sebagai masalah pencarian: menemukan rute terpendek, memecahkan puzzle, merencanakan gerakan robot, hingga mengalahkan lawan dalam permainan (yang akan dibahas di Pertemuan 5).

> **Definisi: Pencarian (Search)**  
> Pencarian adalah proses sistematis untuk menemukan urutan aksi yang mengubah kondisi awal (*initial state*) menjadi kondisi tujuan (*goal state*) dengan mengeksplorasi ruang kemungkinan (*state space*).

### 1.1 Klasifikasi Algoritma Pencarian

Algoritma pencarian dibagi menjadi dua kategori utama:

| Kategori | Karakteristik | Contoh Algoritma |
|----------|---------------|------------------|
| **Uninformed Search** (Blind Search) | Tidak memiliki informasi tambahan tentang seberapa dekat suatu state dengan goal | BFS, DFS, UCS |
| **Informed Search** (Heuristic Search) | Menggunakan fungsi heuristik untuk memperkirakan jarak ke goal | Greedy Best-First, A* (Pertemuan 3) |

Modul ini membahas **uninformed search**, yaitu strategi pencarian yang hanya menggunakan informasi yang tersedia dalam definisi masalah tanpa pengetahuan tambahan tentang lokasi goal.

---

## 2. Formulasi Masalah Pencarian

Langkah pertama dalam menyelesaikan masalah dengan pencarian adalah **memformulasikan masalah** ke dalam komponen-komponen standar.

### 2.1 Komponen Problem Pencarian

> **Definisi: Problem Pencarian**  
> Sebuah problem pencarian didefinisikan secara formal oleh lima komponen:
> 1. **State Space (S)**: Himpunan semua state yang mungkin
> 2. **Initial State (s₀)**: State awal dari mana pencarian dimulai
> 3. **Actions (A)**: Himpunan aksi yang dapat dilakukan pada setiap state
> 4. **Transition Model**: Fungsi Result(s, a) yang menghasilkan state baru setelah aksi a dilakukan pada state s
> 5. **Goal Test**: Fungsi yang menentukan apakah suatu state adalah goal state
> 6. **Path Cost**: Fungsi yang menghitung biaya dari suatu jalur (urutan aksi)

![Komponen Problem Pencarian](images/p02-01-komponen-problem-pencarian.png)

*Gambar 2.1: Lima komponen utama dalam formulasi problem pencarian*

### 2.2 Contoh: Masalah Romania

Contoh klasik dalam literatur AI adalah masalah mencari rute dari kota Arad ke Bucharest di Romania.

**Formulasi:**
- **State Space**: Semua kota di Romania
- **Initial State**: Arad
- **Actions**: Pergi ke kota tetangga yang terhubung jalan
- **Transition Model**: Result(Arad, GoTo(Sibiu)) = Sibiu
- **Goal Test**: Apakah state saat ini = Bucharest?
- **Path Cost**: Jarak total dalam kilometer

![Peta Romania](images/p02-02-peta-romania.png)

*Gambar 2.2: Graf jalan di Romania dengan jarak dalam kilometer*

---

#### Solved Problem 1 ⭐

**Soal:** Formulasikan masalah 8-puzzle sebagai problem pencarian!

![8-Puzzle](images/p02-03-8-puzzle.png)

*Gambar 2.3: Contoh konfigurasi 8-puzzle*

**Penyelesaian:**

| Komponen | Deskripsi |
|----------|-----------|
| **State Space** | Semua kemungkinan konfigurasi 8 angka pada grid 3×3 (ada 9!/2 = 181.440 state yang reachable) |
| **Initial State** | Konfigurasi awal puzzle yang diberikan |
| **Actions** | Menggeser kotak kosong ke atas, bawah, kiri, atau kanan (maksimal 4 aksi per state) |
| **Transition Model** | Result(state, slide_up) = state baru dengan kotak kosong bertukar posisi dengan kotak di atasnya |
| **Goal Test** | Apakah konfigurasi sudah urut 1-2-3-4-5-6-7-8-blank? |
| **Path Cost** | Jumlah langkah (setiap pergeseran = 1) |

---

#### Solved Problem 2 ⭐

**Soal:** Seorang prajurit harus menyeberangi medan dengan kondisi sebagai berikut:
- Titik awal: Pos A
- Tujuan: Pos E
- Dapat bergerak antar pos yang terhubung jalur
- Setiap jalur memiliki tingkat kesulitan berbeda (waktu tempuh dalam menit)

Formulasikan masalah ini sebagai problem pencarian!

**Penyelesaian:**

| Komponen | Deskripsi |
|----------|-----------|
| **State Space** | {Pos A, Pos B, Pos C, Pos D, Pos E} |
| **Initial State** | Pos A |
| **Actions** | Bergerak ke pos tetangga yang terhubung jalur |
| **Transition Model** | Result(Pos A, GoTo(Pos B)) = Pos B |
| **Goal Test** | Apakah state saat ini = Pos E? |
| **Path Cost** | Total waktu tempuh (menit) dari semua jalur yang dilalui |

**Konteks Pertahanan:** Dalam operasi militer, formulasi pencarian seperti ini digunakan untuk merencanakan rute patroli, evakuasi, atau penyusupan dengan memperhitungkan faktor medan, ancaman, dan waktu.

---

## 3. Search Tree dan Search Graph

### 3.1 Representasi Search Tree

Proses pencarian dapat divisualisasikan sebagai **pohon pencarian (search tree)** yang dibangun secara bertahap:

> **Definisi: Search Tree**  
> Search tree adalah struktur pohon di mana:
> - **Root** adalah initial state
> - **Node** merepresentasikan state
> - **Edge** merepresentasikan aksi
> - **Path** dari root ke suatu node merepresentasikan urutan aksi

![Search Tree](images/p02-04-search-tree.png)

*Gambar 2.4: Pembangunan search tree dari initial state*

**Terminologi Penting:**

| Istilah | Definisi |
|---------|----------|
| **Node** | State dalam search tree beserta informasi parent, action, path cost |
| **Expand** | Menghasilkan semua child node dari suatu node |
| **Frontier** | Himpunan node yang sudah di-generate tetapi belum di-expand (juga disebut *open list*) |
| **Explored Set** | Himpunan state yang sudah di-expand (juga disebut *closed list*) |

### 3.2 Search Tree vs Search Graph

Perbedaan krusial antara keduanya:

| Aspek | Search Tree | Search Graph |
|-------|-------------|--------------|
| **Struktur** | Pohon (tidak ada cycle) | Graf (bisa ada cycle) |
| **State berulang** | State yang sama bisa muncul di node berbeda | Setiap state hanya muncul sekali |
| **Memori** | Bisa sangat besar jika banyak state berulang | Lebih efisien dengan explored set |
| **Implementasi** | Lebih sederhana | Perlu tracking explored states |

> **Penting:** Dalam implementasi praktis, kita biasanya menggunakan **graph search** untuk menghindari eksplorasi state yang sama berulang kali.

---

#### Solved Problem 3 ⭐

**Soal:** Pada graf di bawah ini, jika kita memulai pencarian dari A, berapa banyak node yang akan di-expand dalam search tree sebelum menemukan G? (asumsikan eksplorasi alfabetis)

![Graf Pencarian Sederhana](images/p02-03-simple-search-graph.png)

*Gambar 2.5: Graf pencarian sederhana*

**Penyelesaian:**

Dalam **search tree** (tanpa pengecekan state berulang):
- Level 0: A di-expand → menghasilkan B, C, D
- Level 1: B di-expand → menghasilkan E; C di-expand → tidak ada child; D di-expand → menghasilkan F
- Level 2: E di-expand → menghasilkan G ✓

**Node yang di-expand:** A, B, C, D, E = **5 node**

Dalam **graph search** (dengan explored set):
- Hasilnya sama untuk kasus ini karena tidak ada state berulang

---

## 4. Kriteria Evaluasi Algoritma Pencarian

Untuk membandingkan berbagai algoritma pencarian, kita menggunakan empat kriteria standar:

### 4.1 Empat Kriteria Evaluasi

> **Definisi: Kriteria Evaluasi Algoritma Pencarian**
> 1. **Completeness**: Apakah algoritma dijamin menemukan solusi jika solusi ada?
> 2. **Optimality**: Apakah algoritma dijamin menemukan solusi dengan biaya terendah?
> 3. **Time Complexity**: Berapa banyak node yang di-generate?
> 4. **Space Complexity**: Berapa banyak node maksimal yang disimpan di memori?

### 4.2 Parameter Kompleksitas

Kompleksitas algoritma pencarian diukur dalam parameter:

| Parameter | Simbol | Deskripsi |
|-----------|--------|-----------|
| Branching factor | b | Jumlah maksimal successor dari setiap node |
| Depth of shallowest goal | d | Kedalaman goal terdekat dari root |
| Maximum depth | m | Kedalaman maksimal dari search tree |

![Ilustrasi Parameter](images/p02-05-parameter-kompleksitas.png)

*Gambar 2.6: Ilustrasi parameter b, d, dan m dalam search tree*

---

#### Solved Problem 4 ⭐

**Soal:** Sebuah search tree memiliki branching factor b = 4. Goal terdekat berada di kedalaman d = 3. Berapa jumlah node maksimal yang bisa di-generate pada level 0 hingga level d?

**Penyelesaian:**

Jumlah node pada setiap level:
- Level 0: 1 node (root)
- Level 1: 4 node (b¹)
- Level 2: 16 node (b²)
- Level 3: 64 node (b³)

Total = 1 + 4 + 16 + 64 = **85 node**

Formula umum: $\sum_{i=0}^{d} b^i = \frac{b^{d+1} - 1}{b - 1} = \frac{4^4 - 1}{4 - 1} = \frac{255}{3} = 85$

---

## 5. Breadth-First Search (BFS)

### 5.1 Konsep BFS

> **Definisi: Breadth-First Search (BFS)**  
> BFS adalah strategi pencarian yang mengeksplorasi semua node pada kedalaman d sebelum mengeksplorasi node pada kedalaman d+1. Implementasi menggunakan **queue (FIFO)** untuk frontier.

**Karakteristik:**
- Eksplorasi per level (melebar dulu)
- Menggunakan queue sebagai struktur data frontier
- Cocok untuk mencari solusi dengan langkah minimum

### 5.2 Algoritma BFS

```python
def breadth_first_search(problem):
    """
    Implementasi Breadth-First Search
    
    Args:
        problem: objek dengan atribut initial_state, goal_test(), 
                 actions(), result(), path_cost()
    
    Returns:
        path: list of actions menuju goal, atau None jika tidak ditemukan
    """
    # Inisialisasi node awal
    node = Node(problem.initial_state)
    
    # Early goal test
    if problem.goal_test(node.state):
        return node.path()
    
    # Frontier menggunakan queue (FIFO)
    frontier = Queue()
    frontier.enqueue(node)
    
    # Explored set untuk menghindari state berulang
    explored = set()
    
    while not frontier.is_empty():
        # Ambil node dari depan queue
        node = frontier.dequeue()
        explored.add(node.state)
        
        # Expand node: generate semua successor
        for action in problem.actions(node.state):
            child = node.child(problem, action)
            
            # Cek apakah state baru
            if child.state not in explored and child not in frontier:
                # Goal test
                if problem.goal_test(child.state):
                    return child.path()
                frontier.enqueue(child)
    
    # Tidak ada solusi
    return None
```

### 5.3 Visualisasi Ekspansi BFS

![BFS Expansion](images/p02-06-bfs-expansion.png)

*Gambar 2.7: Urutan ekspansi node pada BFS*

### 5.4 Analisis Kompleksitas BFS

| Kriteria | BFS |
|----------|-----|
| **Complete?** | Ya, jika b terbatas |
| **Optimal?** | Ya, jika semua step cost = 1 |
| **Time Complexity** | O(b^d) |
| **Space Complexity** | O(b^d) |

**Penjelasan:**
- BFS **complete** karena akan menemukan solusi di level d sebelum melanjutkan ke level d+1
- BFS **optimal** untuk step cost uniform karena menemukan solusi terdangkal terlebih dahulu
- Kompleksitas waktu dan ruang **eksponensial** karena harus menyimpan seluruh frontier level d

---

#### Solved Problem 5 ⭐⭐

**Soal:** Terapkan algoritma BFS pada graf berikut untuk mencari jalur dari S ke G. Tunjukkan isi queue pada setiap iterasi!

```
    S --- A --- B
    |     |     |
    C --- D --- G
```

**Penyelesaian:**

| Iterasi | Node Diproses | Queue (setelah ekspansi) | Explored |
|---------|---------------|--------------------------|----------|
| 0 | - | [S] | {} |
| 1 | S | [A, C] | {S} |
| 2 | A | [C, B, D] | {S, A} |
| 3 | C | [B, D] | {S, A, C} |
| 4 | B | [D, G] | {S, A, C, B} |
| 5 | D | [G] | {S, A, C, B, D} |
| 6 | G | **GOAL FOUND!** | {S, A, C, B, D, G} |

**Jalur yang ditemukan:** S → A → B → G (atau S → C → D → G, tergantung urutan ekspansi)

**Jumlah node yang di-expand:** 6 node

---

#### Solved Problem 6 ⭐⭐

**Soal:** Implementasikan BFS dalam C++ untuk mencari jalur dalam maze sederhana!

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <set>
#include <map>
using namespace std;

// Representasi state sebagai pasangan koordinat (x, y)
typedef pair<int, int> State;

// Struktur Node untuk search tree
struct Node {
    State state;
    Node* parent;
    string action;
    int path_cost;
    
    Node(State s, Node* p = nullptr, string a = "", int c = 0) 
        : state(s), parent(p), action(a), path_cost(c) {}
};

class MazeProblem {
public:
    vector<vector<int>> maze;
    State initial;
    State goal;
    int rows, cols;
    
    // Direction: Up, Down, Left, Right
    vector<pair<int,int>> directions = {{-1,0}, {1,0}, {0,-1}, {0,1}};
    vector<string> dir_names = {"UP", "DOWN", "LEFT", "RIGHT"};
    
    MazeProblem(vector<vector<int>>& m, State init, State g) 
        : maze(m), initial(init), goal(g) {
        rows = m.size();
        cols = m[0].size();
    }
    
    bool goal_test(State s) {
        return s == goal;
    }
    
    vector<pair<string, State>> successors(State s) {
        vector<pair<string, State>> result;
        for (int i = 0; i < 4; i++) {
            int nx = s.first + directions[i].first;
            int ny = s.second + directions[i].second;
            // Cek validitas: dalam batas dan bukan dinding
            if (nx >= 0 && nx < rows && ny >= 0 && ny < cols 
                && maze[nx][ny] != 1) {
                result.push_back({dir_names[i], {nx, ny}});
            }
        }
        return result;
    }
};

vector<string> bfs(MazeProblem& problem) {
    // Node awal
    Node* node = new Node(problem.initial);
    
    // Early goal test
    if (problem.goal_test(node->state)) {
        return {};  // Sudah di goal
    }
    
    // Frontier (queue)
    queue<Node*> frontier;
    frontier.push(node);
    
    // Explored set
    set<State> explored;
    set<State> in_frontier;
    in_frontier.insert(node->state);
    
    while (!frontier.empty()) {
        // Dequeue
        Node* node = frontier.front();
        frontier.pop();
        in_frontier.erase(node->state);
        
        // Tambah ke explored
        explored.insert(node->state);
        
        // Expand
        for (auto& [action, next_state] : problem.successors(node->state)) {
            if (explored.find(next_state) == explored.end() 
                && in_frontier.find(next_state) == in_frontier.end()) {
                
                Node* child = new Node(next_state, node, action, 
                                       node->path_cost + 1);
                
                // Goal test
                if (problem.goal_test(next_state)) {
                    // Rekonstruksi path
                    vector<string> path;
                    Node* current = child;
                    while (current->parent != nullptr) {
                        path.insert(path.begin(), current->action);
                        current = current->parent;
                    }
                    return path;
                }
                
                frontier.push(child);
                in_frontier.insert(next_state);
            }
        }
    }
    
    return {};  // Tidak ada solusi
}

int main() {
    // 0 = free, 1 = wall
    vector<vector<int>> maze = {
        {0, 0, 1, 0, 0},
        {0, 1, 0, 1, 0},
        {0, 0, 0, 0, 0},
        {1, 1, 1, 1, 0},
        {0, 0, 0, 0, 0}
    };
    
    State start = {0, 0};
    State goal = {4, 4};
    
    MazeProblem problem(maze, start, goal);
    vector<string> solution = bfs(problem);
    
    cout << "Solusi BFS:" << endl;
    for (const string& action : solution) {
        cout << action << " -> ";
    }
    cout << "GOAL" << endl;
    cout << "Jumlah langkah: " << solution.size() << endl;
    
    return 0;
}
```

**Output:**
```
Solusi BFS:
DOWN -> DOWN -> DOWN -> RIGHT -> DOWN -> RIGHT -> RIGHT -> RIGHT -> GOAL
Jumlah langkah: 8
```

---

#### Solved Problem 7 ⭐

**Soal:** Mengapa BFS tidak optimal jika step cost berbeda-beda? Berikan contoh!

**Penyelesaian:**

BFS memilih node berdasarkan **kedalaman (level)**, bukan **biaya total**. Jika step cost berbeda, node yang lebih dangkal belum tentu memiliki biaya lebih rendah.

**Contoh:**

![Graf dengan Biaya Berbeda](images/p02-07-weighted-graph-example.png)

*Gambar 2.8: Graf dengan biaya edge berbeda*

- **BFS path:** Start → A → Goal (total cost = 10 + 1 = 11)
- **Optimal path:** Start → B → Goal (total cost = 5 + 5 = 10)

BFS menemukan path via A terlebih dahulu karena path tersebut lebih *dangkal* (2 edge vs tetap 2 edge, tapi BFS tidak melihat cost, hanya urutan masuk queue).

Untuk kasus dengan step cost berbeda, kita memerlukan **Uniform-Cost Search (UCS)** yang akan dibahas di bagian 7.

---

## 6. Depth-First Search (DFS)

### 6.1 Konsep DFS

> **Definisi: Depth-First Search (DFS)**  
> DFS adalah strategi pencarian yang selalu mengeksplorasi node terdalam di frontier terlebih dahulu. Implementasi menggunakan **stack (LIFO)** atau rekursi untuk frontier.

**Karakteristik:**
- Eksplorasi mendalam dulu (*deep before wide*)
- Menggunakan stack atau rekursi
- Memori lebih hemat dibanding BFS
- Tidak complete dan tidak optimal dalam bentuk standar

### 6.2 Algoritma DFS

```python
def depth_first_search(problem):
    """
    Implementasi Depth-First Search
    
    Args:
        problem: objek problem dengan interface standar
    
    Returns:
        path: list of actions menuju goal, atau None jika tidak ditemukan
    """
    # Inisialisasi
    node = Node(problem.initial_state)
    
    # Frontier menggunakan stack (LIFO)
    frontier = Stack()
    frontier.push(node)
    
    # Explored set
    explored = set()
    
    while not frontier.is_empty():
        # Pop dari stack (node terdalam)
        node = frontier.pop()
        
        # Goal test
        if problem.goal_test(node.state):
            return node.path()
        
        explored.add(node.state)
        
        # Expand dan push child ke stack
        for action in problem.actions(node.state):
            child = node.child(problem, action)
            if child.state not in explored and child not in frontier:
                frontier.push(child)
    
    return None
```

### 6.3 Visualisasi Ekspansi DFS

![DFS Expansion](images/p02-07-dfs-expansion.png)

*Gambar 2.9: Urutan ekspansi node pada DFS - selalu menelusuri cabang terdalam*

### 6.4 Analisis Kompleksitas DFS

| Kriteria | DFS |
|----------|-----|
| **Complete?** | Tidak (bisa stuck di infinite loop atau path tak terbatas) |
| **Optimal?** | Tidak (bisa menemukan solusi lebih dalam padahal ada solusi dangkal) |
| **Time Complexity** | O(b^m) - bisa sangat buruk jika m >> d |
| **Space Complexity** | O(bm) - linear terhadap kedalaman! |

**Keunggulan utama DFS:** Space complexity jauh lebih baik dari BFS!
- BFS: O(b^d) ≈ menyimpan seluruh level
- DFS: O(bm) ≈ menyimpan satu path + siblings

---

#### Solved Problem 8 ⭐⭐

**Soal:** Terapkan DFS pada graf yang sama dengan Solved Problem 5. Bandingkan hasilnya!

```
    S --- A --- B
    |     |     |
    C --- D --- G
```
(Asumsi: eksplorasi alfabetis, S adalah start, G adalah goal)

**Penyelesaian:**

| Iterasi | Node Diproses | Stack (setelah ekspansi) | Explored |
|---------|---------------|--------------------------|----------|
| 0 | - | [S] | {} |
| 1 | S | [C, A] | {S} |
| 2 | A | [C, D, B] | {S, A} |
| 3 | B | [C, D, G] | {S, A, B} |
| 4 | G | **GOAL FOUND!** | {S, A, B, G} |

**Jalur yang ditemukan:** S → A → B → G

**Perbandingan:**
| Aspek | BFS | DFS |
|-------|-----|-----|
| Node di-expand | 6 | 4 |
| Jalur ditemukan | S→A→B→G atau S→C→D→G | S→A→B→G |
| Memori maksimal | 4 nodes | 4 nodes |

**Catatan:** Dalam contoh ini DFS kebetulan lebih efisien, tetapi ini tidak selalu terjadi. DFS bisa sangat buruk jika terjebak di cabang yang panjang dan salah.

---

#### Solved Problem 9 ⭐

**Soal:** Berikan contoh situasi di mana DFS gagal menemukan solusi padahal solusi ada!

**Penyelesaian:**

**Situasi 1: Infinite Path**
```
    A ←→ B ←→ C
    ↑
    |
    D (Goal)
```

Jika DFS pertama kali memilih path A → B → C → B → C → B ... (loop), algoritma tidak akan pernah mencapai D. 

**Situasi 2: State Space Tak Terbatas**

Contoh: Mencari bilangan bulat x sehingga x² = 100
- State space: {..., -3, -2, -1, 0, 1, 2, 3, ...}
- Jika DFS memilih arah negatif: -1, -2, -3, ...
- DFS tidak akan menemukan x = 10 atau x = -10

**Solusi:** Gunakan variasi DFS seperti **Depth-Limited Search** atau **Iterative Deepening**.

---

### 6.5 Variasi DFS: Depth-Limited Search

> **Definisi: Depth-Limited Search (DLS)**  
> DLS adalah DFS dengan batasan kedalaman maksimal L. Node pada kedalaman L tidak akan di-expand.

```python
def depth_limited_search(problem, limit):
    """
    DFS dengan batas kedalaman
    
    Returns:
        'cutoff' jika limit tercapai tanpa menemukan goal
        'failure' jika tidak ada solusi
        solution path jika goal ditemukan
    """
    return recursive_dls(Node(problem.initial_state), problem, limit)

def recursive_dls(node, problem, limit):
    if problem.goal_test(node.state):
        return node.path()
    elif limit == 0:
        return 'cutoff'  # Batas tercapai
    else:
        cutoff_occurred = False
        for action in problem.actions(node.state):
            child = node.child(problem, action)
            result = recursive_dls(child, problem, limit - 1)
            if result == 'cutoff':
                cutoff_occurred = True
            elif result != 'failure':
                return result
        return 'cutoff' if cutoff_occurred else 'failure'
```

**Masalah DLS:** Bagaimana memilih L yang tepat? Jika L terlalu kecil, solusi tidak ditemukan. Jika L terlalu besar, tidak efisien.

### 6.6 Variasi DFS: Iterative Deepening Search (IDS)

> **Definisi: Iterative Deepening Depth-First Search (IDS)**  
> IDS menjalankan DLS secara berulang dengan limit yang meningkat: L=0, L=1, L=2, ... sampai solusi ditemukan.

```python
def iterative_deepening_search(problem):
    """
    Kombinasi keunggulan BFS (complete, optimal untuk uniform cost)
    dengan keunggulan DFS (space efficient)
    """
    depth = 0
    while True:
        result = depth_limited_search(problem, depth)
        if result != 'cutoff':
            return result
        depth += 1
```

![IDS Illustration](images/p02-08-iterative-deepening.png)

*Gambar 2.10: Iterative Deepening Search - menjalankan DLS dengan depth limit meningkat*

**Analisis IDS:**

| Kriteria | IDS |
|----------|-----|
| **Complete?** | Ya (seperti BFS) |
| **Optimal?** | Ya, untuk uniform step cost (seperti BFS) |
| **Time Complexity** | O(b^d) |
| **Space Complexity** | O(bd) - seperti DFS! |

> **Mengapa IDS efisien?**  
> Meskipun node di-generate ulang berkali-kali, overhead-nya kecil karena sebagian besar node berada di level terdalam. Jumlah total node: $(d)b^1 + (d-1)b^2 + ... + (1)b^d = O(b^d)$

---

#### Solved Problem 10 ⭐⭐

**Soal:** Jika branching factor b = 3 dan goal berada di depth d = 3, hitung rasio jumlah node yang di-generate oleh IDS dibanding BFS!

**Penyelesaian:**

**BFS:** Generate semua node sampai level d
$$N_{BFS} = 1 + 3 + 9 + 27 = 40$$

**IDS:** Generate ulang untuk setiap iterasi
- Limit 0: 1 node
- Limit 1: 1 + 3 = 4 nodes
- Limit 2: 1 + 3 + 9 = 13 nodes
- Limit 3: 1 + 3 + 9 + 27 = 40 nodes

$$N_{IDS} = 1 + 4 + 13 + 40 = 58$$

**Rasio:** $\frac{N_{IDS}}{N_{BFS}} = \frac{58}{40} = 1.45$

**Interpretasi:** IDS hanya membutuhkan 45% lebih banyak node generation dibanding BFS, tetapi dengan space complexity jauh lebih kecil (O(bd) vs O(b^d)).

---

#### Solved Problem 11 ⭐⭐⭐

**Soal:** Implementasikan IDS dalam C++ untuk menyelesaikan 8-puzzle!

**Penyelesaian:**

```cpp
#include <iostream>
#include <vector>
#include <array>
#include <set>
using namespace std;

// State direpresentasikan sebagai array 9 elemen (0 = blank)
typedef array<int, 9> PuzzleState;

struct Node {
    PuzzleState state;
    Node* parent;
    string action;
    int depth;
    
    Node(PuzzleState s, Node* p = nullptr, string a = "", int d = 0)
        : state(s), parent(p), action(a), depth(d) {}
};

class EightPuzzle {
public:
    PuzzleState initial;
    PuzzleState goal = {1, 2, 3, 4, 5, 6, 7, 8, 0};
    
    // Posisi blank: 4 arah gerakan (up, down, left, right)
    // Swap blank dengan tile di arah tersebut
    vector<pair<string, PuzzleState>> successors(PuzzleState& state) {
        vector<pair<string, PuzzleState>> result;
        
        // Cari posisi blank (0)
        int blank_pos = 0;
        for (int i = 0; i < 9; i++) {
            if (state[i] == 0) {
                blank_pos = i;
                break;
            }
        }
        
        int row = blank_pos / 3;
        int col = blank_pos % 3;
        
        // Try each direction
        // UP: swap with position above
        if (row > 0) {
            PuzzleState new_state = state;
            swap(new_state[blank_pos], new_state[blank_pos - 3]);
            result.push_back({"UP", new_state});
        }
        // DOWN
        if (row < 2) {
            PuzzleState new_state = state;
            swap(new_state[blank_pos], new_state[blank_pos + 3]);
            result.push_back({"DOWN", new_state});
        }
        // LEFT
        if (col > 0) {
            PuzzleState new_state = state;
            swap(new_state[blank_pos], new_state[blank_pos - 1]);
            result.push_back({"LEFT", new_state});
        }
        // RIGHT
        if (col < 2) {
            PuzzleState new_state = state;
            swap(new_state[blank_pos], new_state[blank_pos + 1]);
            result.push_back({"RIGHT", new_state});
        }
        
        return result;
    }
    
    bool goal_test(PuzzleState& state) {
        return state == goal;
    }
};

// Recursive Depth-Limited Search
string recursive_dls(Node* node, EightPuzzle& problem, int limit,
                     set<PuzzleState>& path) {
    if (problem.goal_test(node->state)) {
        // Reconstruct solution
        vector<string> actions;
        Node* curr = node;
        while (curr->parent != nullptr) {
            actions.insert(actions.begin(), curr->action);
            curr = curr->parent;
        }
        string solution = "";
        for (auto& a : actions) solution += a + " ";
        return solution;
    }
    
    if (limit == 0) {
        return "cutoff";
    }
    
    bool cutoff_occurred = false;
    path.insert(node->state);
    
    for (auto& [action, next_state] : problem.successors(node->state)) {
        // Avoid cycles in current path
        if (path.find(next_state) != path.end()) continue;
        
        Node* child = new Node(next_state, node, action, node->depth + 1);
        string result = recursive_dls(child, problem, limit - 1, path);
        
        if (result == "cutoff") {
            cutoff_occurred = true;
        } else if (result != "failure") {
            return result;
        }
        delete child;
    }
    
    path.erase(node->state);
    return cutoff_occurred ? "cutoff" : "failure";
}

string iterative_deepening_search(EightPuzzle& problem) {
    for (int depth = 0; depth < 50; depth++) {  // Max depth limit
        cout << "Trying depth limit: " << depth << endl;
        Node* root = new Node(problem.initial);
        set<PuzzleState> path;
        string result = recursive_dls(root, problem, depth, path);
        delete root;
        
        if (result != "cutoff" && result != "failure") {
            return result;
        }
    }
    return "failure";
}

int main() {
    EightPuzzle puzzle;
    // Initial state (mudah - hanya butuh beberapa langkah)
    puzzle.initial = {1, 2, 3, 4, 0, 6, 7, 5, 8};
    
    cout << "Solving 8-puzzle with IDS..." << endl;
    cout << "Initial: ";
    for (int i : puzzle.initial) cout << i << " ";
    cout << endl;
    
    string solution = iterative_deepening_search(puzzle);
    
    if (solution != "failure") {
        cout << "Solution found: " << solution << endl;
    } else {
        cout << "No solution found!" << endl;
    }
    
    return 0;
}
```

**Output (untuk initial state sederhana):**
```
Solving 8-puzzle with IDS...
Initial: 1 2 3 4 0 6 7 5 8
Trying depth limit: 0
Trying depth limit: 1
Trying depth limit: 2
Solution found: DOWN RIGHT
```

---

## 7. Uniform-Cost Search (UCS)

### 7.1 Konsep UCS

> **Definisi: Uniform-Cost Search (UCS)**  
> UCS adalah strategi pencarian yang selalu mengeksplorasi node dengan **path cost terendah** terlebih dahulu. Implementasi menggunakan **priority queue** dengan priority = g(n), di mana g(n) adalah total cost dari initial state ke node n.

**Mengapa UCS dibutuhkan?**
- BFS optimal hanya untuk uniform step cost
- Jika step cost bervariasi, kita butuh algoritma yang memperhitungkan biaya

### 7.2 Algoritma UCS

```python
def uniform_cost_search(problem):
    """
    Pencarian dengan prioritas biaya terendah
    
    Args:
        problem: objek problem dengan step_cost(state, action, next_state)
    
    Returns:
        path ke goal dengan biaya minimum
    """
    node = Node(problem.initial_state, path_cost=0)
    
    # Priority queue dengan priority = path_cost
    frontier = PriorityQueue()
    frontier.push(node, priority=node.path_cost)
    
    explored = set()
    
    while not frontier.is_empty():
        node = frontier.pop()  # Node dengan cost terendah
        
        # Goal test saat expansion (bukan saat generation!)
        if problem.goal_test(node.state):
            return node.path()
        
        explored.add(node.state)
        
        for action in problem.actions(node.state):
            child = node.child(problem, action)
            child.path_cost = node.path_cost + problem.step_cost(
                node.state, action, child.state)
            
            if child.state not in explored:
                # Cek apakah state sudah di frontier dengan cost lebih tinggi
                existing = frontier.find(child.state)
                if existing is None:
                    frontier.push(child, priority=child.path_cost)
                elif child.path_cost < existing.path_cost:
                    frontier.replace(existing, child)
    
    return None
```

### 7.3 Visualisasi UCS

![UCS Expansion](images/p02-09-ucs-expansion.png)

*Gambar 2.11: UCS mengeksplorasi berdasarkan total path cost, bukan kedalaman*

### 7.4 Perbedaan Penting: Goal Test pada UCS

> **Kritis:** Pada UCS, **goal test dilakukan saat node di-expand (dikeluarkan dari frontier)**, bukan saat node di-generate (dimasukkan ke frontier).

**Alasan:** Node dengan path cost lebih rendah bisa saja muncul kemudian. Jika kita melakukan goal test saat generation, kita bisa menemukan goal dengan path cost yang bukan minimum.

### 7.5 Analisis Kompleksitas UCS

| Kriteria | UCS |
|----------|-----|
| **Complete?** | Ya, jika step cost ≥ ε untuk ε > 0 |
| **Optimal?** | Ya! |
| **Time Complexity** | O(b^(1+⌊C*/ε⌋)) ≈ O(b^(C*/ε)) |
| **Space Complexity** | O(b^(1+⌊C*/ε⌋)) |

Di mana:
- C* = biaya solusi optimal
- ε = step cost minimum

**Catatan:** Jika semua step cost sama, UCS berperilaku identik dengan BFS.

---

#### Solved Problem 12 ⭐⭐

**Soal:** Terapkan UCS untuk mencari jalur dari S ke G pada graf berikut. Tunjukkan isi priority queue di setiap langkah!

```
       2       4
    S ---- A ---- G
    |             ^
    1             |
    |      3      |
    B ---- C -----+
              2
```

**Penyelesaian:**

| Iterasi | Pop Node | g(n) | Priority Queue (setelah ekspansi) |
|---------|----------|------|-----------------------------------|
| 0 | - | - | [(S, 0)] |
| 1 | S | 0 | [(B, 1), (A, 2)] |
| 2 | B | 1 | [(A, 2), (C, 4)] |
| 3 | A | 2 | [(C, 4), (G, 6)] |
| 4 | C | 4 | [(G, 6)] *note: path S→B→C→G = 1+3+2 = 6, sama* |
| 5 | G | 6 | **GOAL! Path cost = 6** |

**Jalur optimal:** S → A → G dengan total cost = 2 + 4 = 6  
(atau S → B → C → G dengan cost = 1 + 3 + 2 = 6)

**Kedua jalur memiliki cost yang sama!** UCS menjamin menemukan salah satu jalur optimal.

---

#### Solved Problem 13 ⭐⭐⭐

**Soal:** Dalam konteks operasi militer, sebuah unit harus bergerak dari Pos Komando (PK) ke Sasaran (S). Tersedia beberapa rute dengan tingkat risiko berbeda yang direpresentasikan sebagai "biaya" perjalanan. Implementasikan UCS untuk menemukan rute dengan risiko total minimum!

```
Pos Komando (PK)
    |
    | risiko: 3
    v
   (A) --- risiko: 2 --- (B)
    |                     |
risiko: 4            risiko: 1
    |                     |
    v                     v
   (C) --- risiko: 2 --- (S) Sasaran
```

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <map>
#include <set>
using namespace std;

struct Node {
    string state;
    int path_cost;
    vector<string> path;
    
    // Untuk priority queue (min-heap)
    bool operator>(const Node& other) const {
        return path_cost > other.path_cost;
    }
};

map<string, vector<pair<string, int>>> graph = {
    {"PK", {{"A", 3}}},
    {"A", {{"B", 2}, {"C", 4}}},
    {"B", {{"S", 1}}},
    {"C", {{"S", 2}}}
};

Node uniform_cost_search(string start, string goal) {
    // Priority queue (min-heap)
    priority_queue<Node, vector<Node>, greater<Node>> frontier;
    
    // Node awal
    Node initial;
    initial.state = start;
    initial.path_cost = 0;
    initial.path = {start};
    frontier.push(initial);
    
    set<string> explored;
    
    while (!frontier.empty()) {
        // Pop node dengan cost terendah
        Node current = frontier.top();
        frontier.pop();
        
        // Goal test saat expansion
        if (current.state == goal) {
            return current;
        }
        
        // Skip jika sudah dieksplor
        if (explored.count(current.state)) continue;
        explored.insert(current.state);
        
        // Expand
        for (auto& [next_state, risk] : graph[current.state]) {
            if (!explored.count(next_state)) {
                Node child;
                child.state = next_state;
                child.path_cost = current.path_cost + risk;
                child.path = current.path;
                child.path.push_back(next_state);
                frontier.push(child);
            }
        }
    }
    
    return Node(); // Tidak ditemukan
}

int main() {
    cout << "=== PERENCANAAN RUTE OPERASI MILITER ===" << endl;
    cout << "Mencari rute dengan risiko minimum dari PK ke S" << endl;
    cout << endl;
    
    Node result = uniform_cost_search("PK", "S");
    
    cout << "Rute optimal ditemukan:" << endl;
    cout << "Path: ";
    for (int i = 0; i < result.path.size(); i++) {
        cout << result.path[i];
        if (i < result.path.size() - 1) cout << " -> ";
    }
    cout << endl;
    cout << "Total risiko: " << result.path_cost << endl;
    
    return 0;
}
```

**Output:**
```
=== PERENCANAAN RUTE OPERASI MILITER ===
Mencari rute dengan risiko minimum dari PK ke S

Rute optimal ditemukan:
Path: PK -> A -> B -> S
Total risiko: 6
```

**Analisis Jalur:**
- PK → A → B → S: 3 + 2 + 1 = **6** ✓ (Optimal)
- PK → A → C → S: 3 + 4 + 2 = **9**

---

#### Solved Problem 14 ⭐

**Soal:** Kapan UCS berperilaku sama dengan BFS?

**Penyelesaian:**

UCS berperilaku identik dengan BFS ketika:

1. **Semua step cost sama** (uniform cost)
   - Jika setiap edge memiliki cost = 1, maka g(n) = depth(n)
   - Priority queue akan mengembalikan node berdasarkan depth

2. **Secara matematis:**
   - BFS mengeksplorasi berdasarkan level (depth)
   - UCS mengeksplorasi berdasarkan g(n) = total cost
   - Jika cost(action) = c untuk semua action, maka g(n) = c × depth(n)
   - Urutan eksplorasi akan sama

**Contoh:**
```
Semua edge cost = 1:
BFS level 0: {A}
BFS level 1: {B, C}  
BFS level 2: {D, E, F}

UCS g=0: {A}
UCS g=1: {B, C}
UCS g=2: {D, E, F}
```

---

## 8. Perbandingan Algoritma Uninformed Search

### 8.1 Tabel Perbandingan Lengkap

| Kriteria | BFS | DFS | DLS | IDS | UCS |
|----------|-----|-----|-----|-----|-----|
| **Complete?** | Ya* | Tidak | Tidak | Ya* | Ya** |
| **Optimal?** | Ya*** | Tidak | Tidak | Ya*** | Ya |
| **Time** | O(b^d) | O(b^m) | O(b^L) | O(b^d) | O(b^(1+C*/ε)) |
| **Space** | O(b^d) | O(bm) | O(bL) | O(bd) | O(b^(1+C*/ε)) |

**Keterangan:**
- \* Jika b terbatas
- \** Jika b terbatas dan step cost ≥ ε > 0
- \*** Jika semua step cost sama

### 8.2 Panduan Pemilihan Algoritma

![Flowchart Pemilihan Algoritma](images/p02-10-flowchart-pemilihan.png)

*Gambar 2.12: Panduan pemilihan algoritma uninformed search*

**Rekomendasi Praktis:**

| Situasi | Rekomendasi | Alasan |
|---------|-------------|--------|
| Step cost bervariasi | **UCS** | Menjamin solusi optimal |
| Memori sangat terbatas | **IDS** | Space O(bd), tetap complete |
| Perlu solusi tercepat | **BFS** atau **IDS** | Menemukan solusi terdangkal |
| State space sangat besar/infinite | **IDS** | Complete dengan memori efisien |
| Solusi diketahui dalam | **DFS** | Memori efisien |

---

#### Solved Problem 15 ⭐⭐

**Soal:** Sebuah sistem navigasi drone militer harus memilih algoritma pencarian. Tentukan algoritma yang tepat untuk setiap skenario:

a) Mencari rute dengan konsumsi bahan bakar minimum
b) Mencari rute tercepat (semua segmen memiliki waktu tempuh sama)
c) Sistem embedded dengan memori 512KB
d) Pencarian dalam ruang 3D yang sangat luas

**Penyelesaian:**

| Skenario | Algoritma | Alasan |
|----------|-----------|--------|
| (a) Konsumsi BBM minimum | **UCS** | Step cost berbeda (konsumsi BBM tergantung jarak dan medan) |
| (b) Rute tercepat, waktu seragam | **BFS** atau **IDS** | Uniform cost, keduanya optimal |
| (c) Memori 512KB | **IDS** | Space complexity O(bd) paling efisien |
| (d) Ruang 3D luas | **IDS** | Complete meski state space besar, memori efisien |

---

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Analisis kompleksitas untuk masalah berikut:
- Branching factor b = 4
- Goal depth d = 5
- Maximum depth m = 10
- Minimum step cost ε = 1
- Optimal solution cost C* = 5

Hitung estimasi jumlah node yang di-generate untuk setiap algoritma!

**Penyelesaian:**

**1. BFS:**
$$N_{BFS} = \sum_{i=0}^{d} b^i = \frac{b^{d+1} - 1}{b - 1} = \frac{4^6 - 1}{3} = \frac{4095}{3} = 1365$$

**2. DFS (worst case):**
$$N_{DFS} = b^m = 4^{10} = 1,048,576$$

**3. IDS:**
$$N_{IDS} = db^1 + (d-1)b^2 + ... + 1 \cdot b^d$$
$$= 5(4) + 4(16) + 3(64) + 2(256) + 1(1024)$$
$$= 20 + 64 + 192 + 512 + 1024 = 1812$$

**4. UCS:** (karena ε = 1 dan C* = 5, sama dengan d = 5)
$$N_{UCS} \approx b^{1+\lfloor C*/\varepsilon \rfloor} = 4^{6} = 4096$$

| Algoritma | Node Generated | Rasio vs BFS |
|-----------|----------------|--------------|
| BFS | 1,365 | 1.00× |
| IDS | 1,812 | 1.33× |
| UCS | 4,096 | 3.00× |
| DFS | 1,048,576 | 768× |

**Kesimpulan:** BFS paling efisien untuk kasus ini, tetapi membutuhkan memori O(b^d) = O(1024) node. IDS hanya membutuhkan memori O(bd) = O(20) node dengan overhead 33%.

---

#### Solved Problem 17 ⭐

**Soal:** Jelaskan mengapa DFS bisa sangat buruk dalam kasus worst case!

**Penyelesaian:**

DFS bisa sangat buruk karena:

1. **Tidak melihat kedalaman goal:** DFS terus menelusuri cabang terdalam meskipun goal ada di dekat root.

2. **Contoh worst case:**
```
        Root
       /    \
      A      Goal (d=1)
     /
    B
   /
  C
 /
... (depth m = 1000)
```

- BFS menemukan Goal di iterasi ke-2 (setelah expand Root)
- DFS bisa mengeksplorasi seluruh cabang kiri (1000+ node) sebelum menemukan Goal

3. **Infinite loops:** Tanpa graph search, DFS bisa terjebak dalam loop: A → B → A → B → ...

4. **Space tidak menjadi keuntungan jika m besar:**
   - DFS space: O(bm) = O(4 × 1000) = O(4000)
   - Masih lebih baik dari BFS O(b^d), tapi waktu O(b^m) sangat buruk

---

#### Solved Problem 18 ⭐⭐

**Soal:** Implementasikan ketiga algoritma (BFS, DFS, UCS) untuk graf yang sama dan bandingkan hasilnya!

**Graf:**
```
    A ---(3)--- B ---(2)--- E
    |          |           |
   (1)        (4)         (1)
    |          |           |
    C ---(2)--- D ---(3)--- F (Goal)
```

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <stack>
#include <vector>
#include <set>
#include <map>
using namespace std;

// Graf dengan adjacency list
map<char, vector<pair<char, int>>> graph = {
    {'A', {{'B', 3}, {'C', 1}}},
    {'B', {{'A', 3}, {'D', 4}, {'E', 2}}},
    {'C', {{'A', 1}, {'D', 2}}},
    {'D', {{'B', 4}, {'C', 2}, {'F', 3}}},
    {'E', {{'B', 2}, {'F', 1}}},
    {'F', {}}  // Goal
};

// BFS
pair<string, int> bfs(char start, char goal) {
    queue<pair<char, string>> frontier;  // (state, path)
    set<char> explored;
    
    frontier.push({start, string(1, start)});
    int nodes_expanded = 0;
    
    while (!frontier.empty()) {
        auto [state, path] = frontier.front();
        frontier.pop();
        
        if (state == goal) {
            return {path, nodes_expanded};
        }
        
        if (explored.count(state)) continue;
        explored.insert(state);
        nodes_expanded++;
        
        for (auto& [next, cost] : graph[state]) {
            if (!explored.count(next)) {
                frontier.push({next, path + "->" + next});
            }
        }
    }
    return {"Not found", nodes_expanded};
}

// DFS
pair<string, int> dfs(char start, char goal) {
    stack<pair<char, string>> frontier;
    set<char> explored;
    
    frontier.push({start, string(1, start)});
    int nodes_expanded = 0;
    
    while (!frontier.empty()) {
        auto [state, path] = frontier.top();
        frontier.pop();
        
        if (state == goal) {
            return {path, nodes_expanded};
        }
        
        if (explored.count(state)) continue;
        explored.insert(state);
        nodes_expanded++;
        
        for (auto& [next, cost] : graph[state]) {
            if (!explored.count(next)) {
                frontier.push({next, path + "->" + next});
            }
        }
    }
    return {"Not found", nodes_expanded};
}

// UCS
pair<string, int> ucs(char start, char goal) {
    // Priority queue: (cost, state, path)
    priority_queue<tuple<int, char, string>, 
                   vector<tuple<int, char, string>>,
                   greater<tuple<int, char, string>>> frontier;
    set<char> explored;
    
    frontier.push({0, start, string(1, start)});
    int nodes_expanded = 0;
    
    while (!frontier.empty()) {
        auto [cost, state, path] = frontier.top();
        frontier.pop();
        
        if (state == goal) {
            return {path + " (cost=" + to_string(cost) + ")", nodes_expanded};
        }
        
        if (explored.count(state)) continue;
        explored.insert(state);
        nodes_expanded++;
        
        for (auto& [next, step_cost] : graph[state]) {
            if (!explored.count(next)) {
                frontier.push({cost + step_cost, next, path + "->" + next});
            }
        }
    }
    return {"Not found", nodes_expanded};
}

int main() {
    cout << "=== Perbandingan Algoritma Pencarian ===" << endl;
    cout << "Start: A, Goal: F" << endl << endl;
    
    auto [bfs_path, bfs_exp] = bfs('A', 'F');
    cout << "BFS: " << bfs_path << " (expanded: " << bfs_exp << ")" << endl;
    
    auto [dfs_path, dfs_exp] = dfs('A', 'F');
    cout << "DFS: " << dfs_path << " (expanded: " << dfs_exp << ")" << endl;
    
    auto [ucs_path, ucs_exp] = ucs('A', 'F');
    cout << "UCS: " << ucs_path << " (expanded: " << ucs_exp << ")" << endl;
    
    return 0;
}
```

**Output:**
```
=== Perbandingan Algoritma Pencarian ===
Start: A, Goal: F

BFS: A->C->D->F (expanded: 4)
DFS: A->B->E->F (expanded: 4)
UCS: A->B->E->F (cost=6) (expanded: 5)
```

**Analisis:**
| Algoritma | Path | Cost | Nodes Expanded |
|-----------|------|------|----------------|
| BFS | A→C→D→F | 1+2+3=6 | 4 |
| DFS | A→B→E→F | 3+2+1=6 | 4 |
| UCS | A→B→E→F | 3+2+1=6 | 5 |

Dalam kasus ini, kebetulan semua path yang ditemukan memiliki cost yang sama. UCS memeriksa lebih banyak node untuk memastikan optimalitas.

---

#### Solved Problem 19 ⭐⭐

**Soal:** Buktikan bahwa UCS adalah complete dan optimal!

**Penyelesaian:**

**Pembuktian Completeness:**

1. **Asumsi:** Branching factor b terbatas, step cost ≥ ε > 0 untuk semua langkah

2. **Lemma:** Untuk setiap nilai cost c, hanya ada sejumlah terbatas node dengan g(n) ≤ c
   - Karena setiap langkah menambah minimal ε ke cost
   - Maksimal c/ε langkah untuk mencapai cost c
   - Dengan b terbatas, jumlah node = O(b^(c/ε))

3. **Argumen:** Jika solusi dengan cost C* ada:
   - UCS akan mengeksplorasi semua node dengan g(n) < C* terlebih dahulu
   - Karena jumlahnya terbatas, pasti akan sampai ke node goal
   
∴ **UCS complete** jika b terbatas dan ε > 0.

**Pembuktian Optimality:**

1. **Invariant:** UCS selalu mengeksplorasi node dalam urutan g(n) yang tidak menurun

2. **Argumen:**
   - Misalkan n* adalah goal node dengan cost optimal C*
   - Misalkan n' adalah goal node lain dengan cost C' > C*
   - Karena UCS mengeksplorasi berdasarkan g(n) urut naik
   - n* akan di-explore sebelum n'
   - Ketika n* di-explore, goal test sukses dan UCS berhenti

3. **Kasus frontier:** Jika ada node goal di frontier:
   - Node dengan g(n) terendah diproses dulu
   - Jika goal dengan cost C' > C* di frontier, node dengan cost < C' diproses dulu
   - Termasuk semua ancestor dari n* yang memiliki cost < C*

∴ **UCS optimal** karena selalu menemukan goal dengan cost minimum.

---

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Sebuah sistem Command and Control (C2) militer perlu merencanakan misi pengintaian drone. Drone harus mengunjungi 4 checkpoint dalam urutan tertentu. Setiap transisi memiliki "biaya misi" yang mencakup jarak, risiko deteksi, dan konsumsi energi. Formulasikan sebagai problem pencarian dan tentukan algoritma terbaik!

**Data:**
- Checkpoint: Base (B), Alpha (A), Bravo (V), Charlie (C), Delta (D)
- Urutan wajib: B → ? → ? → ? → B (kembali ke base)
- Harus mengunjungi A, V, C, D tepat sekali

**Penyelesaian:**

**Formulasi Problem:**

| Komponen | Deskripsi |
|----------|-----------|
| **State** | (lokasi_saat_ini, {checkpoint_dikunjungi}) |
| **Initial State** | (B, {}) |
| **Goal Test** | lokasi = B dan {A, V, C, D} ⊆ dikunjungi |
| **Actions** | Terbang ke checkpoint yang belum dikunjungi, atau kembali ke B jika semua sudah dikunjungi |
| **Path Cost** | Jumlah biaya misi semua transisi |

**State Space:**
- Initial: (B, {}) — 1 state
- Setelah 1 move: (A, {A}), (V, {V}), (C, {C}), (D, {D}) — 4 states
- Setelah 2 moves: 4 × 3 = 12 states
- Setelah 3 moves: 12 × 2 = 24 states
- Setelah 4 moves: 24 × 1 = 24 states
- Return to base: 24 states goal candidates

**Total: 1 + 4 + 12 + 24 + 24 = 65 reachable states**

**Algoritma Terbaik: UCS**

Alasan:
1. Biaya misi bervariasi antar transisi
2. Perlu solusi optimal (misi dengan biaya minimum)
3. State space cukup kecil (65 states), kompleksitas UCS manageable
4. Memori bukan constraint kritis untuk sistem C2

```cpp
// Pseudocode untuk planner drone
struct MissionState {
    char location;
    set<char> visited;
    int total_cost;
    vector<char> path;
    
    bool operator>(const MissionState& other) const {
        return total_cost > other.total_cost;
    }
};

MissionState plan_mission() {
    priority_queue<MissionState, vector<MissionState>, 
                   greater<MissionState>> frontier;
    
    MissionState initial = {'B', {}, 0, {'B'}};
    frontier.push(initial);
    
    while (!frontier.empty()) {
        MissionState current = frontier.top();
        frontier.pop();
        
        // Goal test: back at base with all visited
        if (current.location == 'B' && 
            current.visited.size() == 4) {
            return current;  // Optimal mission plan
        }
        
        // Generate successors
        for (char checkpoint : {'A', 'V', 'C', 'D', 'B'}) {
            if (checkpoint == 'B') {
                // Can return to base only if all visited
                if (current.visited.size() == 4) {
                    MissionState next = current;
                    next.location = 'B';
                    next.total_cost += mission_cost(current.location, 'B');
                    next.path.push_back('B');
                    frontier.push(next);
                }
            } else if (current.visited.find(checkpoint) == 
                       current.visited.end()) {
                MissionState next = current;
                next.location = checkpoint;
                next.visited.insert(checkpoint);
                next.total_cost += mission_cost(current.location, checkpoint);
                next.path.push_back(checkpoint);
                frontier.push(next);
            }
        }
    }
    
    return MissionState();  // No solution
}
```

---

#### Solved Problem 21 ⭐⭐

**Soal:** Modifikasi algoritma BFS untuk menghitung dan menyimpan jumlah langkah ke setiap node yang ditemukan!

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <map>
#include <vector>
using namespace std;

// BFS dengan tracking depth/langkah ke setiap node
map<char, int> bfs_with_depth(
    map<char, vector<char>>& graph, 
    char start
) {
    map<char, int> depth;  // depth[node] = jumlah langkah dari start
    queue<char> frontier;
    
    frontier.push(start);
    depth[start] = 0;
    
    while (!frontier.empty()) {
        char current = frontier.front();
        frontier.pop();
        
        for (char neighbor : graph[current]) {
            if (depth.find(neighbor) == depth.end()) {
                depth[neighbor] = depth[current] + 1;
                frontier.push(neighbor);
            }
        }
    }
    
    return depth;
}

int main() {
    map<char, vector<char>> graph = {
        {'A', {'B', 'C'}},
        {'B', {'A', 'D', 'E'}},
        {'C', {'A', 'F'}},
        {'D', {'B'}},
        {'E', {'B', 'F'}},
        {'F', {'C', 'E'}}
    };
    
    map<char, int> distances = bfs_with_depth(graph, 'A');
    
    cout << "Jarak (jumlah langkah) dari A ke setiap node:" << endl;
    for (auto& [node, dist] : distances) {
        cout << "  A -> " << node << ": " << dist << " langkah" << endl;
    }
    
    return 0;
}
```

**Output:**
```
Jarak (jumlah langkah) dari A ke setiap node:
  A -> A: 0 langkah
  A -> B: 1 langkah
  A -> C: 1 langkah
  A -> D: 2 langkah
  A -> E: 2 langkah
  A -> F: 2 langkah
```

**Aplikasi:** Teknik ini berguna untuk:
- Menghitung shortest path dalam graf unweighted
- Analisis reachability
- Level-order traversal
- Menentukan diameter graf

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Implementasikan "Bidirectional Search" yang menjalankan BFS dari start dan goal secara bersamaan, berhenti ketika kedua pencarian bertemu!

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <map>
#include <set>
#include <vector>
using namespace std;

// Bidirectional BFS
vector<char> bidirectional_bfs(
    map<char, vector<char>>& graph,
    char start,
    char goal
) {
    if (start == goal) return {start};
    
    // Dua frontier dan dua explored set
    queue<char> frontier_s, frontier_g;  // dari start, dari goal
    map<char, char> parent_s, parent_g;  // untuk rekonstruksi path
    set<char> explored_s, explored_g;
    
    frontier_s.push(start);
    frontier_g.push(goal);
    parent_s[start] = '\0';
    parent_g[goal] = '\0';
    
    while (!frontier_s.empty() && !frontier_g.empty()) {
        // Expand dari sisi start
        char current_s = frontier_s.front();
        frontier_s.pop();
        explored_s.insert(current_s);
        
        for (char neighbor : graph[current_s]) {
            if (explored_s.find(neighbor) == explored_s.end() &&
                parent_s.find(neighbor) == parent_s.end()) {
                parent_s[neighbor] = current_s;
                frontier_s.push(neighbor);
                
                // Cek apakah bertemu dengan pencarian dari goal
                if (explored_g.find(neighbor) != explored_g.end() ||
                    parent_g.find(neighbor) != parent_g.end()) {
                    // Rekonstruksi path
                    vector<char> path;
                    
                    // Path dari start ke meeting point
                    char node = neighbor;
                    while (node != '\0') {
                        path.insert(path.begin(), node);
                        node = parent_s[node];
                    }
                    
                    // Path dari meeting point ke goal
                    node = parent_g[neighbor];
                    while (node != '\0') {
                        path.push_back(node);
                        node = parent_g[node];
                    }
                    
                    return path;
                }
            }
        }
        
        // Expand dari sisi goal (serupa)
        char current_g = frontier_g.front();
        frontier_g.pop();
        explored_g.insert(current_g);
        
        for (char neighbor : graph[current_g]) {
            if (explored_g.find(neighbor) == explored_g.end() &&
                parent_g.find(neighbor) == parent_g.end()) {
                parent_g[neighbor] = current_g;
                frontier_g.push(neighbor);
                
                if (explored_s.find(neighbor) != explored_s.end() ||
                    parent_s.find(neighbor) != parent_s.end()) {
                    // Rekonstruksi path
                    vector<char> path;
                    char node = neighbor;
                    while (node != '\0') {
                        path.insert(path.begin(), node);
                        node = parent_s[node];
                    }
                    node = parent_g[neighbor];
                    while (node != '\0') {
                        path.push_back(node);
                        node = parent_g[node];
                    }
                    return path;
                }
            }
        }
    }
    
    return {};  // Tidak ditemukan
}

int main() {
    // Graf tidak berarah
    map<char, vector<char>> graph = {
        {'A', {'B', 'C'}},
        {'B', {'A', 'D', 'E'}},
        {'C', {'A', 'F', 'G'}},
        {'D', {'B', 'H'}},
        {'E', {'B', 'H'}},
        {'F', {'C', 'I'}},
        {'G', {'C', 'I'}},
        {'H', {'D', 'E', 'J'}},
        {'I', {'F', 'G', 'J'}},
        {'J', {'H', 'I'}}
    };
    
    cout << "Bidirectional BFS dari A ke J:" << endl;
    vector<char> path = bidirectional_bfs(graph, 'A', 'J');
    
    if (!path.empty()) {
        cout << "Path: ";
        for (int i = 0; i < path.size(); i++) {
            cout << path[i];
            if (i < path.size() - 1) cout << " -> ";
        }
        cout << endl;
    } else {
        cout << "Path tidak ditemukan!" << endl;
    }
    
    return 0;
}
```

**Keunggulan Bidirectional Search:**
- Time complexity: O(b^(d/2)) vs O(b^d) untuk BFS standar
- Sangat efektif jika goal state diketahui dan reversible

**Aplikasi:** Navigasi GPS, social network (friend suggestion), game solving.

---

## Supplementary Problems

### Problem S1 ⭐
Formulasikan masalah "Water Jug Problem" (dua ember dengan kapasitas 4 liter dan 3 liter, harus mendapatkan tepat 2 liter) sebagai problem pencarian. Tentukan state space, initial state, goal test, dan actions!

**Jawaban Singkat:**
- State: (volume_ember_4L, volume_ember_3L), contoh (0,0), (4,3)
- Initial: (0, 0)
- Goal: (2, *) atau (*, 2)
- Actions: Isi penuh, Kosongkan, Tuang dari satu ke lain

---

### Problem S2 ⭐⭐
Jika BFS diterapkan pada tree dengan branching factor b=3 dan goal di depth d=4, berapa memory (dalam jumlah node) yang dibutuhkan pada worst case?

**Jawaban Singkat:**
Memory = O(b^d) = 3^4 = **81 nodes** (seluruh level 4 di frontier)

---

### Problem S3 ⭐⭐
Mengapa IDS memiliki overhead waktu yang relatif kecil dibanding BFS meskipun mengulang eksplorasi dari awal setiap iterasi?

**Jawaban Singkat:**
Karena sebagian besar node berada di level terdalam. Node di level d: b^d. Node di level < d: (b^d - 1)/(b-1). Overhead ≈ 1/(b-1) atau ~50% untuk b=2, ~11% untuk b=10.

---

### Problem S4 ⭐⭐
Pada graf dengan cycle, apa yang terjadi jika DFS diimplementasikan tanpa explored set?

**Jawaban Singkat:**
DFS akan terjebak dalam infinite loop, mengunjungi node yang sama berulang kali: A→B→C→A→B→C→... Tidak akan pernah terminasi.

---

### Problem S5 ⭐⭐⭐
Desain sebuah algoritma pencarian yang menggabungkan keunggulan BFS (complete, optimal untuk uniform cost) dan DFS (memory efficient) untuk kasus di mana kita tahu bahwa goal pasti berada di kedalaman antara d_min dan d_max. Jelaskan algoritmanya!

**Jawaban Singkat:**
**Bounded Iterative Deepening:** Mulai DLS dengan limit = d_min, iterasi sampai d_max. Jika tidak ditemukan sampai d_max, return failure. Keunggulan: tidak membuang waktu di kedalaman < d_min, tidak mencari di kedalaman > d_max. Memory: O(b × d_max).

---

## Ringkasan

| Konsep | Deskripsi |
|--------|-----------|
| **Problem Pencarian** | Didefinisikan oleh: State Space, Initial State, Actions, Transition Model, Goal Test, Path Cost |
| **Search Tree** | Representasi pohon dari proses pencarian; root = initial state |
| **Frontier** | Himpunan node yang sudah di-generate tapi belum di-expand |
| **Explored Set** | Himpunan state yang sudah di-expand (untuk menghindari cycle) |
| **BFS** | Eksplorasi per level; Queue (FIFO); Complete & Optimal (uniform cost); O(b^d) time & space |
| **DFS** | Eksplorasi mendalam dulu; Stack (LIFO); Not complete, not optimal; O(bm) space |
| **DLS** | DFS dengan batas kedalaman L |
| **IDS** | DLS berulang dengan L meningkat; Complete & optimal; O(bd) space |
| **UCS** | Eksplorasi berdasarkan g(n) minimum; Priority Queue; Complete & Optimal; O(b^(C*/ε)) |
| **Kriteria Evaluasi** | Completeness, Optimality, Time Complexity, Space Complexity |

### Tabel Perbandingan Final

| Algoritma | Complete | Optimal | Time | Space | Struktur Data |
|-----------|:--------:|:-------:|------|-------|---------------|
| **BFS** | ✓* | ✓** | O(b^d) | O(b^d) | Queue |
| **DFS** | ✗ | ✗ | O(b^m) | O(bm) | Stack/Rekursi |
| **DLS** | ✗ | ✗ | O(b^L) | O(bL) | Stack/Rekursi |
| **IDS** | ✓* | ✓** | O(b^d) | O(bd) | Stack/Rekursi |
| **UCS** | ✓*** | ✓ | O(b^(C*/ε)) | O(b^(C*/ε)) | Priority Queue |

\* jika b terbatas; \** jika step cost uniform; \*** jika step cost ≥ ε > 0

### Langkah Selanjutnya

Di **Pertemuan 3**, kita akan mempelajari **Informed Search (Pencarian Heuristik)** yang menggunakan fungsi heuristik untuk memperkirakan jarak ke goal. Algoritma seperti **Greedy Best-First Search** dan **A*** dapat jauh lebih efisien dari uninformed search untuk banyak masalah praktis.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
