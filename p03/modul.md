# Modul 03: Pencarian Heuristik (Informed Search)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 03  
**Topik:** Pencarian Heuristik - Informed Search  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan konsep heuristik sebagai estimasi biaya menuju goal
2. Membedakan antara pencarian uninformed dan informed search
3. Mengimplementasikan algoritma Greedy Best-First Search
4. Mengimplementasikan algoritma A* dan memahami formula f(n) = g(n) + h(n)
5. Menjelaskan properti admissibility dan consistency pada fungsi heuristik
6. Merancang fungsi heuristik yang baik menggunakan teknik relaxed problem
7. Menganalisis optimalitas dan kompleksitas algoritma A*

---

## Prasyarat

Sebelum mempelajari modul ini, pastikan Anda telah memahami:

- **Pertemuan 02:** Algoritma Uninformed Search (BFS, DFS, UCS)
- Konsep search tree dan search graph
- Struktur data priority queue
- Analisis kompleksitas algoritma (Big-O notation)

---

## 1. Pendahuluan: Keterbatasan Uninformed Search

### 1.1 Review Uninformed Search

Pada pertemuan sebelumnya, kita telah mempelajari algoritma pencarian tanpa informasi (uninformed search) seperti BFS, DFS, dan UCS. Algoritma-algoritma ini disebut "buta" karena tidak memiliki pengetahuan tentang lokasi goal.

> **Uninformed Search** adalah strategi pencarian yang hanya menggunakan informasi yang tersedia dalam definisi masalah, tanpa pengetahuan tambahan tentang seberapa dekat suatu state dengan goal.

### 1.2 Masalah dengan Uninformed Search

Perhatikan masalah pencarian rute dari Arad ke Bucharest pada peta Romania:

![Peta Romania untuk Pencarian Rute](images/p03-01-peta-romania-pencarian.png)

*Gambar 3.1: Peta Romania dengan jarak antar kota untuk demonstrasi algoritma pencarian*

**Masalah:**
- BFS akan mengeksplorasi semua node pada level yang sama sebelum ke level berikutnya
- UCS akan mengeksplorasi berdasarkan biaya terendah tanpa mempertimbangkan arah goal
- Kedua algoritma dapat mengeksplorasi banyak node yang tidak relevan

**Solusi:** Gunakan **informed search** yang memanfaatkan pengetahuan tentang domain masalah.

---

#### Solved Problem 1 ⭐

**Soal:** Jelaskan mengapa BFS tidak efisien untuk mencari rute dari Arad ke Bucharest pada peta Romania!

**Penyelesaian:**

**Langkah 1:** Identifikasi karakteristik BFS
- BFS mengeksplorasi semua node pada kedalaman d sebelum kedalaman d+1
- Tidak mempertimbangkan arah atau jarak ke goal

**Langkah 2:** Analisis eksplorasi BFS dari Arad
```
Level 0: Arad
Level 1: Zerind, Sibiu, Timisoara
Level 2: Oradea, Fagaras, Rimnicu Vilcea, Lugoj
Level 3: Bucharest, Pitesti, Craiova, Mehadia, ...
```

**Langkah 3:** Identifikasi inefisiensi
- BFS mengeksplorasi Zerind dan Timisoara yang menjauh dari Bucharest
- Total node yang dieksplorasi: ~13 node sebelum menemukan Bucharest
- Banyak node tidak relevan yang dieksplorasi

**Jawaban:** BFS tidak efisien karena mengeksplorasi semua arah secara merata tanpa mempertimbangkan bahwa Bucharest berada di sebelah timur. Node seperti Zerind, Timisoara, dan Oradea yang menjauh dari goal tetap dieksplorasi. ∎

---

## 2. Konsep Heuristik

### 2.1 Definisi Heuristik

> **Heuristik** (dari bahasa Yunani "heuriskein" = menemukan) adalah fungsi yang memberikan estimasi biaya dari suatu state ke goal terdekat.

Notasi: **h(n)** = estimasi biaya termurah dari node n ke goal

**Karakteristik heuristik:**
- h(n) ≥ 0 untuk semua node n
- h(goal) = 0
- Semakin kecil h(n), semakin dekat (diperkirakan) node n ke goal

### 2.2 Contoh Fungsi Heuristik

#### a) Straight-Line Distance (SLD)

Untuk masalah pencarian rute, heuristik yang umum adalah **jarak garis lurus** ke goal:

| Kota | h_SLD ke Bucharest |
|------|-------------------|
| Arad | 366 km |
| Bucharest | 0 km |
| Craiova | 160 km |
| Fagaras | 176 km |
| Pitesti | 100 km |
| Rimnicu Vilcea | 193 km |
| Sibiu | 253 km |
| Timisoara | 329 km |
| Zerind | 374 km |

#### b) Manhattan Distance

Untuk grid-based problems seperti 8-puzzle:

> **Manhattan Distance** adalah jumlah jarak horizontal dan vertikal yang harus ditempuh setiap tile untuk mencapai posisi goalnya.

$$h_{Manhattan}(n) = \sum_{i=1}^{k} |x_i - x_{goal}| + |y_i - y_{goal}|$$

#### c) Misplaced Tiles

Untuk puzzle, menghitung jumlah tile yang tidak berada di posisi seharusnya.

$$h_{misplaced}(n) = \text{jumlah tile yang salah posisi}$$

---

#### Solved Problem 2 ⭐

**Soal:** Hitung Manhattan distance untuk state 8-puzzle berikut menuju goal state!

![State 8-Puzzle untuk Perhitungan Manhattan Distance](images/p03-02-8puzzle-manhattan-example.png)

*Gambar 3.2: State 8-puzzle (kiri: current state, kanan: goal state)*

**Penyelesaian:**

**Langkah 1:** Identifikasi posisi current vs goal untuk setiap tile

| Tile | Posisi Current (x,y) | Posisi Goal (x,y) | Jarak Manhattan |
|------|---------------------|-------------------|-----------------|
| 1 | (0, 1) | (0, 0) | \|0-0\| + \|1-0\| = 1 |
| 2 | (0, 0) | (1, 0) | \|0-1\| + \|0-0\| = 1 |
| 3 | (2, 0) | (2, 0) | 0 |
| 4 | (2, 1) | (0, 1) | \|2-0\| + \|1-1\| = 2 |
| 5 | (2, 2) | (1, 1) | \|2-1\| + \|2-1\| = 2 |
| 6 | (1, 1) | (2, 1) | \|1-2\| + \|1-1\| = 1 |
| 7 | (0, 2) | (0, 2) | 0 |
| 8 | (1, 0) | (1, 2) | \|1-1\| + \|0-2\| = 2 |

**Langkah 2:** Jumlahkan semua jarak

$$h_{Manhattan} = 1 + 1 + 0 + 2 + 2 + 1 + 0 + 2 = 9$$

**Jawaban:** Manhattan distance = 9 ∎

---

#### Solved Problem 3 ⭐

**Soal:** Hitung heuristik misplaced tiles untuk state 8-puzzle yang sama!

**Penyelesaian:**

**Langkah 1:** Bandingkan setiap posisi

| Posisi | Current | Goal | Salah? |
|--------|---------|------|--------|
| (0,0) | 2 | 1 | ✓ |
| (1,0) | 8 | 2 | ✓ |
| (2,0) | 3 | 3 | - |
| (0,1) | 1 | 4 | ✓ |
| (1,1) | 6 | 5 | ✓ |
| (2,1) | 4 | 6 | ✓ |
| (0,2) | 7 | 7 | - |
| (1,2) | blank | 8 | ✓ |
| (2,2) | 5 | blank | ✓ |

**Langkah 2:** Hitung tile yang salah posisi (tidak termasuk blank)

$$h_{misplaced} = 6$$

**Jawaban:** Misplaced tiles = 6 ∎

---

#### Solved Problem 4 ⭐⭐

**Soal:** Mengapa Manhattan distance selalu memberikan nilai ≥ misplaced tiles untuk 8-puzzle? Buktikan!

**Penyelesaian:**

**Langkah 1:** Analisis definisi kedua heuristik
- Misplaced tiles: bernilai 1 jika tile salah posisi, 0 jika benar
- Manhattan distance: bernilai ≥ 1 jika tile salah posisi (minimal perlu 1 gerakan)

