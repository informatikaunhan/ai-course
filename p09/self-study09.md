# Panduan Belajar Mandiri Pertemuan 09: Representasi Pengetahuan - Logika Proposisional

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 09  
**Topik:** Representasi Pengetahuan - Logika Proposisional  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  
**Estimasi Waktu:** 420 menit (~7 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan aktivitas belajar mandiri ini, mahasiswa diharapkan mampu:

1. Merepresentasikan pengetahuan dunia nyata menggunakan logika proposisional
2. Memahami dan menerapkan konnektif logika (NOT, AND, OR, IMPLIES, IFF)
3. Melakukan inferensi menggunakan aturan inferensi dasar (Modus Ponens, Modus Tollens, dll.)
4. Mengkonversi kalimat logika ke Conjunctive Normal Form (CNF)
5. Membuktikan entailment menggunakan algoritma resolution
6. Mengimplementasikan knowledge base sederhana untuk aplikasi pertahanan

---

## 1. Review Konsep: Pengantar Logika Proposisional (45 menit)

### Ringkasan Materi

**Logika Proposisional** adalah sistem formal untuk merepresentasikan pengetahuan menggunakan proposisi (pernyataan yang bernilai benar atau salah). Dalam konteks AI, logika proposisional menjadi fondasi untuk representasi pengetahuan dan reasoning.

**Mengapa Logika Proposisional Penting dalam AI?**
- Memungkinkan representasi pengetahuan yang **presisi dan tidak ambigu**
- Mendukung **inferensi otomatis** — sistem dapat menarik kesimpulan baru dari fakta yang ada
- Basis untuk sistem **expert systems** dalam aplikasi militer dan intelijen
- Digunakan dalam **Wumpus World**, contoh klasik knowledge-based agent

**Komponen Utama:**
- **Proposisi**: Pernyataan yang bernilai benar (True/T/1) atau salah (False/F/0)
- **Konnektif Logika**: Operator untuk menghubungkan proposisi (¬, ∧, ∨, →, ↔)
- **Tabel Kebenaran**: Tabel yang menunjukkan nilai kebenaran untuk semua kombinasi input
- **Model**: Interpretasi yang memberikan nilai kebenaran untuk setiap proposisi
- **Knowledge Base (KB)**: Kumpulan kalimat logika yang merepresentasikan pengetahuan agen

**Knowledge-Based Agent** memiliki dua operasi utama:
1. **TELL**: Menambahkan fakta/aturan baru ke KB
2. **ASK**: Mengajukan query ke KB untuk mendapatkan kesimpulan

![Komponen Logika Proposisional](images/p09-01-propositional-logic-components.png)

*Gambar 9.1: Komponen utama dalam logika proposisional*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Komponen utama logika proposisional - proposisi, konnektif, model, dan knowledge base
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Hierarchical diagram showing components and relationships
COLORS: 
- Primary: #2563eb (blue) for main components
- Secondary: #10b981 (green) for propositions
- Accent: #f59e0b (orange) for connectives
- Warning: #ef4444 (red) for false values
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Top center: "Logika Proposisional" title box
2. Second level, left: "Proposisi" box with examples "P: Hujan", "Q: Basah" 
3. Second level, center: "Konnektif" box with symbols "¬, ∧, ∨, →, ↔"
4. Second level, right: "Model" box with truth value assignments
5. Bottom: "Knowledge Base" large box containing multiple logical sentences
6. Arrows connecting all components showing relationships
ARROWS/CONNECTIONS: Bidirectional arrows between propositions and connectives, downward arrow to knowledge base
LABELS: "Logika Proposisional", "Proposisi", "Konnektif", "Model", "Knowledge Base", "Pernyataan", "Operator", "Nilai Kebenaran", "Basis Pengetahuan"
SIZE: 900x600 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Propositional Logic - Introduction | Neso Academy | 11:24 | https://www.youtube.com/watch?v=HKEjVwZq2a0 |
| 2 | Propositional Logic Basics | Khan Academy | 8:47 | https://www.youtube.com/watch?v=qV4htTfow-E |
| 3 | Logic in AI - Propositional Logic | Artificial Intelligence - All in One | 15:32 | https://www.youtube.com/watch?v=JyKVRJ5Y71w |

### ✍️ Latihan Pemahaman

Setelah menonton video, jawab pertanyaan berikut:

1. Apa perbedaan antara **proposisi** dan **kalimat biasa** dalam bahasa natural? Berikan contoh masing-masing!
2. Sebutkan tiga alasan mengapa AI memerlukan representasi pengetahuan yang formal!
3. Berikan 3 contoh proposisi dalam konteks sistem pertahanan udara Indonesia!

---

## 2. Review Konsep: Konnektif Logika dan Tabel Kebenaran (60 menit)

### Ringkasan Materi

**Lima konnektif logika utama** membentuk "bahasa" untuk mengekspresikan hubungan antar proposisi:

| Konnektif | Simbol | Nama | Contoh |
|-----------|--------|------|--------|
| **NOT** | ¬ | Negasi | ¬P: "Tidak hujan" |
| **AND** | ∧ | Konjungsi | P ∧ Q: "Hujan DAN dingin" |
| **OR** | ∨ | Disjungsi | P ∨ Q: "Hujan ATAU dingin" |
| **IMPLIES** | → | Implikasi | P → Q: "Jika hujan maka basah" |
| **IFF** | ↔ | Biimplikasi | P ↔ Q: "Hujan jika dan hanya jika mendung" |

**Catatan Penting tentang Implikasi (→):**
- P → Q bernilai **False** hanya ketika P = True dan Q = False
- Jika P = False, maka P → Q **selalu True** (vacuously true)
- Ini sering membingungkan! Ingat: "Dari premis palsu, apapun bisa disimpulkan"

**Konteks Pertahanan:** Sistem C6ISR menggunakan logika untuk decision making:
- **Deteksi → Alert**: Jika radar mendeteksi objek asing → aktifkan sistem peringatan
- **Ancaman ∧ Otorisasi**: Tindakan ofensif hanya jika ada ancaman DAN ada otorisasi
- **Cuaca_Buruk ∨ Malam → Gunakan_Infrared**: Kondisi terbatas memerlukan sensor alternatif

**Prioritas Operator (dari tertinggi ke terendah):**

| Prioritas | Operator | Contoh |
|-----------|----------|--------|
| 1 (tertinggi) | ¬ (NOT) | ¬P |
| 2 | ∧ (AND) | P ∧ Q |
| 3 | ∨ (OR) | P ∨ Q |
| 4 | → (IMPLIES) | P → Q |
| 5 (terendah) | ↔ (IFF) | P ↔ Q |

**Ekuivalensi Logika Penting:**

| Nama | Ekuivalensi |
|------|-------------|
| Implication Elimination | P → Q ≡ ¬P ∨ Q |
| Contrapositive | P → Q ≡ ¬Q → ¬P |
| De Morgan's Law 1 | ¬(P ∧ Q) ≡ ¬P ∨ ¬Q |
| De Morgan's Law 2 | ¬(P ∨ Q) ≡ ¬P ∧ ¬Q |
| Double Negation | ¬(¬P) ≡ P |
| Biconditional Elimination | P ↔ Q ≡ (P → Q) ∧ (Q → P) |

![Konnektif Logika dan Tabel Kebenaran](images/p09-02-logical-connectives-truth-tables.png)

*Gambar 9.2: Lima konnektif logika dengan tabel kebenaran*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Lima konnektif logika proposisional dengan tabel kebenaran masing-masing
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Grid layout showing 5 connectives, each with symbol, name, and compact truth table
COLORS: 
- Primary: #2563eb (blue) for connective boxes
- Secondary: #10b981 (green) for True values in tables
- Accent: #f59e0b (orange) for symbols
- Warning: #ef4444 (red) for False values in tables
- Neutral: #6b7280 (gray) for table borders
- Background: #ffffff (white)
ELEMENTS:
1. Five boxes arranged in grid (3 top, 2 bottom):
   - Box 1: "NOT (¬)" with 2-row truth table
   - Box 2: "AND (∧)" with 4-row truth table
   - Box 3: "OR (∨)" with 4-row truth table
   - Box 4: "IMPLIES (→)" with 4-row truth table
   - Box 5: "IFF (↔)" with 4-row truth table
2. Each box has: symbol at top, Indonesian name below, compact truth table
3. Truth tables use T/F notation with color coding
ARROWS/CONNECTIONS: None between boxes (independent display)
LABELS: "NOT", "Negasi", "AND", "Konjungsi", "OR", "Disjungsi", "IMPLIES", "Implikasi", "IFF", "Biimplikasi", "P", "Q", "Hasil"
SIZE: 1000x700 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Truth Tables for Logical Operators | The Organic Chemistry Tutor | 12:28 | https://www.youtube.com/watch?v=9a9xqgV2UWc |
| 2 | Logical Connectives (Discrete Math) | Trefor Bazett | 15:10 | https://www.youtube.com/watch?v=vExH5hM9cJA |
| 3 | Propositional Logic Connectives | Neso Academy | 13:45 | https://www.youtube.com/watch?v=qV4htTfow-E |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Truth Table Generator | Stanford Logic | Generate dan verify truth tables | https://web.stanford.edu/class/cs103/tools/truth-table-tool/ |
| Logic Calculator | LogicCalculus | Interactive calculator untuk propositional logic | https://www.erpelstolz.at/gateway/LogicCalculus.html |
| Logic Tutor | Carnegie Mellon OLI | Interactive tutor untuk learning logic | http://oli.cmu.edu/courses/logic-proofs/ |

### ✍️ Latihan Pemahaman

1. Buat tabel kebenaran lengkap untuk formula: **(P ∧ Q) → R**
2. Dalam sistem radar, P = "Objek terdeteksi", Q = "Objek bergerak cepat", R = "Aktifkan alert". Representasikan: "Alert aktif jika dan hanya jika objek terdeteksi DAN bergerak cepat"
3. Buktikan menggunakan tabel kebenaran: **P → Q** ekuivalen dengan **¬P ∨ Q**

---

## 3. Eksplorasi Tools & Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Deskripsi | Link |
|------|-----------|------|
| Truth Table Generator | Generate truth tables untuk formula kompleks | https://web.stanford.edu/class/cs103/tools/truth-table-tool/ |
| Logic Circuit Simulator | Simulasi circuit logika | https://logic.ly/demo/ |
| Logictools | Comprehensive logic toolset | http://logictools.org/ |
| Wolfram Alpha Logic | Analyze logical expressions | https://www.wolframalpha.com/examples/mathematics/discrete-mathematics/logic |

### Tugas Eksplorasi

**Aktivitas 1: Truth Table Exploration (20 menit)**
1. Buka **Stanford Truth Table Generator**
2. Masukkan formula: `(P ∨ Q) ∧ (P → R) ∧ (Q → R) → R`
3. Generate tabel kebenaran
4. Screenshot hasil dan identifikasi: apakah formula ini **tautology** (selalu benar)?
5. Coba modifikasi formula dan observasi perubahan

**Aktivitas 2: Military Scenario Modeling (20 menit)**

Skenario: Sistem pertahanan udara otomatis
- **D**: Drone terdeteksi
- **H**: Drone di zona terlarang (High-security zone)
- **A**: Sistem otorisasi aktif
- **F**: Fire (tembak)

Tugas:
1. Representasikan aturan: "Tembak jika drone terdeteksi di zona terlarang dan sistem otorisasi aktif"
2. Buat truth table di tool untuk: `(D ∧ H ∧ A) → F`
3. Identifikasi kondisi kapan sistem TIDAK menembak (F = False)

**Aktivitas 3: Logic Puzzle (20 menit)**

Gunakan **Logic Calculator** untuk solve puzzle berikut:

Intel menerima informasi:
1. Jika ada infiltrasi, maka alarm akan berbunyi ATAU ada laporan
2. Tidak ada laporan
3. Alarm tidak berbunyi

Apakah ada infiltrasi? Buktikan dengan logika!

**Hint:** Representasikan sebagai:
- I = Infiltrasi, A = Alarm, L = Laporan
- KB: {I → (A ∨ L), ¬L, ¬A}
- Gunakan Modus Tollens untuk derive kesimpulan

---

## 4. Pendalaman: Inferensi dan Aturan Inferensi (60 menit)

### Ringkasan Materi

**Inferensi** adalah proses menarik kesimpulan baru dari pengetahuan yang ada. Aturan inferensi memungkinkan sistem AI untuk "berpikir" secara logis.

**Konsep Kunci:**
- **Entailment (⊨)**: KB ⊨ α artinya α pasti benar di semua model dimana KB benar
- **Satisfiability**: Formula yang bernilai True pada minimal satu model
- **Validity (Tautology)**: Formula yang bernilai True pada SEMUA model
- **Unsatisfiability (Contradiction)**: Formula yang bernilai False pada SEMUA model

**Hubungan Penting:** KB ⊨ α **jika dan hanya jika** (KB ∧ ¬α) unsatisfiable — ini adalah basis proof by refutation!

**Aturan Inferensi Dasar:**

| Aturan | Formula | Contoh |
|--------|---------|--------|
| **Modus Ponens** | P, P → Q ⊢ Q | Hujan, Hujan→Basah ⊢ Basah |
| **Modus Tollens** | ¬Q, P → Q ⊢ ¬P | ¬Basah, Hujan→Basah ⊢ ¬Hujan |
| **And-Elimination** | P ∧ Q ⊢ P | Hujan∧Dingin ⊢ Hujan |
| **And-Introduction** | P, Q ⊢ P ∧ Q | Hujan, Dingin ⊢ Hujan∧Dingin |
| **Or-Introduction** | P ⊢ P ∨ Q | Hujan ⊢ Hujan∨Salju |
| **Disjunctive Syllogism** | P ∨ Q, ¬P ⊢ Q | Hujan∨Salju, ¬Hujan ⊢ Salju |
| **Resolution** | P ∨ Q, ¬P ∨ R ⊢ Q ∨ R | Inferensi umum |

![Aturan Inferensi](images/p09-03-inference-rules.png)

*Gambar 9.3: Aturan inferensi dasar dalam logika proposisional*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Aturan inferensi logika proposisional - Modus Ponens, Modus Tollens, Resolution, dan aturan lainnya
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Grid of cards, each showing one inference rule
COLORS: 
- Primary: #2563eb (blue) for rule cards
- Secondary: #10b981 (green) for premises
- Accent: #f59e0b (orange) for conclusions
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Six cards in 3x2 grid:
   - Card 1: "Modus Ponens" with P, P→Q above line, Q below line
   - Card 2: "Modus Tollens" with ¬Q, P→Q above line, ¬P below line
   - Card 3: "And-Elimination" with P∧Q above line, P below line
   - Card 4: "And-Introduction" with P, Q above line, P∧Q below line
   - Card 5: "Disjunctive Syllogism" with P∨Q, ¬P above line, Q below line
   - Card 6: "Resolution" with P∨Q, ¬P∨R above line, Q∨R below line
2. Each card has horizontal line separating premises from conclusion
3. Arrow or "therefore" symbol (∴) at conclusion
LABELS: All rule names in Indonesian and English, premise labels "Premis", conclusion label "Kesimpulan"
SIZE: 900x600 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Rules of Inference - Discrete Mathematics | Neso Academy | 14:52 | https://www.youtube.com/watch?v=XXRk8sbnMHo |
| 2 | Modus Ponens & Modus Tollens | TrevTutor | 10:15 | https://www.youtube.com/watch?v=3TJiQCLkfJE |
| 3 | Inference in AI - Knowledge Representation | Gate Smashers | 12:30 | https://www.youtube.com/watch?v=W0tdCJoExTk |

### ✍️ Latihan Problem Solving

**Problem 1:** Cyber Defense Scenario:
```
KB:
1. Jika ada aktivitas mencurigakan, maka tingkatkan surveillance (S → T)
2. Ada aktivitas mencurigakan (S)
```
Kesimpulan apa yang dapat ditarik? Aturan inferensi apa yang digunakan?

**Problem 2:** Military Rules of Engagement:
```
KB:
1. Target_Valid ∧ Authorization → Engage
2. ¬Engage
3. Authorization
```
Apa yang dapat disimpulkan tentang Target_Valid?

**Problem 3:** Rantai Inferensi:
```
KB:
1. Rain → Wet
2. Wet → Slippery
3. Slippery → Dangerous
4. Rain
```
Buktikan: Dangerous (gunakan aturan inferensi langkah demi langkah)

**Problem 4:** Military Intelligence:
```
KB:
1. Enemy_Detected → Alert
2. Alert ∧ Threat_Level_High → Scramble_Jets
3. Enemy_Detected
4. Threat_Level_High
```
Derive: Scramble_Jets (tunjukkan setiap langkah dan aturan yang digunakan)

---

## 5. Pendalaman: CNF dan Resolution (75 menit)

### Ringkasan Materi

**Conjunctive Normal Form (CNF)** adalah format standar di mana formula logika diekspresikan sebagai konjungsi dari klausa-klausa disjungsi literal.

**Format CNF:** (L₁ ∨ L₂ ∨ ...) ∧ (L₃ ∨ L₄ ∨ ...) ∧ ...

dimana setiap L adalah **literal** (proposisi P atau negasinya ¬P).

**Langkah Konversi ke CNF:**
1. Eliminasi bikonditional (↔): ganti P ↔ Q dengan (P → Q) ∧ (Q → P)
2. Eliminasi implikasi (→): ganti P → Q dengan ¬P ∨ Q
3. Pindahkan NOT ke dalam: gunakan De Morgan's Law dan double negation
4. Distribusi OR over AND: P ∨ (Q ∧ R) menjadi (P ∨ Q) ∧ (P ∨ R)

**Contoh Konversi:**
```
Formula: (P → Q) ∧ (Q → R)
Step 1: (¬P ∨ Q) ∧ (¬Q ∨ R)  ← sudah dalam CNF!
```

**Algoritma Resolution** adalah metode pembuktian yang **sound dan complete** untuk propositional logic:
1. Konversi KB dan **negasi goal** ke CNF
2. Cari dua klausa yang mengandung literal komplementer (P dan ¬P)
3. Resolve mereka untuk menghasilkan resolvent baru
4. Tambahkan resolvent ke KB
5. Ulangi sampai derive **empty clause** (⊥) atau tidak ada resolvent baru

**Jika empty clause (⊥) ditemukan** → KB ∧ ¬Goal unsatisfiable → **KB ⊨ Goal terbukti**

![Proses Resolution](images/p09-04-resolution-algorithm.png)

*Gambar 9.4: Algoritma resolution untuk proving entailment*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Algoritma resolution untuk pembuktian dalam logika proposisional - flowchart dan contoh
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Two-column layout - left side shows flowchart, right side shows example
COLORS: 
- Primary: #2563eb (blue) for flowchart boxes
- Secondary: #10b981 (green) for clauses
- Accent: #f59e0b (orange) for resolution steps
- Warning: #ef4444 (red) for empty clause/contradiction
- Neutral: #6b7280 (gray) for arrows
- Background: #ffffff (white)
ELEMENTS:
Left column - Flowchart:
1. Start box: "KB dan ¬Goal ke CNF"
2. Process box: "Pilih 2 klausa dengan literal komplementer"
3. Process box: "Resolve → buat resolvent"
4. Decision diamond: "Resolvent = ⊥?"
5. Yes path to: "TERBUKTI" (green box)
6. No path loops back with: "Tambah resolvent ke KB"
7. Check: "Ada resolvent baru?" - No leads to "TIDAK TERBUKTI"
Right column - Example:
1. Box showing initial clauses: "¬P∨Q", "¬Q∨R", "P", "¬R"
2. Arrow showing resolution steps with complementary literals highlighted
3. Final empty clause shown in red
ARROWS/CONNECTIONS: Flow arrows between steps, resolution lines between clauses
LABELS: "CNF", "Resolve", "Resolvent", "Klausa Kosong", "Terbukti", "Literal Komplementer"
SIZE: 900x700 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Resolution in Propositional Logic | Neso Academy | 16:30 | https://www.youtube.com/watch?v=PMm5Mat0MRA |
| 2 | CNF and Resolution Proof | Easy Theory | 12:45 | https://www.youtube.com/watch?v=rNHcYy4gFnQ |
| 3 | Resolution - Artificial Intelligence | Gate Smashers | 11:20 | https://www.youtube.com/watch?v=B3g7fi4MhKA |

### ✍️ Latihan Problem Solving

**Problem 1: Konversi ke CNF**

Konversi formula berikut ke CNF:
- a) (P → Q) ∧ (R ∨ ¬Q)
- b) ¬((P ∧ Q) ∨ (R → S))
- c) (P ↔ Q) → R