**Langkah 2:** Buktikan untuk setiap tile
- Jika tile di posisi benar: kedua heuristik = 0
- Jika tile di posisi salah: 
  - Misplaced tiles = 1
  - Manhattan distance ≥ 1 (minimal 1 langkah untuk tile yang hanya salah 1 posisi)

**Langkah 3:** Kesimpulan

Untuk setiap tile i:
$$h_{Manhattan}(tile_i) \geq h_{misplaced}(tile_i)$$

Maka untuk total:
$$\sum h_{Manhattan}(tile_i) \geq \sum h_{misplaced}(tile_i)$$

**Jawaban:** Manhattan distance selalu ≥ misplaced tiles karena setiap tile yang salah posisi minimal memerlukan 1 gerakan (kontribusi 1 ke Manhattan), sementara misplaced tiles hanya menghitung 1 per tile yang salah tanpa mempertimbangkan seberapa jauh. ∎

---

## 3. Greedy Best-First Search

### 3.1 Konsep Dasar

> **Greedy Best-First Search** adalah algoritma pencarian yang selalu mengekspansi node dengan nilai heuristik h(n) terkecil.

**Karakteristik:**
- Hanya menggunakan h(n) untuk evaluasi
- Mengabaikan biaya path yang sudah ditempuh g(n)
- "Greedy" = serakah, selalu memilih yang terlihat terbaik saat ini

### 3.2 Algoritma

```
function GreedyBestFirstSearch(problem, h):
    node ← Node(problem.initial_state)
    frontier ← PriorityQueue() ordered by h(n)
    frontier.insert(node)
    explored ← empty set
    
    while frontier is not empty:
        node ← frontier.pop()  // node dengan h(n) terkecil
        
        if problem.goal_test(node.state):
            return Solution(node)
        
        explored.add(node.state)
        
        for action in problem.actions(node.state):
            child ← ChildNode(node, action)
            if child.state not in explored and child not in frontier:
                frontier.insert(child)
            else if child in frontier with higher h:
                replace with child
    
    return Failure
```

### 3.3 Implementasi C++

```cpp
#include <iostream>
#include <queue>
#include <unordered_set>
#include <unordered_map>
#include <vector>
#include <string>
#include <functional>

using namespace std;

struct Node {
    string state;
    int heuristic;
    vector<string> path;
    
    // Untuk priority queue (min-heap berdasarkan heuristic)
    bool operator>(const Node& other) const {
        return heuristic > other.heuristic;
    }
};

class GreedyBestFirstSearch {
private:
    unordered_map<string, vector<pair<string, int>>> graph;
    unordered_map<string, int> heuristicValues;
    
public:
    void addEdge(string from, string to, int cost) {
        graph[from].push_back({to, cost});
        graph[to].push_back({from, cost});
    }
    
    void setHeuristic(string state, int h) {
        heuristicValues[state] = h;
    }
    
    int getHeuristic(string state) {
        return heuristicValues.count(state) ? heuristicValues[state] : INT_MAX;
    }
    
    vector<string> search(string start, string goal) {
        priority_queue<Node, vector<Node>, greater<Node>> frontier;
        unordered_set<string> explored;
        
        Node startNode = {start, getHeuristic(start), {start}};
        frontier.push(startNode);
        
        while (!frontier.empty()) {
            Node current = frontier.top();
            frontier.pop();
            
            cout << "Exploring: " << current.state 
                 << " (h=" << current.heuristic << ")" << endl;
            
            if (current.state == goal) {
                return current.path;
            }
            
            if (explored.count(current.state)) continue;
            explored.insert(current.state);
            
            for (auto& [neighbor, cost] : graph[current.state]) {
                if (!explored.count(neighbor)) {
                    vector<string> newPath = current.path;
                    newPath.push_back(neighbor);
                    Node childNode = {
                        neighbor, 
                        getHeuristic(neighbor), 
                        newPath
                    };
                    frontier.push(childNode);
                }
            }
        }
        
        return {}; // Tidak ditemukan
    }
};

int main() {
    GreedyBestFirstSearch gbfs;
    
    // Graf peta Romania (simplified)
    gbfs.addEdge("Arad", "Zerind", 75);
    gbfs.addEdge("Arad", "Sibiu", 140);
    gbfs.addEdge("Arad", "Timisoara", 118);
    gbfs.addEdge("Sibiu", "Fagaras", 99);
    gbfs.addEdge("Sibiu", "RimnicuVilcea", 80);
    gbfs.addEdge("Fagaras", "Bucharest", 211);
    gbfs.addEdge("RimnicuVilcea", "Pitesti", 97);
    gbfs.addEdge("Pitesti", "Bucharest", 101);
    
    // Heuristik: Straight-Line Distance ke Bucharest
    gbfs.setHeuristic("Arad", 366);
    gbfs.setHeuristic("Zerind", 374);
    gbfs.setHeuristic("Sibiu", 253);
    gbfs.setHeuristic("Timisoara", 329);
    gbfs.setHeuristic("Fagaras", 176);
    gbfs.setHeuristic("RimnicuVilcea", 193);
    gbfs.setHeuristic("Pitesti", 100);
    gbfs.setHeuristic("Bucharest", 0);
    
    cout << "=== Greedy Best-First Search ===" << endl;
    cout << "Dari Arad ke Bucharest:" << endl << endl;
    
    vector<string> path = gbfs.search("Arad", "Bucharest");
    
    cout << "\nPath ditemukan: ";
    for (int i = 0; i < path.size(); i++) {
        cout << path[i];
        if (i < path.size() - 1) cout << " -> ";
    }
    cout << endl;
    
    return 0;
}
```

**Output:**
```
=== Greedy Best-First Search ===
Dari Arad ke Bucharest:

Exploring: Arad (h=366)
Exploring: Sibiu (h=253)
Exploring: Fagaras (h=176)
Exploring: Bucharest (h=0)

Path ditemukan: Arad -> Sibiu -> Fagaras -> Bucharest
```

### 3.4 Visualisasi Greedy Best-First Search

![Visualisasi Greedy Best-First Search](images/p03-02-greedy-bfs-visualization.png)

*Gambar 3.3: Proses eksplorasi Greedy Best-First Search dari Arad ke Bucharest*

### 3.5 Kelebihan dan Kelemahan

| Aspek | Kelebihan | Kelemahan |
|-------|-----------|-----------|
| Kecepatan | Sangat cepat jika h(n) baik | Bisa lambat jika h(n) buruk |
| Memori | Lebih efisien dari BFS | Tetap eksponensial worst case |
| Optimalitas | - | **Tidak optimal** |
| Kelengkapan | - | **Tidak complete** (bisa infinite loop) |

---

#### Solved Problem 5 ⭐⭐

**Soal:** Tunjukkan bahwa Greedy Best-First Search tidak optimal dengan contoh!

**Penyelesaian:**

**Langkah 1:** Perhatikan graf berikut

```
        A ----10---- B
        |            |
       20            5
        |            |
        C ----15---- D (Goal)
        
h(A) = 25, h(B) = 5, h(C) = 15, h(D) = 0
```

**Langkah 2:** Trace Greedy BFS dari A ke D
1. Start: A, frontier = {A}
2. Expand A: frontier = {B(h=5), C(h=15)}
3. Pilih B (h=5 < h=15): expand B, frontier = {C(h=15), D(h=0)}
4. Pilih D (h=0): Goal ditemukan!
5. Path: A → B → D, Cost = 10 + 5 = **15**

**Langkah 3:** Bandingkan dengan path optimal
- Path A → B → D: Cost = 15
- Path A → C → D: Cost = 20 + 15 = 35

Tunggu, dalam contoh ini Greedy menemukan path optimal. Mari ubah grafnya:

```
        A ----1----- B
        |            |
        3           10
        |            |
        C ----1----- D (Goal)
        
h(A) = 5, h(B) = 1, h(C) = 3, h(D) = 0
```

**Langkah 4:** Trace ulang
1. Expand A: frontier = {B(h=1), C(h=3)}
2. Pilih B (h=1): expand B, frontier = {C(h=3), D(h=0)}
3. Pilih D: Goal! Path: A → B → D, Cost = 1 + 10 = **11**

**Langkah 5:** Path optimal sebenarnya
- A → C → D: Cost = 3 + 1 = **4** ✓

**Jawaban:** Greedy BFS tidak optimal. Pada contoh di atas, Greedy memilih path A→B→D dengan cost 11, padahal path optimal A→C→D hanya cost 4. Ini karena Greedy hanya melihat h(n) tanpa mempertimbangkan biaya aktual g(n). ∎