**Problem 2: Resolution Proof**
```
KB:
1. P ∨ Q
2. ¬P ∨ R
3. ¬Q ∨ S
4. ¬R ∨ T
5. ¬S ∨ T
```
Buktikan: T (gunakan algoritma resolution step-by-step)

**Problem 3: Resolution dalam Konteks Pertahanan**
```
KB:
1. Radar_Deteksi → (Ancaman_Udara ∨ Objek_Sipil)
2. Ancaman_Udara → Aktifkan_SAM
3. ¬IFF_Response → ¬Objek_Sipil
4. Radar_Deteksi
5. ¬IFF_Response
```
Buktikan: Aktifkan_SAM

---

## 6. Latihan Soal Komprehensif (60 menit)

### Soal Set A: Representasi Pengetahuan

**Soal 1:** Representasikan aturan berikut dalam logika proposisional:

"Dalam operasi militer, jika musuh terdeteksi DAN kondisi cuaca mendukung, MAKA luncurkan serangan ATAU tingkatkan pengawasan. Namun serangan hanya diluncurkan jika ada otorisasi dari komandan."

Definisikan proposisi yang diperlukan dan tuliskan formula logikanya.

**Soal 2:** Diberikan knowledge base sistem keamanan fasilitas militer:
```
1. Kartu_Valid ∧ Biometrik_Match → Akses_Granted
2. ¬Kartu_Valid → Alarm
3. Akses_Granted → Log_Entry
4. Alarm → Notifikasi_Security
```
Jika diketahui Kartu_Valid = True dan Biometrik_Match = True, apa saja yang dapat disimpulkan?

### Soal Set B: Tabel Kebenaran dan Satisfiability

**Soal 3:** Tentukan apakah formula berikut valid, satisfiable, atau unsatisfiable. Buktikan dengan tabel kebenaran!
- a) P ∨ ¬P
- b) P ∧ ¬P
- c) (P → Q) ∨ (Q → P)

**Soal 4:** Berikan model (assignment of truth values) yang membuat formula berikut True:
```
(P → Q) ∧ (Q → R) ∧ P ∧ ¬R
```
Jika tidak ada model yang memenuhi, jelaskan mengapa!

### Soal Set C: Inferensi

**Soal 5:** Dalam sistem keamanan siber:
```
KB:
1. Anomali_Trafik → Scan_System
2. Scan_System ∧ Malware_Ditemukan → Isolasi_Network
3. Isolasi_Network → Lapor_CSIRT
4. Anomali_Trafik
5. Malware_Ditemukan
```
Derive: Lapor_CSIRT. Tunjukkan setiap langkah inferensi dan aturan yang digunakan!

**Soal 6:** Berikan contoh penggunaan setiap aturan inferensi berikut dalam konteks militer:
- a) Modus Ponens
- b) Modus Tollens
- c) Disjunctive Syllogism

### Soal Set D: CNF dan Resolution