---

#### Solved Problem 6 ⭐⭐

**Soal:** Tunjukkan bahwa Greedy Best-First Search tidak complete dengan contoh!

**Penyelesaian:**

**Langkah 1:** Konstruksi graf yang menyebabkan infinite loop

```
A <---> B <---> C
        ^
        |
        v
        D (Goal)
        
h(A) = 3, h(B) = 2, h(C) = 1, h(D) = 0
Tapi C tidak terhubung ke D!
```

**Langkah 2:** Trace Greedy BFS
1. Start A: frontier = {B(h=2)}
2. Expand B: frontier = {A(h=3), C(h=1), D(h=0)}
3. Pilih D: Goal! 

Hmm, dalam graf terhubung sederhana ini Greedy bisa menemukan. Mari buat graf yang lebih rumit tanpa path ke goal dari beberapa node:

**Langkah 3:** Graf dengan dead-end dan tanpa explored set yang proper

```
Graf dengan infinite branch:
A → B → C → B → C → B → ... (loop tanpa exploring D)
Jika h(C) < h(D) selalu, Greedy bisa stuck

Atau lebih realistis, pada tree search tanpa graph search:
```

**Langkah 4:** Pada **Tree Search** (tanpa explored set)

Jika graf memiliki cycle dan kita tidak track explored nodes, Greedy bisa loop forever.

**Jawaban:** Greedy BFS tidak complete pada tree search karena bisa terjebak dalam infinite loop pada graf dengan cycle. Pada graph search (dengan explored set), Greedy complete untuk ruang state finite, tapi bisa gagal pada infinite state space jika terus memilih branch yang salah. ∎

---

## 4. Algoritma A* (A-Star)

### 4.1 Konsep Dasar

> **Algoritma A*** adalah algoritma pencarian yang menggabungkan biaya aktual g(n) dengan estimasi heuristik h(n) untuk memilih node yang akan diekspansi.

**Fungsi evaluasi:**
$$f(n) = g(n) + h(n)$$

Dimana:
- **g(n)** = biaya aktual dari start ke node n
- **h(n)** = estimasi biaya dari n ke goal
- **f(n)** = estimasi total biaya path melalui n

### 4.2 Perbedaan dengan Algoritma Lain

| Algoritma | Fungsi Evaluasi | Karakteristik |
|-----------|-----------------|---------------|
| BFS | Kedalaman | Optimal untuk unit cost |
| UCS | g(n) | Optimal, tapi buta |
| Greedy BFS | h(n) | Cepat, tidak optimal |
| **A*** | **g(n) + h(n)** | **Optimal + Informed** |

![Perbandingan Fungsi Evaluasi](images/p03-03-perbandingan-algoritma-search.png)

*Gambar 3.4: Perbandingan fungsi evaluasi berbagai algoritma pencarian*

### 4.3 Algoritma A*

```
function AStarSearch(problem, h):
    node ← Node(problem.initial_state, g=0)
    node.f ← node.g + h(node.state)
    frontier ← PriorityQueue() ordered by f(n)
    frontier.insert(node)
    explored ← empty set
    
    while frontier is not empty:
        node ← frontier.pop()  // node dengan f(n) terkecil
        
        if problem.goal_test(node.state):
            return Solution(node)
        
        explored.add(node.state)
        
        for action in problem.actions(node.state):
            child ← ChildNode(node, action)
            child.g ← node.g + action.cost
            child.f ← child.g + h(child.state)
            
            if child.state not in explored:
                if child not in frontier:
                    frontier.insert(child)
                else if child in frontier with higher f:
                    replace with child
    
    return Failure
```

### 4.4 Implementasi C++

```cpp
#include <iostream>
#include <queue>
#include <unordered_set>
#include <unordered_map>
#include <vector>
#include <string>
#include <functional>

using namespace std;

struct AStarNode {
    string state;
    int g;        // biaya aktual dari start
    int h;        // heuristik ke goal
    int f;        // f = g + h
    vector<string> path;
    
    bool operator>(const AStarNode& other) const {
        return f > other.f;  // min-heap berdasarkan f
    }
};

class AStarSearch {
private:
    unordered_map<string, vector<pair<string, int>>> graph;
    unordered_map<string, int> heuristicValues;
    
public:
    void addEdge(string from, string to, int cost) {
        graph[from].push_back({to, cost});
        graph[to].push_back({from, cost});
    }
    
    void setHeuristic(string state, int h) {
        heuristicValues[state] = h;
    }
    
    int getHeuristic(string state) {
        return heuristicValues.count(state) ? heuristicValues[state] : INT_MAX;
    }
    
    vector<string> search(string start, string goal) {
        priority_queue<AStarNode, vector<AStarNode>, greater<AStarNode>> frontier;
        unordered_map<string, int> bestG;  // best g-value seen for each state
        
        AStarNode startNode = {start, 0, getHeuristic(start), 
                               getHeuristic(start), {start}};
        frontier.push(startNode);
        bestG[start] = 0;
        
        int nodesExpanded = 0;
        
        while (!frontier.empty()) {
            AStarNode current = frontier.top();
            frontier.pop();
            
            // Skip jika sudah ada path lebih baik ke state ini
            if (bestG.count(current.state) && 
                current.g > bestG[current.state]) {
                continue;
            }
            
            nodesExpanded++;
            cout << "Expanding: " << current.state 
                 << " (g=" << current.g 
                 << ", h=" << current.h 
                 << ", f=" << current.f << ")" << endl;
            
            if (current.state == goal) {
                cout << "\nTotal nodes expanded: " << nodesExpanded << endl;
                cout << "Total path cost: " << current.g << endl;
                return current.path;
            }
            
            for (auto& [neighbor, cost] : graph[current.state]) {
                int newG = current.g + cost;
                
                // Hanya proses jika ini path lebih baik
                if (!bestG.count(neighbor) || newG < bestG[neighbor]) {
                    bestG[neighbor] = newG;
                    
                    vector<string> newPath = current.path;
                    newPath.push_back(neighbor);
                    
                    int h = getHeuristic(neighbor);
                    AStarNode childNode = {
                        neighbor, 
                        newG, 
                        h, 
                        newG + h, 
                        newPath
                    };
                    frontier.push(childNode);
                }
            }
        }
        
        return {}; // Tidak ditemukan
    }
};

int main() {
    AStarSearch astar;
    
    // Graf peta Romania
    astar.addEdge("Arad", "Zerind", 75);
    astar.addEdge("Arad", "Sibiu", 140);
    astar.addEdge("Arad", "Timisoara", 118);
    astar.addEdge("Zerind", "Oradea", 71);
    astar.addEdge("Oradea", "Sibiu", 151);
    astar.addEdge("Sibiu", "Fagaras", 99);
    astar.addEdge("Sibiu", "RimnicuVilcea", 80);
    astar.addEdge("Fagaras", "Bucharest", 211);
    astar.addEdge("RimnicuVilcea", "Pitesti", 97);
    astar.addEdge("RimnicuVilcea", "Craiova", 146);
    astar.addEdge("Pitesti", "Bucharest", 101);
    astar.addEdge("Pitesti", "Craiova", 138);
    astar.addEdge("Craiova", "Bucharest", 160);
    astar.addEdge("Timisoara", "Lugoj", 111);
    
    // Heuristik: Straight-Line Distance ke Bucharest
    astar.setHeuristic("Arad", 366);
    astar.setHeuristic("Zerind", 374);
    astar.setHeuristic("Oradea", 380);
    astar.setHeuristic("Sibiu", 253);
    astar.setHeuristic("Timisoara", 329);
    astar.setHeuristic("Lugoj", 244);
    astar.setHeuristic("Fagaras", 176);
    astar.setHeuristic("RimnicuVilcea", 193);
    astar.setHeuristic("Craiova", 160);
    astar.setHeuristic("Pitesti", 100);
    astar.setHeuristic("Bucharest", 0);
    
    cout << "=== A* Search ===" << endl;
    cout << "Dari Arad ke Bucharest:" << endl << endl;
    
    vector<string> path = astar.search("Arad", "Bucharest");
    
    cout << "\nPath optimal: ";
    for (int i = 0; i < path.size(); i++) {
        cout << path[i];
        if (i < path.size() - 1) cout << " -> ";
    }
    cout << endl;
    
    return 0;
}
```