**Soal 7:** Konversi ke CNF dan buktikan menggunakan resolution:
```
KB: {P → Q, Q → R, R → S, P}
Buktikan: S
```

**Soal 8:** Dalam Wumpus World 4×4:
- Agen di (1,1): tidak ada Breeze, tidak ada Stench
- Agen pindah ke (1,2): ada Breeze
- Agen pindah ke (2,1): tidak ada Breeze

Dengan aturan: Breeze di sel X ↔ ada Pit di sel yang bertetangga dengan X

Gunakan inferensi logika untuk menentukan: di sel mana kemungkinan ada Pit?

### Soal Set E: Aplikasi Wumpus World

**Soal 9:** Dalam Wumpus World, agen memiliki KB berikut:
```
1. ¬P₁,₁ (tidak ada Pit di (1,1) — start)
2. B₁,₁ ↔ (P₁,₂ ∨ P₂,₁)
3. B₂,₁ ↔ (P₁,₁ ∨ P₂,₂ ∨ P₃,₁)
4. ¬B₁,₁ (tidak ada Breeze di (1,1))
5. ¬B₂,₁ (tidak ada Breeze di (2,1))
```
Gunakan inferensi untuk membuktikan: ¬P₁,₂ ∧ ¬P₂,₁ (tidak ada Pit di (1,2) dan (2,1))