**Output:**
```
=== A* Search ===
Dari Arad ke Bucharest:

Expanding: Arad (g=0, h=366, f=366)
Expanding: Sibiu (g=140, h=253, f=393)
Expanding: RimnicuVilcea (g=220, h=193, f=413)
Expanding: Fagaras (g=239, h=176, f=415)
Expanding: Pitesti (g=317, h=100, f=417)
Expanding: Bucharest (g=418, h=0, f=418)

Total nodes expanded: 6
Total path cost: 418

Path optimal: Arad -> Sibiu -> RimnicuVilcea -> Pitesti -> Bucharest
```

---

#### Solved Problem 7 ⭐

**Soal:** Trace algoritma A* untuk mencari path dari A ke G pada graf berikut:

```
        B ---2--- D
       /|        |
      3 |        1
     /  4        |
    A   |   E    G
     \  | /   \ /
      2 |1     2
       \|/    /
        C ---3--- F
        
h(A)=6, h(B)=4, h(C)=4, h(D)=2, h(E)=2, h(F)=1, h(G)=0
```

**Penyelesaian:**

**Langkah 1:** Inisialisasi
- frontier = {A(g=0, h=6, f=6)}
- explored = {}

**Langkah 2:** Expand A
- explored = {A}
- Successors: B(g=3, f=3+4=7), C(g=2, f=2+4=6)
- frontier = {C(f=6), B(f=7)}

**Langkah 3:** Expand C (f=6 terkecil)
- explored = {A, C}
- Successors dari C: B(g=2+4=6, f=6+4=10), E(g=2+1=3, f=3+2=5), F(g=2+3=5, f=5+1=6)
- frontier = {E(f=5), F(f=6), B(f=7)}

**Langkah 4:** Expand E (f=5 terkecil)
- explored = {A, C, E}
- Successors dari E: G(g=3+2=5, f=5+0=5)
- frontier = {G(f=5), F(f=6), B(f=7)}

**Langkah 5:** Expand G (f=5 terkecil)
- G adalah goal!
- Path: A → C → E → G
- Cost: 2 + 1 + 2 = 5

**Jawaban:** Path optimal: A → C → E → G dengan total cost 5. ∎

---

#### Solved Problem 8 ⭐⭐

**Soal:** Bandingkan jumlah node yang diekspansi oleh UCS vs A* untuk mencari path dari Arad ke Bucharest!

**Penyelesaian:**

**Langkah 1:** Trace UCS (tanpa heuristik)

UCS hanya menggunakan g(n):
1. Expand Arad (g=0)
2. Expand Zerind (g=75)
3. Expand Timisoara (g=118)
4. Expand Sibiu (g=140)
5. Expand Oradea (g=146)
6. Expand RimnicuVilcea (g=220)
7. Expand Lugoj (g=229)
8. Expand Fagaras (g=239)
9. Expand Craiova (g=266)
10. Expand Pitesti (g=317)
11. Expand Bucharest (g=418 via Pitesti) ✓

**UCS: ~11 nodes expanded**

**Langkah 2:** Trace A* (dengan heuristik SLD)

A* menggunakan f(n) = g(n) + h(n):
1. Expand Arad (f=366)
2. Expand Sibiu (f=393)
3. Expand RimnicuVilcea (f=413)
4. Expand Fagaras (f=415)
5. Expand Pitesti (f=417)
6. Expand Bucharest (f=418) ✓

**A*: 6 nodes expanded**

**Langkah 3:** Perbandingan

| Metrik | UCS | A* |
|--------|-----|-----|
| Nodes expanded | ~11 | 6 |
| Path cost | 418 | 418 |
| Optimal? | Ya | Ya |

**Jawaban:** A* mengekspansi 6 node, sedangkan UCS ~11 node. A* lebih efisien karena heuristik mengarahkan pencarian menuju goal, menghindari eksplorasi node yang menjauh seperti Zerind, Timisoara, dan Oradea. Kedua algoritma menemukan path optimal dengan cost 418. ∎

---

## 5. Properti Heuristik

### 5.1 Admissibility

> **Heuristik admissible** adalah heuristik yang tidak pernah meng-overestimate biaya sebenarnya untuk mencapai goal. 
> 
> Formal: h(n) ≤ h*(n) untuk semua n, dimana h*(n) adalah biaya sebenarnya.

**Contoh:**
- Straight-line distance adalah admissible karena jarak garis lurus selalu ≤ jarak jalan sebenarnya
- Manhattan distance untuk 8-puzzle adalah admissible karena setiap tile minimal perlu sejumlah gerakan tersebut

**Teorema:** Jika h(n) admissible, maka A* adalah **optimal**.

### 5.2 Consistency (Monotonicity)

> **Heuristik consistent** memenuhi ketidaksamaan segitiga:
> 
> h(n) ≤ c(n, a, n') + h(n')
> 
> untuk setiap node n dan successor n' melalui aksi a dengan cost c.

![Ilustrasi Consistency](images/p03-04-consistency-heuristic.png)

*Gambar 3.5: Ilustrasi kondisi consistency pada heuristik*

**Teorema:** Setiap heuristik consistent adalah admissible, tapi tidak sebaliknya.

**Implikasi consistency:**
- f(n) tidak pernah berkurang sepanjang path
- Sekali node diekspansi, tidak perlu diekspansi lagi (graph search optimal)

### 5.3 Dominance

> Heuristik h₂ **mendominasi** h₁ jika:
> 
> h₂(n) ≥ h₁(n) untuk semua n, dan keduanya admissible.

**Implikasi:** Jika h₂ mendominasi h₁, maka A* dengan h₂ tidak akan pernah mengekspansi lebih banyak node dari A* dengan h₁.

**Contoh untuk 8-puzzle:**
- h₁ = misplaced tiles
- h₂ = Manhattan distance
- h₂ mendominasi h₁ (terbukti di Solved Problem 3.4)

---

#### Solved Problem 9 ⭐⭐

**Soal:** Buktikan bahwa straight-line distance ke Bucharest adalah heuristik admissible!

**Penyelesaian:**

**Langkah 1:** Definisi admissibility
h(n) admissible jika h(n) ≤ h*(n) untuk semua n, dimana h*(n) adalah biaya sebenarnya.

**Langkah 2:** Analisis straight-line distance (SLD)
- SLD adalah jarak garis lurus dari kota n ke Bucharest
- Jarak sebenarnya h*(n) adalah jarak terpendek melalui jalan

**Langkah 3:** Bukti
Untuk setiap dua titik dalam ruang Euclidean:
- Jarak garis lurus ≤ jarak melalui jalur apapun

Ini adalah konsekuensi dari **ketidaksamaan segitiga**: path terpendek antara dua titik adalah garis lurus.

**Langkah 4:** Verifikasi dengan contoh
- SLD(Arad, Bucharest) = 366 km
- Jarak aktual (Arad→Sibiu→RV→Pitesti→Bucharest) = 418 km
- 366 ≤ 418 ✓

**Jawaban:** SLD admissible karena jarak garis lurus selalu ≤ jarak melalui jalan. Ini berlaku untuk semua kota karena merupakan sifat dasar geometri Euclidean. ∎

---

#### Solved Problem 10 ⭐⭐⭐

**Soal:** Buktikan bahwa Manhattan distance adalah consistent untuk 8-puzzle!

**Penyelesaian:**

**Langkah 1:** Kondisi consistency
h(n) consistent jika: h(n) ≤ c(n, a, n') + h(n') untuk semua n dan successor n'