---

## 7. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. **Keterbatasan Logika Proposisional**: Apa yang tidak bisa direpresentasikan dengan baik menggunakan propositional logic? (Hint: pikirkan tentang "semua", "ada", objek dengan properties — ini mengarah ke materi Pertemuan 10)

2. **Aplikasi Pertahanan**: Berikan 3 contoh konkret sistem pertahanan Indonesia yang dapat menggunakan propositional logic untuk decision making. Jelaskan proposisi dan aturan yang diperlukan!

3. **Trade-offs**: Dalam sistem real-time (seperti missile defense), apa trade-off antara completeness of logical reasoning vs speed of response?

4. **Scalability**: Jika knowledge base memiliki 1000 proposisi, berapa banyak rows dalam truth table lengkap? Apakah pendekatan truth table masih praktis? Apa alternatifnya?

5. **Uncertainty**: Logika proposisional bersifat binary (true/false). Bagaimana menangani uncertainty dalam aplikasi nyata seperti "kemungkinan 70% target adalah musuh"? (Hint: ini mengarah ke materi Pertemuan 11-12 tentang probabilitas dan Bayesian Network)

### 💬 Topik Diskusi

**Diskusi 1: Ethics in Automated Military Systems**
Jika sistem pertahanan menggunakan pure logic untuk decision making:
- Apakah etis untuk fully automate decisions to engage?
- Bagaimana incorporate humanitarian considerations ke dalam KB?
- Apa peran human-in-the-loop?

**Diskusi 2: Real-world Limitations**
Diskusikan gap antara teori (perfect logic) dan praktik (noisy sensors, incomplete information) dalam sistem militer. Bagaimana logika proposisional menangani sensor yang kadang salah?

**Diskusi 3: Next Step — First-Order Logic**
Apa yang perlu ditambahkan ke propositional logic untuk merepresentasikan:
- "Semua pesawat TNI AU memiliki transponder"
- "Ada radar yang dapat mendeteksi stealth aircraft"

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Pengantar Logika Proposisional selesai
- [ ] Section 2: Review Konnektif Logika dan Tabel Kebenaran selesai
- [ ] Section 3: Tools interaktif dieksplorasi
- [ ] Section 4: Pendalaman Inferensi dan Aturan Inferensi selesai
- [ ] Section 5: Pendalaman CNF dan Resolution selesai
- [ ] Section 6: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 7: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS50 AI - Knowledge | Harvard edX | https://cs50.harvard.edu/ai/2024/weeks/1/ |
| Logic for Computer Science | Stanford Lagunita | https://online.stanford.edu/courses/soe-ycs0001-logic |
| Intro to Logic | Coursera (Stanford) | https://www.coursera.org/learn/logic-introduction |

### 📚 Buku & Artikel Online

- **Artificial Intelligence: A Modern Approach** (Russell & Norvig) — Chapter 7 [Referensi Utama]
- **Logic in Computer Science** — https://www.cs.cmu.edu/~fp/courses/15317-f17/
- **Logic and Automated Reasoning** — MIT OCW Materials
- **Introduction to Logic** — Open Logic Project — https://openlogicproject.org/