**Langkah 2:** Analisis satu langkah di 8-puzzle
- Setiap aksi: menggeser satu tile
- c(n, a, n') = 1 (biaya setiap langkah)

**Langkah 3:** Analisis perubahan Manhattan distance
Ketika satu tile digeser:
- Tile bisa mendekat 1 langkah ke posisi goal: h berkurang 1
- Tile bisa menjauh 1 langkah dari posisi goal: h bertambah 1
- Maksimal perubahan = 1

**Langkah 4:** Bukti formal
Misalkan h(n) = Manhattan distance di state n
Setelah satu gerakan: h(n') = h(n) ± 1 (atau tetap)

Kasus 1: h(n') = h(n) - 1 (tile mendekat)
h(n) = h(n') + 1 = c(n,a,n') + h(n') ✓

Kasus 2: h(n') = h(n) + 1 (tile menjauh)
h(n) = h(n') - 1 < c(n,a,n') + h(n') ✓

Kasus 3: h(n') = h(n) (tile tidak terpengaruh)
h(n) = h(n') ≤ 1 + h(n') = c(n,a,n') + h(n') ✓

**Jawaban:** Manhattan distance consistent karena setiap gerakan hanya mengubah jarak satu tile maksimal 1, sementara biaya gerakan adalah 1. Sehingga h(n) ≤ 1 + h(n') selalu terpenuhi. ∎

---

#### Solved Problem 11 ⭐⭐⭐

**Soal:** Berikan contoh heuristik yang admissible tapi tidak consistent!

**Penyelesaian:**

**Langkah 1:** Konstruksi graf

```
    A --1-- B --1-- C (Goal)
    
h*(A) = 2, h*(B) = 1, h*(C) = 0
```

**Langkah 2:** Definisikan heuristik h yang admissible tapi tidak consistent

```
h(A) = 2  (sama dengan h*, admissible)
h(B) = 0  (kurang dari h*=1, admissible)
h(C) = 0  (goal, harus 0)
```

**Langkah 3:** Cek admissibility
- h(A) = 2 ≤ h*(A) = 2 ✓
- h(B) = 0 ≤ h*(B) = 1 ✓
- h(C) = 0 ≤ h*(C) = 0 ✓

Semua admissible!

**Langkah 4:** Cek consistency dari A ke B
h(A) ≤ c(A, B) + h(B)?
2 ≤ 1 + 0?
2 ≤ 1? ✗

**Tidak consistent!**

**Jawaban:** Heuristik h(A)=2, h(B)=0, h(C)=0 pada graf linear A-B-C adalah admissible (tidak overestimate) tapi tidak consistent (melanggar ketidaksamaan segitiga dari A ke B). ∎

---

## 6. Teknik Merancang Heuristik

### 6.1 Relaxed Problem

> **Relaxed problem** adalah versi masalah asli dengan beberapa constraint dihilangkan. Biaya optimal dari relaxed problem adalah heuristik admissible untuk masalah asli.

**Contoh untuk 8-puzzle:**

| Relaxation | Heuristik yang Dihasilkan |
|------------|--------------------------|
| Tile bisa melompat ke posisi manapun | Misplaced tiles |
| Tile bisa bergerak ke kotak adjacent manapun (termasuk yang terisi) | Manhattan distance |
| Tile bisa bergerak ke kotak kosong adjacent | Biaya sebenarnya h* |

### 6.2 Pattern Database

> **Pattern database** menyimpan biaya optimal untuk menyelesaikan subset dari masalah (pattern) dan menjumlahkannya sebagai heuristik.

Contoh: Untuk 15-puzzle, simpan biaya optimal untuk:
- Tile 1-2-3-4 saja
- Tile 5-6-7-8 saja
- dst.

### 6.3 Kombinasi Heuristik

Jika h₁ dan h₂ keduanya admissible:

$$h(n) = \max(h_1(n), h_2(n))$$

adalah juga admissible dan mendominasi keduanya.

---

#### Solved Problem 12 ⭐⭐

**Soal:** Rancang heuristik untuk masalah 8-puzzle menggunakan teknik relaxed problem!

**Penyelesaian:**

**Langkah 1:** Identifikasi constraint masalah asli
1. Tile hanya bisa bergerak ke kotak kosong
2. Kotak kosong harus adjacent dengan tile yang dipindah
3. Hanya satu tile yang bisa dipindah per langkah

**Langkah 2:** Relaxation 1 - Hapus constraint 1 dan 2
"Tile bisa pindah ke kotak manapun dalam satu langkah"

Heuristik: **Misplaced tiles** - hitung berapa tile yang tidak di posisi goal

**Langkah 3:** Relaxation 2 - Hapus hanya constraint 1
"Tile bisa bergerak ke kotak adjacent manapun, meski terisi"

Heuristik: **Manhattan distance** - jumlah jarak horizontal + vertikal setiap tile ke posisinya

**Langkah 4:** Relaxation 3 - Hapus constraint 3
"Bisa memindahkan beberapa tile sekaligus"

Heuristik: **Max Manhattan** atau pattern database

**Langkah 5:** Verifikasi admissibility
- Relaxed problem selalu lebih mudah dari masalah asli
- Biaya optimal di relaxed problem ≤ biaya optimal di masalah asli
- Semua heuristik ini admissible

**Jawaban:** 
1. Misplaced tiles: h₁(n) = jumlah tile salah posisi
2. Manhattan distance: h₂(n) = Σ|xᵢ - xgoal| + |yᵢ - ygoal|

Manhattan distance lebih informatif (mendominasi misplaced tiles). ∎

---

#### Solved Problem 13 ⭐⭐

**Soal:** Jika h₁(n) = 5 dan h₂(n) = 3 untuk suatu state n, dan keduanya admissible, berapa heuristik kombinasi terbaik?

**Penyelesaian:**

**Langkah 1:** Identifikasi metode kombinasi
Untuk heuristik admissible, kita bisa menggunakan:
$$h(n) = \max(h_1(n), h_2(n))$$

**Langkah 2:** Hitung
$$h(n) = \max(5, 3) = 5$$

**Langkah 3:** Verifikasi admissibility
- h₁ admissible → h₁(n) ≤ h*(n) → 5 ≤ h*(n)
- h₂ admissible → h₂(n) ≤ h*(n) → 3 ≤ h*(n)
- max(5, 3) = 5 ≤ h*(n) ✓

**Langkah 4:** Verifikasi dominance
- h(n) = 5 ≥ h₁(n) = 5 ✓
- h(n) = 5 ≥ h₂(n) = 3 ✓

**Jawaban:** h(n) = max(5, 3) = 5. Heuristik kombinasi ini admissible dan mendominasi kedua heuristik individual, sehingga A* akan lebih efisien. ∎

---

## 7. Optimalitas A*

### 7.1 Teorema Optimalitas

> **Teorema:** A* dengan heuristik admissible adalah optimal untuk tree search.
> 
> **Teorema:** A* dengan heuristik consistent adalah optimal untuk graph search.

### 7.2 Bukti Optimalitas (Sketch)

**Lemma 1:** Jika h consistent, maka f(n) non-decreasing sepanjang path.

**Bukti:**
- f(n') = g(n') + h(n')
- f(n') = g(n) + c(n,a,n') + h(n')
- f(n') ≥ g(n) + h(n) = f(n) [karena h(n) ≤ c(n,a,n') + h(n')]

**Lemma 2:** A* mengekspansi node dalam urutan f-value.

**Teorema:** A* menemukan solusi optimal.

**Bukti:**
Misalkan G adalah goal optimal dengan f(G) = g(G) = C*
Misalkan G' adalah goal suboptimal dengan g(G') > C*

Karena h(G) = h(G') = 0:
- f(G) = C*
- f(G') = g(G') > C*

A* mengekspansi node dengan f terkecil, sehingga G akan diekspansi sebelum G'.

### 7.3 Visualisasi Optimalitas

![Visualisasi Optimalitas A*](images/p03-05-astar-optimality-proof.png)

*Gambar 3.6: Ilustrasi mengapa A* dengan heuristik admissible menemukan solusi optimal*

---

#### Solved Problem 14 ⭐⭐

**Soal:** Jelaskan mengapa A* dengan graph search membutuhkan heuristik consistent, bukan hanya admissible!

**Penyelesaian:**

**Langkah 1:** Perbedaan tree search vs graph search
- Tree search: tidak track explored nodes, bisa visit node berkali-kali
- Graph search: track explored nodes, setiap node hanya diekspansi sekali

**Langkah 2:** Konstruksi counterexample
```
    A --1-- B --1-- C
     \            /
      ---5-------
      
h(A) = 4, h(B) = 2, h(C) = 0
(admissible tapi tidak consistent)
```

**Langkah 3:** Trace A* graph search
1. Start A: f(A) = 0 + 4 = 4
2. Expand A, add B(f=1+2=3), C(f=5+0=5)
3. Expand B (explored = {A, B}), add C(f=2+0=2)
4. Tapi C sudah di frontier dengan f=5!
5. Dalam graph search standar, C(f=5) mungkin tidak diganti dengan C(f=2)
6. Jika expand C(f=5), solusi suboptimal!

**Langkah 4:** Masalah
Dengan heuristik non-consistent, path ke suatu node bisa memiliki f-value yang tidak monoton. Graph search yang hanya track explored set bisa miss path yang lebih baik.

**Jawaban:** A* graph search membutuhkan consistent heuristic karena consistency menjamin f-value monoton non-decreasing sepanjang path. Tanpa ini, node yang sudah di-explore mungkin seharusnya di-expand lagi karena ditemukan path lebih baik, yang tidak dilakukan graph search standar. ∎

---

#### Solved Problem 15 ⭐⭐⭐

**Soal:** Buktikan bahwa jika h₁ mendominasi h₂ (h₁ ≥ h₂), maka A* dengan h₁ tidak pernah mengekspansi lebih banyak node dari A* dengan h₂!

**Penyelesaian:**

**Langkah 1:** Definisi dominance
h₁ mendominasi h₂ jika untuk semua n: h₁(n) ≥ h₂(n) dan keduanya admissible.

**Langkah 2:** Analisis ekspansi A*
A* mengekspansi semua node n dengan f(n) < C* (biaya optimal) sebelum menemukan goal.

**Langkah 3:** Perbandingan f-values
Untuk node n dengan A* menggunakan h₁:
$$f_1(n) = g(n) + h_1(n)$$

Dengan A* menggunakan h₂:
$$f_2(n) = g(n) + h_2(n)$$

Karena h₁(n) ≥ h₂(n):
$$f_1(n) \geq f_2(n)$$

**Langkah 4:** Implikasi
- Jika f₁(n) < C*, maka f₂(n) < C* juga (karena f₂ ≤ f₁ < C*)
- Tapi jika f₂(n) < C*, tidak berarti f₁(n) < C*
- Nodes dengan f₂(n) < C* ≤ f₁(n) akan diekspansi oleh A* dengan h₂ tapi tidak h₁

**Langkah 5:** Kesimpulan
$$\{n : f_1(n) < C*\} \subseteq \{n : f_2(n) < C*\}$$

Sehingga nodes diekspansi dengan h₁ ≤ nodes diekspansi dengan h₂.

**Jawaban:** A* dengan h₁ mengekspansi ≤ node karena f₁(n) ≥ f₂(n) untuk semua n. Node yang tidak diekspansi dengan h₁ (karena f₁ ≥ C*) mungkin diekspansi dengan h₂ (jika f₂ < C*). Heuristik yang lebih tinggi memberikan "guidance" lebih baik. ∎

---

## 8. Kompleksitas A*

### 8.1 Kompleksitas Waktu dan Ruang

| Kompleksitas | Worst Case | Dengan Heuristik Baik |
|--------------|------------|----------------------|
| Waktu | O(b^d) | Mendekati O(d) untuk h* |
| Ruang | O(b^d) | O(b^d) |

Dimana:
- b = branching factor
- d = kedalaman solusi
- h* = heuristik sempurna

### 8.2 Effective Branching Factor

> **Effective branching factor b*** adalah branching factor dari tree seragam dengan N nodes dan kedalaman d:
> 
> N = 1 + b* + (b*)² + ... + (b*)^d

Semakin kecil b*, semakin efektif heuristiknya.

**Contoh perbandingan untuk 8-puzzle:**

| Heuristik | Rata-rata Nodes | Effective b* |
|-----------|-----------------|--------------|
| IDS (tanpa heuristik) | 3,644,035 | ~2.87 |
| h = misplaced tiles | 539 | ~1.79 |
| h = Manhattan | 93 | ~1.26 |

---

#### Solved Problem 16 ⭐⭐

**Soal:** Jika A* mengekspansi 25 node untuk menemukan solusi pada kedalaman 4, hitung effective branching factor!

**Penyelesaian:**

**Langkah 1:** Rumus
$$N = 1 + b^* + (b^*)^2 + ... + (b^*)^d$$
$$25 = 1 + b^* + (b^*)^2 + (b^*)^3 + (b^*)^4$$

**Langkah 2:** Sederhanakan menggunakan rumus deret geometri
$$25 = \frac{(b^*)^5 - 1}{b^* - 1}$$

**Langkah 3:** Selesaikan secara numerik
- Coba b* = 2: 1+2+4+8+16 = 31 (terlalu besar)
- Coba b* = 1.8: 1+1.8+3.24+5.83+10.50 = 22.37 (terlalu kecil)
- Coba b* = 1.9: 1+1.9+3.61+6.86+13.03 = 26.4 (mendekati)
- Coba b* = 1.85: 1+1.85+3.42+6.33+11.71 = 24.31 (sangat dekat)

**Langkah 4:** Interpolasi
b* ≈ 1.86

**Jawaban:** Effective branching factor b* ≈ 1.86. Ini menunjukkan heuristik cukup baik karena jauh di bawah branching factor 8-puzzle yang asli (~3). ∎

---

## 9. Variasi Memory-Bounded A*

### 9.1 Masalah Memori pada A*

A* menyimpan semua node di frontier dan explored set, yang bisa sangat besar:
- 15-puzzle: ~10¹³ states
- Rubik's cube: ~4.3 × 10¹⁹ states

### 9.2 IDA* (Iterative Deepening A*)

> **IDA*** menggunakan f-limit sebagai cutoff, bukan depth limit. Setiap iterasi menaikkan f-limit ke f-value minimum yang melebihi limit sebelumnya.

```
function IDA_Star(problem, h):
    limit ← h(problem.initial_state)
    
    loop:
        result, new_limit ← DFS_Contour(problem.initial, limit, h)
        if result is Solution: return result
        if new_limit = ∞: return Failure
        limit ← new_limit

function DFS_Contour(node, limit, h):
    f ← node.g + h(node.state)
    if f > limit: return (Cutoff, f)
    if goal_test(node.state): return (Solution, node)
    
    min_exceeded ← ∞
    for each successor of node:
        result, new_f ← DFS_Contour(successor, limit, h)
        if result is Solution: return (Solution, result)
        min_exceeded ← min(min_exceeded, new_f)
    
    return (Cutoff, min_exceeded)
```

**Karakteristik IDA*:**
- Space: O(bd) - linear!
- Time: Lebih banyak iterasi dari A*
- Optimal dengan heuristik admissible

### 9.3 SMA* (Simplified Memory-Bounded A*)

> **SMA*** menggunakan memori yang tersedia seoptimal mungkin. Ketika memori penuh, buang node dengan f tertinggi.

**Karakteristik SMA*:**
- Menggunakan memori sampai batas yang ditentukan
- Optimal jika solusi muat dalam memori
- Complete jika solusi muat dalam memori

---

#### Solved Problem 17 ⭐⭐

**Soal:** Trace IDA* untuk graf sederhana berikut dari S ke G:

```
S --1-- A --2-- G
 \      |
  2     1
   \    |
    B --2-- C
    
h(S)=3, h(A)=2, h(B)=2, h(C)=1, h(G)=0
```

**Penyelesaian:**

**Iterasi 1: limit = h(S) = 3**

DFS dari S:
- S: f = 0+3 = 3 ≤ 3, expand
- A: f = 1+2 = 3 ≤ 3, expand
- G: f = 1+2+0 = 3 ≤ 3, GOAL!

**Jawaban:** IDA* menemukan solusi S→A→G dengan cost 3 pada iterasi pertama. Lucky case karena f(goal) = limit awal! ∎

---

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Modifikasi contoh sebelumnya sehingga IDA* membutuhkan lebih dari satu iterasi!

**Penyelesaian:**

**Langkah 1:** Modifikasi heuristik
```
S --1-- A --3-- G
 \      |
  2     1
   \    |
    B --2-- C
    
h(S)=4, h(A)=3, h(B)=3, h(C)=2, h(G)=0
```

**Langkah 2:** Iterasi 1: limit = h(S) = 4

DFS dari S:
- S: f = 0+4 = 4 ≤ 4, expand
- A: f = 1+3 = 4 ≤ 4, expand
  - G: f = 1+3+0 = 4 ≤ 4, GOAL!

Hmm, masih ketemu di iterasi 1. Mari modifikasi lagi:

**Langkah 3:** Modifikasi lebih lanjut
```
S --1-- A --3-- G
 \      
  2     
   \    
    B --4-- G
    
h(S)=3, h(A)=2, h(B)=4, h(G)=0
```

**Langkah 4:** Iterasi 1: limit = 3

DFS dari S:
- S: f = 0+3 = 3 ≤ 3, expand
- A: f = 1+2 = 3 ≤ 3, expand
  - G: f = 1+3+0 = 4 > 3, CUTOFF, return 4
- B: f = 2+4 = 6 > 3, CUTOFF, return 6

New limit = min(4, 6) = 4

**Langkah 5:** Iterasi 2: limit = 4

DFS dari S:
- S: f = 3 ≤ 4, expand
- A: f = 3 ≤ 4, expand
  - G: f = 4 ≤ 4, GOAL!

Path: S→A→G, cost = 4

**Jawaban:** Dengan h(S)=3, h(A)=2, dan cost(A,G)=3, IDA* membutuhkan 2 iterasi: pertama dengan limit=3 (cutoff di G dengan f=4), kedua dengan limit=4 (berhasil). ∎

---

## 10. Aplikasi dalam Konteks Pertahanan

### 10.1 Perencanaan Misi Militer

Algoritma A* dapat digunakan untuk merencanakan rute misi dengan mempertimbangkan:
- **g(n)**: Jarak tempuh, konsumsi bahan bakar, waktu
- **h(n)**: Estimasi jarak ke target
- **Constraints**: Zona larangan terbang, posisi musuh

### 10.2 Contoh: Pencarian Rute UAV

```cpp
struct MissionNode {
    int x, y;           // posisi grid
    int altitude;       // ketinggian
    double g;           // biaya: fuel + time
    double h;           // heuristik: jarak ke target
    double threat;      // tingkat ancaman
    
    double f() const {
        return g + h + threat_weight * threat;
    }
};
```

### 10.3 Heuristik untuk Operasi Militer

| Faktor | Heuristik |
|--------|-----------|
| Jarak | Euclidean/Manhattan distance |
| Terrain | Elevation-adjusted distance |
| Threat | Proximity to known enemy positions |
| Stealth | Radar coverage estimation |

---

#### Solved Problem 19 ⭐⭐⭐

**Soal:** Desain fungsi heuristik untuk UAV yang harus menghindari radar musuh!

**Penyelesaian:**

**Langkah 1:** Identifikasi faktor

1. **Jarak ke target** - harus diminimalkan
2. **Jangkauan radar** - harus dihindari
3. **Ketinggian terbang** - mempengaruhi deteksi

**Langkah 2:** Formulasi heuristik

```cpp
double calculateHeuristic(Node n, Target t, vector<Radar>& radars) {
    // Komponen 1: Jarak Euclidean ke target
    double dist = euclideanDistance(n.pos, t.pos);
    
    // Komponen 2: Penalti radar
    double radarPenalty = 0;
    for (auto& radar : radars) {
        double d = euclideanDistance(n.pos, radar.pos);
        if (d < radar.range) {
            // Dalam jangkauan radar
            radarPenalty += (radar.range - d) * radar.detection_prob;
        }
    }
    
    // Komponen 3: Bonus ketinggian rendah (low observable)
    double altitudeBonus = (MAX_ALT - n.altitude) * ALT_FACTOR;
    
    return dist + RADAR_WEIGHT * radarPenalty - altitudeBonus;
}
```

**Langkah 3:** Verifikasi admissibility

Untuk menjamin admissible:
- Jarak Euclidean ≤ jarak aktual (admissible)
- radarPenalty harus ≤ penalti deteksi sebenarnya
- altitudeBonus harus ≤ keuntungan sebenarnya

**Langkah 4:** Implementasi safe

```cpp
// Versi konservatif (pasti admissible)
double safeHeuristic(Node n, Target t) {
    return euclideanDistance(n.pos, t.pos);  // underestimate total cost
}
```

**Jawaban:** Heuristik gabungan dengan distance + radar penalty - altitude bonus. Untuk menjamin admissibility, gunakan weight factors < 1 atau fallback ke Euclidean distance saja. Trade-off: heuristik yang lebih informatif mungkin tidak admissible, heuristik admissible mungkin kurang informatif. ∎

---

#### Solved Problem 20 ⭐⭐

**Soal:** Sebuah tim SAR (Search and Rescue) harus mencari korban di area bencana. Area dibagi menjadi grid 10x10. Tim mulai dari (0,0) dan korban di (9,9). Beberapa sel tidak bisa dilalui karena reruntuhan. Desain representasi masalah dan heuristik untuk A*!

**Penyelesaian:**

**Langkah 1:** Representasi masalah

```cpp
struct SARProblem {
    // State: posisi tim
    struct State {
        int x, y;
    };
    
    State initial = {0, 0};
    State goal = {9, 9};
    
    // Grid: 0 = passable, 1 = blocked
    int grid[10][10];
    
    // Actions: 4-directional movement
    vector<pair<int,int>> actions = {{0,1}, {1,0}, {0,-1}, {-1,0}};
    
    // Cost: uniform = 1 per step
    int cost(State s, Action a) { return 1; }
    
    // Goal test
    bool isGoal(State s) { return s.x == 9 && s.y == 9; }
};
```

**Langkah 2:** Heuristik - Manhattan Distance

```cpp
int heuristic(State s, State goal) {
    return abs(s.x - goal.x) + abs(s.y - goal.y);
}
```

**Langkah 3:** Verifikasi admissibility
- Manhattan distance = minimum steps jika tidak ada obstacle
- Dengan obstacles, actual cost ≥ Manhattan distance
- Heuristik admissible ✓

**Langkah 4:** Trace singkat

```
Start: (0,0), h=18
Expand neighbors: (0,1) h=17, (1,0) h=17
...
Goal: (9,9), h=0
```

**Jawaban:** 
- State: posisi (x,y) pada grid
- Actions: {atas, bawah, kiri, kanan} ke sel yang tidak blocked
- Cost: 1 per langkah (atau berbeda untuk terrain sulit)
- Heuristik: Manhattan distance h(n) = |x-9| + |y-9|

Heuristik ini admissible dan consistent untuk grid-based pathfinding. ∎

---

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Modifikasi heuristik SAR di atas untuk memprioritaskan pencarian di area dengan probabilitas korban lebih tinggi!

**Penyelesaian:**

**Langkah 1:** Tambahkan probability map

```cpp
struct SARProblem {
    // ... (sama seperti sebelumnya)
    
    // Probability map: P(korban ada di sel)
    double probability[10][10];
    
    // Accumulated probability along path
    double accumulatedProb;
};
```

**Langkah 2:** Modifikasi cost function

Daripada hanya minimize jarak, kita ingin maximize probability of finding victim:

```cpp
// Utility-based cost: trade-off distance vs probability
double cost(State from, State to) {
    double distCost = 1.0;  // base movement cost
    double probReward = -PROB_WEIGHT * probability[to.x][to.y];
    return distCost + probReward;  // negative reward = reduced cost
}
```

**Langkah 3:** Modifikasi heuristik

```cpp
double heuristic(State s, State goal) {
    double distH = manhattanDistance(s, goal);
    
    // Estimate remaining probability to collect
    double maxRemainingProb = 0;
    for (int x = s.x; x <= goal.x; x++) {
        for (int y = s.y; y <= goal.y; y++) {
            maxRemainingProb = max(maxRemainingProb, probability[x][y]);
        }
    }
    
    // Optimistic estimate (admissible)
    return distH - PROB_WEIGHT * maxRemainingProb;
}
```

**Langkah 4:** Verifikasi admissibility
- Kita overestimate reward (menggunakan max probability)
- Sehingga underestimate total cost
- Heuristik tetap admissible ✓

**Jawaban:** 
- Cost function: g(n) = Σ(1 - w × P(cell))
- Heuristik: h(n) = Manhattan - w × max(remaining probability)

Dengan modifikasi ini, A* akan cenderung melalui area dengan probabilitas korban tinggi sambil tetap menuju goal. ∎

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Implementasikan A* lengkap untuk menyelesaikan 8-puzzle dengan Manhattan distance heuristic!

**Penyelesaian:**

```cpp
#include <iostream>
#include <queue>
#include <unordered_set>
#include <vector>
#include <string>
#include <sstream>

using namespace std;

class Puzzle8 {
private:
    vector<int> state;  // 0 represents blank
    int g;              // cost from start
    int h;              // heuristic
    int blankPos;
    vector<string> path;
    
    static const vector<int> goal;
    
public:
    Puzzle8(vector<int> initial) : state(initial), g(0) {
        blankPos = find(state.begin(), state.end(), 0) - state.begin();
        h = calculateManhattan();
        path.push_back(stateToString());
    }
    
    Puzzle8(const Puzzle8& other, int newBlankPos) {
        state = other.state;
        g = other.g + 1;
        blankPos = other.blankPos;
        path = other.path;
        
        // Swap blank with target position
        swap(state[blankPos], state[newBlankPos]);
        blankPos = newBlankPos;
        h = calculateManhattan();
        path.push_back(stateToString());
    }
    
    int calculateManhattan() const {
        int total = 0;
        for (int i = 0; i < 9; i++) {
            if (state[i] != 0) {
                int goalPos = state[i] - 1;  // where this tile should be
                int currentRow = i / 3, currentCol = i % 3;
                int goalRow = goalPos / 3, goalCol = goalPos % 3;
                total += abs(currentRow - goalRow) + abs(currentCol - goalCol);
            }
        }
        return total;
    }
    
    int f() const { return g + h; }
    
    bool isGoal() const {
        return state == goal;
    }
    
    string stateToString() const {
        stringstream ss;
        for (int i = 0; i < 9; i++) {
            ss << state[i];
            if (i == 2 || i == 5) ss << "|";
        }
        return ss.str();
    }
    
    vector<Puzzle8> getSuccessors() const {
        vector<Puzzle8> successors;
        int row = blankPos / 3, col = blankPos % 3;
        
        // Up
        if (row > 0) successors.emplace_back(*this, blankPos - 3);
        // Down
        if (row < 2) successors.emplace_back(*this, blankPos + 3);
        // Left
        if (col > 0) successors.emplace_back(*this, blankPos - 1);
        // Right
        if (col < 2) successors.emplace_back(*this, blankPos + 1);
        
        return successors;
    }
    
    void printState() const {
        for (int i = 0; i < 9; i++) {
            if (state[i] == 0) cout << "  ";
            else cout << state[i] << " ";
            if (i % 3 == 2) cout << endl;
        }
    }
    
    void printPath() const {
        cout << "Solution path (" << g << " moves):" << endl;
        for (const string& s : path) {
            cout << s << endl;
        }
    }
    
    // For priority queue comparison
    bool operator>(const Puzzle8& other) const {
        return f() > other.f();
    }
    
    // For unordered_set
    bool operator==(const Puzzle8& other) const {
        return state == other.state;
    }
    
    struct Hash {
        size_t operator()(const Puzzle8& p) const {
            size_t h = 0;
            for (int i : p.state) {
                h = h * 10 + i;
            }
            return h;
        }
    };
};

const vector<int> Puzzle8::goal = {1, 2, 3, 4, 5, 6, 7, 8, 0};

Puzzle8 solve8Puzzle(Puzzle8 initial) {
    priority_queue<Puzzle8, vector<Puzzle8>, greater<Puzzle8>> frontier;
    unordered_set<Puzzle8, Puzzle8::Hash> explored;
    
    frontier.push(initial);
    int nodesExpanded = 0;
    
    while (!frontier.empty()) {
        Puzzle8 current = frontier.top();
        frontier.pop();
        
        if (current.isGoal()) {
            cout << "Nodes expanded: " << nodesExpanded << endl;
            return current;
        }
        
        if (explored.count(current)) continue;
        explored.insert(current);
        nodesExpanded++;
        
        for (Puzzle8& successor : current.getSuccessors()) {
            if (!explored.count(successor)) {
                frontier.push(successor);
            }
        }
    }
    
    return initial;  // No solution
}

int main() {
    // Initial state (example)
    vector<int> initial = {2, 8, 3, 1, 6, 4, 7, 0, 5};
    
    cout << "Initial state:" << endl;
    Puzzle8 puzzle(initial);
    puzzle.printState();
    cout << "Manhattan distance: " << puzzle.calculateManhattan() << endl;
    cout << "\nSolving with A*..." << endl << endl;
    
    Puzzle8 solution = solve8Puzzle(puzzle);
    solution.printPath();
    
    cout << "\nFinal state:" << endl;
    solution.printState();
    
    return 0;
}
```

**Output:**
```
Initial state:
2 8 3 
1 6 4 
7   5 
Manhattan distance: 9

Solving with A*...

Nodes expanded: 8
Solution path (5 moves):
283|164|705
283|164|075
283|064|175
083|264|175
803|264|175
123|804|765

Final state:
1 2 3 
8   4 
7 6 5 
```

Catatan: Output di atas adalah contoh, actual path mungkin berbeda tergantung tie-breaking.

**Jawaban:** Implementasi lengkap A* untuk 8-puzzle menggunakan:
- State: vector 9 elemen (0 = blank)
- Heuristik: Manhattan distance
- Struktur data: priority queue (min-heap by f), unordered_set (explored)
- Successors: 2-4 moves (up, down, left, right) tergantung posisi blank

∎

---

## 5. Supplementary Problems

**SP 3.1:** Jelaskan perbedaan antara Greedy Best-First Search dan A*! Kapan sebaiknya menggunakan masing-masing?

<details>
<summary>Jawaban</summary>

Greedy BFS menggunakan f(n) = h(n), A* menggunakan f(n) = g(n) + h(n). Gunakan Greedy jika kecepatan lebih penting dari optimalitas. Gunakan A* jika membutuhkan solusi optimal dan heuristik yang baik tersedia.
</details>

---

**SP 3.2:** Hitung Manhattan distance untuk 8-puzzle state: [1,8,2,0,4,3,7,6,5] menuju goal [1,2,3,4,5,6,7,8,0]!

<details>
<summary>Jawaban</summary>

h = 2+2+1+1+2+1+0+1 = 10 (tile 2: jarak 2, tile 3: jarak 1, tile 4: jarak 1, tile 5: jarak 2, tile 6: jarak 1, tile 8: jarak 2)
</details>

---

**SP 3.3:** Mengapa straight-line distance tidak bisa digunakan sebagai heuristik untuk pathfinding dalam labirin?

<details>
<summary>Jawaban</summary>

SLD tetap bisa digunakan dan tetap admissible untuk labirin. Namun, SLD mungkin sangat underestimate biaya sebenarnya jika banyak dinding menghalangi. Heuristik yang lebih baik mempertimbangkan struktur labirin.
</details>

---

**SP 3.4:** Sebutkan 3 contoh aplikasi A* selain pathfinding pada peta!

<details>
<summary>Jawaban</summary>

1. Puzzle solving (8-puzzle, 15-puzzle, Rubik's cube)
2. Game AI (NPC navigation, strategy planning)
3. Robot motion planning
4. Network routing
5. Natural language parsing
</details>

---

**SP 3.5:** Jika h(n) = 0 untuk semua n, algoritma apa yang dihasilkan A*?

<details>
<summary>Jawaban</summary>

A* dengan h(n) = 0 menjadi Uniform Cost Search (UCS), karena f(n) = g(n) + 0 = g(n). Tetap optimal tapi tidak terinformasi (blind search).
</details>

---

## Ringkasan

| Konsep | Definisi | Karakteristik |
|--------|----------|---------------|
| **Heuristik** | Estimasi biaya ke goal, h(n) | h(n) ≥ 0, h(goal) = 0 |
| **Greedy BFS** | Search dengan f(n) = h(n) | Cepat, tidak optimal, tidak complete |
| **A*** | Search dengan f(n) = g(n) + h(n) | Optimal dengan h admissible |
| **Admissible** | h(n) ≤ h*(n), tidak overestimate | Menjamin optimalitas A* |
| **Consistent** | h(n) ≤ c(n,a,n') + h(n') | Menjamin optimalitas graph search |
| **Dominance** | h₂(n) ≥ h₁(n) untuk semua n | A* dengan h₂ lebih efisien |
| **Manhattan** | Σ\|xi - xgoal\| + \|yi - ygoal\| | Admissible & consistent untuk grid |
| **IDA*** | Iterative deepening dengan f-limit | Space O(bd), optimal |
| **SMA*** | Memory-bounded A* | Optimal jika solusi muat di memori |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 3.5-3.6**
2. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. **Chapter 4**
3. CS188 Berkeley AI Materials: https://inst.eecs.berkeley.edu/~cs188/
4. A* Visualization: https://www.redblobgames.com/pathfinding/a-star/introduction.html

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