### 🎥 Channel YouTube Rekomendasi

- **Neso Academy** — Comprehensive discrete math and logic playlist
- **Easy Theory** — Clear explanations of logic concepts
- **MIT OpenCourseWare** — 6.042J Mathematics for Computer Science
- **Gate Smashers** — AI-focused logic and knowledge representation

### 🛠️ Tools Tambahan

| Tool | Purpose | Link |
|------|---------|------|
| NLTK Logic Module | Python library for logic | https://www.nltk.org/howto/logic.html |
| Prover9/Mace4 | Automated theorem prover | https://www.cs.unm.edu/~mccune/prover9/ |
| Coq Proof Assistant | Interactive theorem proving | https://coq.inria.fr/ |
| Z3 Theorem Prover | Microsoft Research SMT solver | https://github.com/Z3Prover/z3 |

### Platform Latihan Online

| Platform | Topik | Link |
|----------|-------|------|
| Logic Problems | Stanford CS103 | https://web.stanford.edu/class/cs103/tools/practice-problems/ |
| Logic Exercises | Carnegie Mellon OLI | http://oli.cmu.edu/courses/logic-proofs/ |
| Proof Checker | Open Logic Project | https://proofs.openlogicproject.org/ |

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

1. **Perbedaan proposisi dan kalimat biasa:**
   - **Proposisi**: Pernyataan yang memiliki nilai kebenaran pasti (benar atau salah)
   - **Kalimat biasa**: Bisa ambigu, tidak selalu memiliki nilai kebenaran jelas
   - Contoh: "Tutup pintu!" bukan proposisi (perintah), "Pintu tertutup" adalah proposisi

2. **Tiga alasan AI memerlukan representasi formal:**
   - **Presisi**: Eliminasi ambiguitas dalam komunikasi mesin-mesin
   - **Inferensi Otomatis**: Memungkinkan sistem menarik kesimpulan secara algoritmik
   - **Verifikasi**: Dapat membuktikan correctness dari reasoning

3. **Contoh proposisi sistem pertahanan udara:**
   - P: "Radar mendeteksi objek pada azimuth 45°"
   - Q: "Objek bergerak dengan kecepatan > 500 knots"
   - R: "Objek tidak merespon IFF interrogation"

### Section 2

1. **Truth table (P ∧ Q) → R:**

| P | Q | R | P ∧ Q | (P ∧ Q) → R |
|---|---|---|-------|-------------|
| T | T | T | T | T |
| T | T | F | T | **F** |
| T | F | T | F | T |
| T | F | F | F | T |
| F | T | T | F | T |
| F | T | F | F | T |
| F | F | T | F | T |
| F | F | F | F | T |

2. **Representasi sistem radar:** A ↔ (P ∧ Q) — Alert aktif jika dan hanya jika objek terdeteksi DAN bergerak cepat.

3. **Bukti equivalence P → Q ≡ ¬P ∨ Q:**

| P | Q | P → Q | ¬P | ¬P ∨ Q |
|---|---|-------|----|--------|
| T | T | T | F | T |
| T | F | F | F | F |
| F | T | T | T | T |
| F | F | T | T | T |

Kolom (P → Q) identik dengan (¬P ∨ Q) → **ekuivalen** ✓

### Section 4

**Problem 1:**
- Kesimpulan: "Tingkatkan surveillance" (T)
- Aturan: **Modus Ponens** — dari S dan S → T, derive T

**Problem 2:**
- Dari Modus Tollens pada premise 1 dan 2: ¬(Target_Valid ∧ Authorization)
- De Morgan's Law: ¬Target_Valid ∨ ¬Authorization
- Dari premise 3 (Authorization = True): **¬Target_Valid**
- Kesimpulan: Target tidak valid

**Problem 3:**
1. Rain (premise 4)
2. Rain → Wet (premise 1), Rain ⊢ Wet [Modus Ponens]
3. Wet → Slippery (premise 2), Wet ⊢ Slippery [Modus Ponens]
4. Slippery → Dangerous (premise 3), Slippery ⊢ **Dangerous** [Modus Ponens] ✓

**Problem 4:**
1. Enemy_Detected (premise 3)
2. Enemy_Detected → Alert (premise 1), Enemy_Detected ⊢ Alert [Modus Ponens]
3. Alert, Threat_Level_High (premise 4) ⊢ Alert ∧ Threat_Level_High [And-Introduction]
4. Alert ∧ Threat_Level_High → Scramble_Jets (premise 2) ⊢ **Scramble_Jets** [Modus Ponens] ✓

### Section 5

**Problem 2: Resolution Proof untuk T**

Klausa awal:
- C1: {P, Q}
- C2: {¬P, R}
- C3: {¬Q, S}
- C4: {¬R, T}
- C5: {¬S, T}
- C6: {¬T} ← negasi goal

Resolution steps:
| Step | Resolve | Komplementer | Hasil |
|------|---------|-------------|-------|
| R1 | C1 + C2 | P, ¬P | C7: {Q, R} |
| R2 | C7 + C3 | Q, ¬Q | C8: {R, S} |
| R3 | C8 + C4 | R, ¬R | C9: {S, T} |
| R4 | C9 + C6 | T, ¬T | C10: {S} |
| R5 | C10 + C5 | S, ¬S | C11: {T} |
| R6 | C11 + C6 | T, ¬T | **∅** (empty clause) |

Empty clause ditemukan → KB ⊨ T **terbukti** ✓

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
