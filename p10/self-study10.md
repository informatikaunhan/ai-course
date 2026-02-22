# Panduan Belajar Mandiri Pertemuan 10: Representasi Pengetahuan - Logika Predikat (First-Order Logic)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 10  
**Topik:** Representasi Pengetahuan - Logika Predikat (First-Order Logic)  
**Estimasi Waktu:** 495 menit (~8 jam)  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan aktivitas belajar mandiri ini, mahasiswa diharapkan mampu:

1. Menjelaskan keterbatasan logika proposisional dan keunggulan logika predikat (FOL)
2. Merepresentasikan pengetahuan dunia nyata menggunakan sintaks FOL (konstanta, variabel, predikat, fungsi, kuantor)
3. Melakukan proses unifikasi dan menemukan Most General Unifier (MGU)
4. Menerapkan forward chaining dan backward chaining untuk inferensi dalam FOL
5. Mengaplikasikan resolution dalam FOL untuk pembuktian otomatis

---

## 1. Review Konsep: Keterbatasan Logika Proposisional dan Sintaks FOL (45 menit)

### Ringkasan Materi

**Mengapa Logika Proposisional Tidak Cukup?**

Logika proposisional (Pertemuan 9) memiliki tiga keterbatasan fundamental yang membuat representasi pengetahuan dunia nyata menjadi tidak efisien:

1. **Tidak ada objek individual** — tidak dapat merujuk pada entitas spesifik (misalnya "Drone Alpha-7")
2. **Tidak ada properti dan relasi** — tidak dapat menyatakan "X adalah drone" atau "X lebih cepat dari Y"
3. **Tidak ada kuantifikasi** — tidak dapat menyatakan "semua" atau "ada sesuatu" secara umum

**Contoh Perbandingan:**

| Pernyataan | Logika Proposisional | FOL |
|------------|---------------------|----|
| "Semua tentara harus berani" | P₁ ⇒ Q₁, P₂ ⇒ Q₂, ... (per orang) | ∀x [Tentara(x) ⇒ Berani(x)] |
| "Ada kapal selam di Natuna" | P = "Ada kapal selam..." | ∃x [KapalSelam(x) ∧ DiPerairan(x, Natuna)] |
| "Budi memimpin Kompi Alpha" | P = "Budi memimpin..." | Memimpin(Budi, KompiAlpha) |

**Komponen Sintaks FOL:**

| Komponen | Deskripsi | Contoh |
|----------|-----------|--------|
| **Konstanta** | Objek spesifik | `Budi`, `DroneAlpha7`, `Natuna` |
| **Variabel** | Objek umum | `x`, `y`, `z` |
| **Predikat** | Properti/relasi | `Tentara(x)`, `Memimpin(x, y)` |
| **Fungsi** | Mapping ke objek | `komandan(x)`, `lokasi(x)` |
| **Konnektif** | Penghubung logis | ∧, ∨, ¬, ⇒, ⇔ |
| **Kuantor** | Generalisasi | ∀ (universal), ∃ (eksistensial) |
| **Equality** | Kesamaan objek | `=` |

**Term** dalam FOL adalah ekspresi yang merujuk pada objek: konstanta, variabel, atau fungsi yang diterapkan pada term lain. **Atomic sentence** adalah predikat yang diterapkan pada term, contoh: `Tentara(Budi)`, `LebihCepat(DroneA, DroneB)`.

![Komponen Sintaks FOL](images/p10-ss-01-fol-syntax-components.png)

*Gambar 10.1: Komponen utama sintaks First-Order Logic*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Komponen sintaks First-Order Logic (FOL) - hierarki dari term, atomic sentence, hingga complex sentence
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Hierarchical tree diagram showing FOL syntax components
COLORS: 
- Primary: #2563eb (blue) for main boxes
- Secondary: #10b981 (green) for terms/constants
- Accent: #f59e0b (orange) for predicates/quantifiers
- Warning: #ef4444 (red) for connectives
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Top: "Kalimat FOL (Sentence)" title box
2. Second level left: "Atomic Sentence" box containing "Predikat(term₁, term₂, ...)" and "term₁ = term₂"
3. Second level right: "Complex Sentence" box containing connectives "∧, ∨, ¬, ⇒, ⇔" and quantifiers "∀x, ∃x"
4. Third level under Atomic: "Term" box branching to "Konstanta", "Variabel", "Fungsi(term)"
5. Examples below each: Konstanta→"Budi, DroneA", Variabel→"x, y", Fungsi→"komandan(x)"
6. Example sentences at bottom: "∀x [Tentara(x) ⇒ Berani(x)]"
LABELS: All in Indonesian: "Kalimat FOL", "Kalimat Atomik", "Kalimat Kompleks", "Term", "Konstanta", "Variabel", "Fungsi", "Predikat", "Konnektif", "Kuantor"
SIZE: 900x650 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | First-Order Logic: Syntax and Semantics | Stanford CS221 | ~20 min | [Stanford CS221 YouTube](https://www.youtube.com/results?search_query=stanford+cs221+first+order+logic) |
| 2 | First Order Logic in AI (Complete Tutorial) | TutorialsPoint / Gate Smashers | ~15 min | [YouTube Search](https://www.youtube.com/results?search_query=first+order+logic+AI+tutorial+predicate+logic) |
| 3 | Predicate Logic - Building Blocks | NPTEL IIT Kanpur (Dr. A.V. Ravishankar Sarma) | ~55 min | [NPTEL Lecture 34](https://www.youtube.com/results?search_query=NPTEL+predicate+logic+building+blocks+IIT+Kanpur) |

### ✍️ Latihan Pemahaman

1. Mengapa pernyataan "Semua drone harus melapor ke command center" tidak dapat direpresentasikan secara efisien dalam logika proposisional? Jelaskan dengan contoh!

2. Identifikasi komponen FOL berikut (konstanta, variabel, predikat, fungsi) dari kalimat:
   ∀x [Pilot(x) ∧ Bertugas(x, SkuadronAlpha) ⇒ Terampil(x, komandan(SkuadronAlpha))]

3. Tuliskan FOL untuk: "Ada seorang prajurit yang lebih berani dari semua prajurit lainnya."

### ✅ Checklist Pemahaman Section 1

- [ ] Saya dapat menjelaskan 3 keterbatasan utama logika proposisional
- [ ] Saya dapat mengidentifikasi konstanta, variabel, predikat, dan fungsi dalam kalimat FOL
- [ ] Saya dapat membuat atomic sentence dan complex sentence dalam FOL

---

## 2. Review Konsep: Kuantor dan Representasi Pengetahuan (45 menit)

### Ringkasan Materi

**Kuantor Universal (∀) — "Untuk Semua"**

Menyatakan bahwa suatu properti berlaku untuk semua objek dalam domain.

- Bentuk umum: ∀x [P(x)]
- Biasanya digunakan dengan **implikasi (⇒)**: ∀x [Tentara(x) ⇒ Berani(x)]
- **Peringatan:** ∀x [Tentara(x) ∧ Berani(x)] berarti "semua objek di dunia adalah tentara yang berani" — ini biasanya SALAH!

**Kuantor Eksistensial (∃) — "Ada"**

Menyatakan bahwa ada setidaknya satu objek yang memenuhi properti.

- Bentuk umum: ∃x [P(x)]
- Biasanya digunakan dengan **konjungsi (∧)**: ∃x [KapalSelam(x) ∧ DiPerairan(x, Natuna)]
- **Peringatan:** ∃x [KapalSelam(x) ⇒ DiPerairan(x, Natuna)] terlalu lemah — terpenuhi jika ada objek apapun yang bukan kapal selam!

**Hubungan Antar Kuantor (De Morgan untuk Kuantor):**

| Equivalensi | Penjelasan |
|-------------|------------|
| ∀x P(x) ≡ ¬∃x ¬P(x) | "Semua P" sama dengan "tidak ada yang bukan P" |
| ∃x P(x) ≡ ¬∀x ¬P(x) | "Ada P" sama dengan "tidak semua bukan P" |
| ¬∀x P(x) ≡ ∃x ¬P(x) | "Tidak semua P" sama dengan "ada yang bukan P" |
| ¬∃x P(x) ≡ ∀x ¬P(x) | "Tidak ada P" sama dengan "semua bukan P" |

**Nested Quantifiers:**

Urutan kuantor penting ketika menggunakan kuantor berbeda:
- ∀x ∃y Cinta(x, y) = "Setiap orang mencintai seseorang" (beda orang bisa cinta orang beda)
- ∃y ∀x Cinta(x, y) = "Ada seseorang yang dicintai semua orang" (satu orang spesifik)

**Pola Representasi Pengetahuan dalam FOL:**

| Pola Bahasa Indonesia | Pola FOL |
|----------------------|----------|
| Semua X yang Y adalah Z | ∀x [X(x) ∧ Y(x) ⇒ Z(x)] |
| Ada X yang Y dan Z | ∃x [X(x) ∧ Y(x) ∧ Z(x)] |
| Tidak ada X yang Y | ¬∃x [X(x) ∧ Y(x)] atau ∀x [X(x) ⇒ ¬Y(x)] |
| Hanya X yang Y | ∀x [Y(x) ⇒ X(x)] |
| Tepat satu X yang Y | ∃x [Y(x) ∧ ∀z [Y(z) ⇒ z = x]] |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Quantifiers in First-Order Logic | Neso Academy | ~12 min | [YouTube Search](https://www.youtube.com/results?search_query=neso+academy+quantifiers+first+order+logic) |
| 2 | Lecture 35: Quantifiers, Freedom, Bondage | NPTEL IIT Kanpur | ~55 min | [NPTEL FOL Quantifiers](https://www.youtube.com/results?search_query=NPTEL+IIT+Kanpur+quantifiers+freedom+bondage+predicate+logic) |
| 3 | FOL: Translating English to Predicate Logic | Gate Smashers | ~15 min | [YouTube Search](https://www.youtube.com/results?search_query=gate+smashers+first+order+logic+translation+english) |

### ✍️ Latihan Pemahaman

1. Representasikan dalam FOL: "Semua pesawat tempur yang terdeteksi radar harus dicegat oleh interceptor."

2. Jelaskan perbedaan makna antara:
   - ∀x ∃y Melaporkan(x, y)
   - ∃y ∀x Melaporkan(x, y)
   dalam konteks "prajurit melaporkan kepada atasan."

3. Representasikan dalam FOL: "Tidak ada drone musuh yang berhasil melewati zona pertahanan tanpa terdeteksi."

4. Mana yang benar untuk "Setiap pilot memiliki pesawat"?
   - (a) ∀x [Pilot(x) ∧ ∃y [Pesawat(y) ∧ Memiliki(x, y)]]
   - (b) ∀x [Pilot(x) ⇒ ∃y [Pesawat(y) ∧ Memiliki(x, y)]]
   Jelaskan alasannya!

### ✅ Checklist Pemahaman Section 2

- [ ] Saya memahami perbedaan ∀ dengan ⇒ dan ∃ dengan ∧
- [ ] Saya dapat menerjemahkan kalimat bahasa Indonesia ke FOL
- [ ] Saya memahami pengaruh urutan nested quantifiers
- [ ] Saya menguasai equivalensi De Morgan untuk kuantor

---

## 3. Review Konsep: Unifikasi dan Most General Unifier (45 menit)

### Ringkasan Materi

**Unifikasi** adalah proses menemukan substitusi yang membuat dua ekspresi logis menjadi identik. Ini adalah mekanisme fundamental yang digunakan oleh semua teknik inferensi dalam FOL.

**Definisi Formal:**
- Diberikan dua literal ψ₁ dan ψ₂, **unifier** adalah substitusi θ sedemikian sehingga ψ₁θ = ψ₂θ
- **Most General Unifier (MGU)** adalah unifier yang paling umum (tidak lebih spesifik dari yang diperlukan)

**Aturan Unifikasi:**

| Kasus | Aturan | Contoh |
|-------|--------|--------|
| Konstanta sama | Berhasil, θ = {} | UNIFY(Budi, Budi) = {} |
| Konstanta beda | **Gagal** | UNIFY(Budi, Andi) = FAIL |
| Variabel + Term | θ = {x/term} | UNIFY(x, Budi) = {x/Budi} |
| Fungsi sama | Unifikasi rekursif argumen | UNIFY(f(x), f(Budi)) = {x/Budi} |
| Fungsi beda | **Gagal** | UNIFY(f(x), g(x)) = FAIL |
| **Occur Check** | Variabel muncul dalam term → **Gagal** | UNIFY(x, f(x)) = FAIL |

**Langkah-Langkah Algoritma Unifikasi:**

1. Jika kedua ekspresi identik → kembalikan substitusi kosong {}
2. Jika salah satu variabel → substitusikan (dengan occur check)
3. Jika keduanya fungsi/predikat → periksa nama sama dan arity sama, lalu unifikasi argumen secara rekursif
4. Selain itu → GAGAL

**Contoh Detail:**

UNIFY(Knows(John, x), Knows(John, Jane))
- Predikat: Knows = Knows ✓
- Argumen 1: John = John ✓ (identik)
- Argumen 2: x vs Jane → θ = {x/Jane}
- **MGU = {x/Jane}**

UNIFY(Knows(John, x), Knows(y, Bill))
- Predikat: Knows = Knows ✓
- Argumen 1: John vs y → θ₁ = {y/John}
- Argumen 2: x vs Bill → θ₂ = {x/Bill}
- **MGU = {y/John, x/Bill}**

UNIFY(Knows(John, x), Knows(x, Jane))
- Argumen 1: John vs x → θ₁ = {x/John}
- Terapkan θ₁ ke argumen 2: John vs Jane → **GAGAL** (konstanta berbeda!)

![Proses Unifikasi FOL](images/p10-ss-02-unification-process.png)

*Gambar 10.2: Proses unifikasi step-by-step pada dua ekspresi FOL*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Proses unifikasi step-by-step dalam First-Order Logic, menunjukkan bagaimana dua ekspresi menjadi identik melalui substitusi
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Flowchart showing unification steps from top to bottom
COLORS: 
- Primary: #2563eb (blue) for expression boxes
- Secondary: #10b981 (green) for successful unification steps
- Accent: #f59e0b (orange) for substitution arrows
- Warning: #ef4444 (red) for failed cases
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Top: Two expression boxes side by side "Knows(John, x)" and "Knows(y, Bill)"
2. Step arrows pointing down showing comparison:
   - Step 1: "Predikat: Knows = Knows ✓" (green)
   - Step 2: "Arg 1: John vs y → θ = {y/John}" (orange arrow)
   - Step 3: "Arg 2: x vs Bill → θ = {x/Bill}" (orange arrow)
3. Bottom: Result box "MGU = {y/John, x/Bill}" in green
4. Side panel: Failed case "Knows(John, x) vs Knows(x, Jane)" with red X showing conflict
LABELS: All in Indonesian: "Ekspresi 1", "Ekspresi 2", "Langkah", "Substitusi", "Hasil MGU", "Gagal"
SIZE: 900x700 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Unification in First Order Logic | Gate Smashers | ~15 min | [YouTube Search](https://www.youtube.com/results?search_query=gate+smashers+unification+first+order+logic+MGU) |
| 2 | Unification Algorithm Step by Step | Knowledge Gate | ~20 min | [YouTube Search](https://www.youtube.com/results?search_query=unification+algorithm+first+order+logic+step+by+step+examples) |
| 3 | Unification in FOL (with Occur Check) | Neso Academy | ~12 min | [YouTube Search](https://www.youtube.com/results?search_query=neso+academy+unification+FOL+occur+check) |

### ✍️ Latihan Pemahaman

1. Tentukan MGU untuk pasangan berikut (atau nyatakan GAGAL):
   - (a) P(x, B) dan P(A, y)
   - (b) P(x, f(x)) dan P(A, y)
   - (c) P(x, x) dan P(A, B)
   - (d) P(f(x), y) dan P(y, f(A))

2. Jelaskan mengapa occur check diperlukan! Apa yang terjadi tanpa occur check pada UNIFY(x, f(x))?

3. Berikan contoh dua ekspresi yang memiliki lebih dari satu unifier, dan tunjukkan mana yang merupakan MGU!

### ✅ Checklist Pemahaman Section 3

- [ ] Saya dapat menjalankan algoritma unifikasi langkah per langkah
- [ ] Saya dapat menemukan MGU untuk dua ekspresi FOL
- [ ] Saya memahami occur check dan kapan unifikasi gagal
- [ ] Saya dapat membedakan MGU dari unifier yang lebih spesifik

---

## 4. Review Konsep: Forward Chaining dan Backward Chaining (45 menit)

### Ringkasan Materi

Setelah pengetahuan direpresentasikan dalam FOL, kita memerlukan mekanisme inferensi untuk menarik kesimpulan baru. Dua strategi utama adalah **forward chaining** (data-driven) dan **backward chaining** (goal-driven).

**Forward Chaining (Penalaran Maju):**

- Dimulai dari **fakta yang diketahui** di Knowledge Base
- Menerapkan **semua aturan** yang premisnya terpenuhi
- Menghasilkan **fakta baru** yang ditambahkan ke KB
- Berulang sampai **tidak ada fakta baru** atau **query terjawab**
- Analogi: "Dari apa yang saya tahu, apa yang bisa saya simpulkan?"

**Contoh Forward Chaining:**

KB berisi:
1. Tentara(Budi)
2. BerdinasAktif(Budi)
3. ∀x [Tentara(x) ∧ BerdinasAktif(x) ⇒ WajibLatihan(x)]

Iterasi 1: Aturan 3 match dengan Fakta 1 dan 2 → **WajibLatihan(Budi)** ditambahkan ke KB

**Backward Chaining (Penalaran Mundur):**

- Dimulai dari **query/goal** yang ingin dibuktikan
- Mencari **aturan** yang kesimpulannya match dengan goal
- Premis aturan menjadi **sub-goals** baru
- Berulang sampai semua sub-goals terbukti dari **fakta di KB**
- Analogi: "Untuk membuktikan X, apa yang perlu saya tunjukkan?"

**Contoh Backward Chaining:**

Query: WajibLatihan(Budi)?
1. Cari aturan dengan kesimpulan WajibLatihan(x) → Aturan 3: Tentara(x) ∧ BerdinasAktif(x) ⇒ WajibLatihan(x), θ = {x/Budi}
2. Sub-goal 1: Tentara(Budi)? → Ada di KB ✓
3. Sub-goal 2: BerdinasAktif(Budi)? → Ada di KB ✓
4. Semua sub-goals terbukti → **WajibLatihan(Budi) = TRUE**

**Perbandingan:**

| Aspek | Forward Chaining | Backward Chaining |
|-------|-----------------|-------------------|
| Arah | Data → Kesimpulan | Goal → Data |
| Strategi | Bottom-up | Top-down |
| Kapan cocok | Banyak data baru masuk | Ada pertanyaan spesifik |
| Efisiensi | Bisa generate fakta tak relevan | Fokus pada yang diperlukan |
| Completeness | Complete untuk definite clauses | Complete untuk definite clauses |
| Contoh aplikasi | Monitoring/alert system | Diagnostic/query system |
| Analog militer | Situational awareness | Intelligence query |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Forward & Backward Chaining in AI | Gate Smashers | ~20 min | [YouTube Search](https://www.youtube.com/results?search_query=gate+smashers+forward+backward+chaining+AI+first+order+logic) |
| 2 | Inference in First-Order Logic | NPTEL IIT Madras (Prof. Deepak Khemani) | ~55 min | [YouTube Search](https://www.youtube.com/results?search_query=NPTEL+Deepak+Khemani+inference+first+order+logic+backward+chaining) |
| 3 | Forward Chaining Algorithm FOL | Applied AI Course | ~15 min | [YouTube Search](https://www.youtube.com/results?search_query=forward+chaining+algorithm+first+order+logic+AI+example) |

### ✍️ Latihan Pemahaman

1. Diberikan KB berikut, lakukan forward chaining untuk menemukan semua fakta baru:
   - Fakta: Perwira(Andi), Terlatih(Andi), BerdinasAktif(Andi)
   - Aturan 1: ∀x [Perwira(x) ∧ Terlatih(x) ⇒ BolehMemimpin(x)]
   - Aturan 2: ∀x [BolehMemimpin(x) ∧ BerdinasAktif(x) ⇒ KomandanPleton(x)]

2. Gunakan backward chaining untuk membuktikan KomandanPleton(Andi) dari KB di atas. Gambarkan proof tree-nya!

3. Dalam konteks apa forward chaining lebih cocok dibandingkan backward chaining untuk sistem C2 (Command and Control)? Berikan contoh konkret!

### ✅ Checklist Pemahaman Section 4

- [ ] Saya dapat menjalankan forward chaining langkah per langkah
- [ ] Saya dapat menjalankan backward chaining dan menggambar proof tree
- [ ] Saya memahami perbedaan kapan menggunakan masing-masing strategi
- [ ] Saya dapat mengidentifikasi aplikasi forward/backward chaining di dunia nyata

---

## 5. Review Konsep: Resolution dalam FOL dan Aplikasi (45 menit)

### Ringkasan Materi

**Resolution** adalah teknik inferensi yang powerful dan complete untuk FOL. Ia bekerja dengan pembuktian kontradiksi (refutation): untuk membuktikan KB ⊨ α, kita menunjukkan bahwa KB ∧ ¬α menghasilkan kontradiksi (empty clause).

**Langkah-Langkah Resolution dalam FOL:**

1. **Konversi ke CNF (Conjunctive Normal Form):**
   - Eliminasi implikasi (⇒): P ⇒ Q menjadi ¬P ∨ Q
   - Pindahkan negasi ke dalam: ¬∀x P(x) menjadi ∃x ¬P(x)
   - Standardisasi variabel (rename jika perlu)
   - **Skolemisasi**: Ganti ∃y dengan Skolem constant/function
     - ∃x P(x) → P(A) dimana A adalah Skolem constant
     - ∀x ∃y P(x, y) → P(x, f(x)) dimana f adalah Skolem function
   - Buang kuantor universal (sudah implisit)
   - Distribusikan ∨ over ∧ untuk mendapatkan CNF

2. **Negasikan goal** dan tambahkan ke KB

3. **Terapkan resolution rule:**
   - Dari clause P ∨ L₁ dan ¬P ∨ L₂, simpulkan L₁ ∨ L₂
   - Gunakan **unifikasi** untuk mencocokkan literal komplementer

4. **Ulangi** sampai mendapat **empty clause {}** (kontradiksi → goal terbukti) atau tidak ada resolusi baru

**Contoh Singkat:**

KB:
1. ∀x [Tentara(x) ⇒ BeraniAtauPatuh(x)]
   → CNF: ¬Tentara(x) ∨ Berani(x) ∨ Patuh(x)
2. Tentara(Budi)
3. ¬Patuh(Budi)

Goal: Berani(Budi)?
Negasi goal: ¬Berani(Budi)

Resolusi:
- Clause 1 + Clause 2: {x/Budi} → Berani(Budi) ∨ Patuh(Budi)
- Hasil + Clause 3: Berani(Budi)
- Hasil + ¬Berani(Budi): {} (empty clause) → **TERBUKTI!**

**Aplikasi FOL dalam AI:**

| Aplikasi | Deskripsi |
|----------|-----------|
| **Expert Systems** | MYCIN (diagnosis medis), R1/XCON (konfigurasi komputer) |
| **Knowledge Graphs** | Google Knowledge Graph, Wikidata — entitas dan relasi dalam FOL |
| **Logic Programming** | Prolog — program = KB + backward chaining |
| **Semantic Web** | OWL (Web Ontology Language) berbasis deskripsi logika subset FOL |
| **Militer** | Sistem inferensi untuk intelligence analysis, threat assessment |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Resolution in First-Order Logic | Knowledge Gate | ~18 min | [YouTube Search](https://www.youtube.com/results?search_query=resolution+first+order+logic+AI+CNF+skolemization) |
| 2 | Skolemization and CNF Conversion | Neso Academy | ~15 min | [YouTube Search](https://www.youtube.com/results?search_query=skolemization+CNF+conversion+first+order+logic+tutorial) |
| 3 | Resolution Method for FOL | NPTEL IIT Madras (KR&R Course) | ~55 min | [YouTube Search](https://www.youtube.com/results?search_query=NPTEL+resolution+refutation+method+first+order+logic) |

### ✍️ Latihan Pemahaman

1. Konversikan ke CNF: ∀x [∃y Teman(x, y) ⇒ ¬Kesepian(x)]

2. Apa itu Skolemisasi? Skolemisasi ekspresi berikut:
   - (a) ∃x Pilot(x)
   - (b) ∀x ∃y Memimpin(x, y)
   - (c) ∀x ∀y ∃z DiAntara(z, x, y)

3. Gunakan resolution untuk membuktikan bahwa dari KB:
   - ∀x [Pilot(x) ⇒ Terampil(x)]
   - Pilot(Citra)
   
   Dapat disimpulkan: Terampil(Citra)

### ✅ Checklist Pemahaman Section 5

- [ ] Saya dapat mengkonversi kalimat FOL ke CNF melalui langkah-langkah standar
- [ ] Saya memahami Skolemisasi dan kapan menggunakan Skolem constant vs function
- [ ] Saya dapat menjalankan resolution refutation step-by-step
- [ ] Saya dapat mengidentifikasi aplikasi FOL di berbagai domain AI

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| No | Tool | Deskripsi | Link |
|----|------|-----------|------|
| 1 | **Tree Proof Generator** | Membuat pohon bukti semantic tableaux untuk FOL | [umsu.de/trees](https://www.umsu.de/trees/) |
| 2 | **Logitext** | Proof assistant untuk logika proposisional dan predikat (MIT) | [logitext.mit.edu](http://logitext.mit.edu/main) |
| 3 | **SWI-Prolog Online** | Interpreter Prolog online untuk bereksperimen dengan backward chaining | [swish.swi-prolog.org](https://swish.swi-prolog.org/) |
| 4 | **AIMA Code Repository** | Implementasi Python algoritma FOL dari buku Russell & Norvig | [github.com/aimacode](https://github.com/aimacode/aima-python) |
| 5 | **TutorialsPoint FOL** | Tutorial interaktif tentang FOL, unifikasi, dan resolution | [tutorialspoint.com](https://www.tutorialspoint.com/artificial_intelligence/artificial_intelligence_first_order_logic.htm) |
| 6 | **GeeksforGeeks FOL** | Artikel dan contoh soal FOL, unifikasi, forward/backward chaining | [geeksforgeeks.org](https://www.geeksforgeeks.org/first-order-logic-in-artificial-intelligence/) |

### Tugas Eksplorasi

**Tugas 1: Tree Proof Generator (15 menit)**
1. Buka [umsu.de/trees](https://www.umsu.de/trees/)
2. Masukkan formula: `\forall x (Fx -> Gx), Fa |- Ga`
3. Amati bagaimana pohon bukti dihasilkan
4. Coba formula dengan nested quantifiers: `\forall x \exists y Rxy |- \exists y Rcy`
5. Screenshot atau catat langkah-langkah bukti yang dihasilkan

**Tugas 2: Prolog dan Backward Chaining (25 menit)**
1. Buka [SWISH Prolog](https://swish.swi-prolog.org/)
2. Masukkan program berikut:
```prolog
% Fakta
tentara(budi).
tentara(andi).
berdinas_aktif(budi).
terlatih(budi).
terlatih(andi).

% Aturan
wajib_latihan(X) :- tentara(X), berdinas_aktif(X).
boleh_memimpin(X) :- tentara(X), terlatih(X).
komandan(X) :- boleh_memimpin(X), berdinas_aktif(X).
```
3. Jalankan query: `?- wajib_latihan(budi).`
4. Jalankan query: `?- komandan(X).`
5. Amati bagaimana Prolog menggunakan backward chaining untuk menjawab query

**Tugas 3: Tutorial Online (20 menit)**
1. Baca tutorial unifikasi di [TutorialsPoint](https://www.tutorialspoint.com/artificial_intelligence/ai_unification_in_first_order_logic_fol.htm)
2. Kerjakan contoh unifikasi yang diberikan secara mandiri (tutup jawaban dulu)
3. Bandingkan jawaban Anda dengan penjelasan di tutorial

### ✅ Checklist Eksplorasi Tools

- [ ] Saya telah menggunakan Tree Proof Generator untuk membuat bukti FOL
- [ ] Saya telah menjalankan program Prolog dan memahami backward chaining secara praktis
- [ ] Saya telah membaca tutorial online dan mengerjakan contoh soal tambahan

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | AI: Knowledge Representation and Reasoning (Week 4-5: FOL) | NPTEL IIT Madras | ~5 jam (pilih yang relevan) | [Class Central](https://www.classcentral.com/course/youtube-artificial-intelligence-knowledge-representation-and-reasoning-47799) |
| 2 | Artificial Intelligence - Lec 45-48 (FOL, Reasoning, Resolution) | NPTEL IIT Madras (Prof. Deepak Khemani) | ~4 × 55 min | [YouTube Search](https://www.youtube.com/results?search_query=NPTEL+Deepak+Khemani+first+order+logic+reasoning+resolution) |
| 3 | Introduction to Logic - Lectures 32-43 (Predicate Logic) | NPTEL IIT Kanpur (Dr. Sarma) | ~12 × 55 min (pilih) | [YouTube Search](https://www.youtube.com/results?search_query=NPTEL+IIT+Kanpur+introduction+logic+predicate+lectures) |
| 4 | CS188 Berkeley: Logic and Planning | UC Berkeley | ~80 min | [YouTube Search](https://www.youtube.com/results?search_query=cs188+berkeley+first+order+logic+planning) |
| 5 | MIT 6.825: First-Order Logic | MIT OCW | ~50 min | [MIT OCW](https://ocw.mit.edu/courses/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/) |

**Panduan Menonton (pilih sesuai waktu):**
- **60 menit tersedia:** Tonton Video 1 (pilih 2-3 lecture dari Week 4-5) atau Video 4
- **Lebih dari 60 menit:** Tambahkan Video 2 (Lec 45: FOL Basics, Lec 48: Resolution)

### 📖 Bacaan Tambahan

- Russell & Norvig, *AIMA* 4th Ed., **Chapter 8** (First-Order Logic) dan **Chapter 9** (Inference in FOL)
- Poole & Mackworth, *AI: Foundations of Computational Agents*, **Chapter 5** (Propositions and Predicate Logic)
- Philipp Koehn, JHU — [Inference in First-Order Logic (Slides)](https://www.cs.jhu.edu/~phi/ai/slides/lecture-inference-in-first-order-logic.pdf)
- AIMA Book Website: [aima.cs.berkeley.edu](http://aima.cs.berkeley.edu/)

### ✅ Checklist Video Lanjutan

- [ ] Saya telah menonton minimal 60 menit video tentang FOL
- [ ] Saya telah membaca Chapter 8-9 AIMA atau sumber bacaan alternatif
- [ ] Saya mencatat poin-poin yang masih membingungkan untuk ditanyakan di kelas

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| No | Platform | Topik | Link |
|----|----------|-------|------|
| 1 | AIMA Exercises | Inference in First-Order Logic | [aimacode.github.io](https://aimacode.github.io/aima-exercises/FOL-exercises/) |
| 2 | GeeksforGeeks | FOL Practice Problems | [geeksforgeeks.org](https://www.geeksforgeeks.org/first-order-logic-in-artificial-intelligence/) |
| 3 | TutorialsPoint | FOL, Unification, Resolution, Chaining | [tutorialspoint.com](https://www.tutorialspoint.com/artificial_intelligence/artificial_intelligence_first_order_logic.htm) |
| 4 | Brilliant.org | Logic & Proofs | [brilliant.org](https://brilliant.org/courses/logic/) |

### Soal Latihan Mandiri

**Soal 1 ⭐ (Representasi FOL)**

Representasikan pernyataan-pernyataan berikut dalam FOL:
- (a) "Setiap kapal perang memiliki komandan"
- (b) "Ada komandan yang memimpin lebih dari satu kapal"
- (c) "Tidak ada kapal selam yang bisa menyelam lebih dari 500 meter tanpa peralatan khusus"
- (d) "Jika seseorang adalah perwira dan terlatih, maka dia boleh mengoperasikan sistem senjata"

**Soal 2 ⭐⭐ (Unifikasi)**

Tentukan MGU atau nyatakan GAGAL:
- (a) UNIFY(Command(x, Armada1), Command(Admiral, y))
- (b) UNIFY(Patrol(x, x), Patrol(Drone1, Drone2))
- (c) UNIFY(Assign(x, squad(y)), Assign(Budi, squad(Alpha)))
- (d) UNIFY(Report(x, superior(x)), Report(Andi, y))
- (e) UNIFY(Mission(f(x), g(y)), Mission(f(A), g(f(A))))

**Soal 3 ⭐⭐ (Forward Chaining)**

Diberikan KB:
- Fakta: Pilot(Reza), Sehat(Reza), HasClearance(Reza), Pesawat(F16Alpha)
- Aturan 1: ∀x [Pilot(x) ∧ Sehat(x) ⇒ FitToFly(x)]
- Aturan 2: ∀x ∀y [FitToFly(x) ∧ HasClearance(x) ∧ Pesawat(y) ⇒ CanFly(x, y)]
- Aturan 3: ∀x ∀y [CanFly(x, y) ⇒ Assigned(x, y)]

Jalankan forward chaining lengkap! Tunjukkan setiap iterasi dan fakta baru yang dihasilkan.

**Soal 4 ⭐⭐ (Backward Chaining)**

Dari KB Soal 3, gunakan backward chaining untuk membuktikan: Assigned(Reza, F16Alpha). Gambarkan proof tree lengkap!

**Soal 5 ⭐⭐⭐ (Resolution)**

Diberikan KB:
- ∀x [Soldier(x) ⇒ Loyal(x) ∨ Discharged(x)]
- Soldier(Private_Ali)
- ¬Discharged(Private_Ali)

Buktikan menggunakan resolution: Loyal(Private_Ali)
Tunjukkan: konversi ke CNF, negasi goal, dan setiap langkah resolusi.

**Soal 6 ⭐⭐⭐ (Skolemisasi dan Resolution)**

Konversikan ke CNF dan buktikan menggunakan resolution:
- ∀x [∃y Friend(x, y) ⇒ ¬Alone(x)]
- ∀x [Soldier(x) ⇒ ∃y Friend(x, y)]
- Soldier(Budi)

Query: ¬Alone(Budi)

**Soal 7 ⭐⭐⭐ (Studi Kasus Militer)**

Sebuah sistem intelligence analysis menggunakan KB berikut:

Fakta:
- Aircraft(ObjectAlpha), DetectedBy(ObjectAlpha, RadarNorth)
- Aircraft(ObjectBeta), DetectedBy(ObjectBeta, RadarSouth)
- HighSpeed(ObjectAlpha), LowAltitude(ObjectAlpha)
- ForeignTransponder(ObjectAlpha)
- FriendlyTransponder(ObjectBeta)

Aturan:
1. ∀x [Aircraft(x) ∧ HighSpeed(x) ∧ LowAltitude(x) ⇒ SuspiciousBehavior(x)]
2. ∀x [Aircraft(x) ∧ ForeignTransponder(x) ⇒ PotentialThreat(x)]
3. ∀x [SuspiciousBehavior(x) ∧ PotentialThreat(x) ⇒ HighThreat(x)]
4. ∀x [HighThreat(x) ⇒ AlertLevel(x, Red)]
5. ∀x [Aircraft(x) ∧ FriendlyTransponder(x) ⇒ Friendly(x)]

(a) Jalankan forward chaining untuk menentukan semua fakta baru  
(b) Gunakan backward chaining untuk menjawab: AlertLevel(ObjectAlpha, Red)?  
(c) Apa level ancaman ObjectBeta? Jelaskan reasoning-nya!

### ✅ Checklist Latihan

- [ ] Saya telah mengerjakan minimal 5 soal dari 7 soal di atas
- [ ] Saya telah memeriksa jawaban saya dengan kunci jawaban
- [ ] Saya telah mengerjakan latihan tambahan dari platform online

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. **Dari Proposisional ke Predikat:** Apa pengalaman Anda beralih dari logika proposisional (Pertemuan 9) ke logika predikat? Konsep apa yang paling sulit dipahami dan bagaimana Anda mengatasinya?

2. **Aplikasi Militer:** Bayangkan Anda merancang knowledge base untuk sistem threat assessment TNI AL. Predikat, fungsi, dan aturan apa saja yang akan Anda definisikan? Bagaimana forward chaining dapat membantu mengidentifikasi ancaman secara real-time?

3. **Keterbatasan FOL:** Meskipun FOL jauh lebih ekspresif dari logika proposisional, apakah FOL cukup untuk merepresentasikan semua pengetahuan? Pikirkan tentang ketidakpastian (misalnya "drone *mungkin* musuh"), temporal reasoning ("drone terdeteksi *kemarin*"), dan default reasoning ("biasanya pesawat sipil *tidak* berbahaya"). Bagaimana keterbatasan ini diatasi? (Petunjuk: Pertemuan 11-12 akan membahas penalaran probabilistik)

4. **FOL vs Machine Learning:** Dalam konteks AI modern, kapan pendekatan berbasis logika (FOL, expert systems) lebih tepat dibandingkan pendekatan machine learning? Berikan contoh konkret dari bidang pertahanan!

5. **Koneksi Interdisiplin:** Bagaimana konsep FOL berhubungan dengan mata kuliah lain yang telah Anda pelajari (Basis Data, Pemrograman Berorientasi Objek, Teori Bahasa dan Automata)?

### 💬 Forum Diskusi Online

- **Reddit:** r/artificial, r/logic, r/learnprogramming
- **Stack Overflow:** Tag [first-order-logic], [prolog], [knowledge-representation]
- **AI Stack Exchange:** [ai.stackexchange.com](https://ai.stackexchange.com/)

### Topik Diskusi yang Disarankan

- Perbandingan representasi pengetahuan: FOL vs ontologies vs knowledge graphs
- Peran Prolog dan logic programming di era modern AI
- Bagaimana knowledge graphs (Google, Wikidata) menggunakan prinsip FOL
- Aplikasi expert systems di bidang pertahanan dan keamanan

### ✅ Checklist Refleksi

- [ ] Saya telah menjawab minimal 3 pertanyaan refleksi secara tertulis
- [ ] Saya telah mengeksplorasi minimal 1 forum diskusi online
- [ ] Saya mencatat koneksi antara FOL dengan materi kuliah lain

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Keterbatasan Logprop dan Sintaks FOL selesai
- [ ] Section 2: Review Kuantor dan Representasi Pengetahuan selesai
- [ ] Section 3: Review Unifikasi dan MGU selesai
- [ ] Section 4: Review Forward dan Backward Chaining selesai
- [ ] Section 5: Review Resolution dalam FOL dan Aplikasi selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| Symbolic Logic (IIT Kharagpur) | NPTEL | [nptel.ac.in](https://nptel.ac.in/courses/109105111) |
| AI: Knowledge Representation and Reasoning (IIT Madras) | NPTEL/YouTube | [Class Central](https://www.classcentral.com/course/youtube-artificial-intelligence-knowledge-representation-and-reasoning-47799) |
| Fundamentals of Artificial Intelligence (IIT Guwahati) | NPTEL | [YouTube Search](https://www.youtube.com/results?search_query=NPTEL+fundamentals+artificial+intelligence+IIT+Guwahati+first+order+logic) |
| Stanford CS221: Artificial Intelligence | Stanford Online | [stanford-cs221.github.io](https://stanford-cs221.github.io/) |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *AIMA* 4th Ed. — Chapter 8-9
- Poole, D.L. & Mackworth, A.K. (2023). *AI: Foundations of Computational Agents* 3rd Ed. — Chapter 5
- Bratko, I. (2011). *Prolog Programming for Artificial Intelligence* 4th Ed. — Chapter 1-3
- Wikipedia: [First-Order Logic](https://en.wikipedia.org/wiki/First-order_logic)

### 🎥 Channel YouTube Rekomendasi

- **Gate Smashers** — Tutorial AI dan FOL dalam bahasa yang mudah dipahami
- **Neso Academy** — Penjelasan logika dan AI terstruktur
- **Knowledge Gate** — Tutorial unifikasi dan inferensi FOL
- **NPTEL Official** — Kuliah lengkap dari IIT tentang logic dan AI

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

1. Untuk "Semua drone harus melapor ke command center": dalam logika proposisional, kita perlu membuat proposisi terpisah untuk setiap drone (P₁ = "Drone1 melapor", P₂ = "Drone2 melapor", ...). Jika ada 100 drone, perlu 100 proposisi. Jika drone baru ditambahkan, KB harus diperbarui manual. Dalam FOL cukup satu kalimat: ∀x [Drone(x) ⇒ MelaporKe(x, CommandCenter)].

2. Komponen dalam ∀x [Pilot(x) ∧ Bertugas(x, SkuadronAlpha) ⇒ Terampil(x, komandan(SkuadronAlpha))]:
   - Variabel: x
   - Konstanta: SkuadronAlpha
   - Predikat: Pilot (unary), Bertugas (binary), Terampil (binary)
   - Fungsi: komandan (unary, mengembalikan objek "komandan dari")
   - Kuantor: ∀ (universal)
   - Konnektif: ∧ (konjungsi), ⇒ (implikasi)

3. "Ada seorang prajurit yang lebih berani dari semua prajurit lainnya":
   ∃x [Prajurit(x) ∧ ∀y [Prajurit(y) ∧ ¬(y = x) ⇒ LebihBerani(x, y)]]

### Section 2

1. "Semua pesawat tempur yang terdeteksi radar harus dicegat oleh interceptor":
   ∀x [PesawatTempur(x) ∧ TerdeteksiRadar(x) ⇒ ∃y [Interceptor(y) ∧ Mencegat(y, x)]]

2. Perbedaan makna:
   - ∀x ∃y Melaporkan(x, y): "Setiap prajurit melaporkan kepada *seseorang*" (bisa atasan yang berbeda-beda)
   - ∃y ∀x Melaporkan(x, y): "Ada *satu orang* yang menerima laporan dari semua prajurit" (satu atasan yang sama)
   
   Kalimat kedua lebih kuat/spesifik.

3. "Tidak ada drone musuh yang berhasil melewati zona pertahanan tanpa terdeteksi":
   ¬∃x [DronMusuh(x) ∧ Melewati(x, ZonaPertahanan) ∧ ¬Terdeteksi(x)]
   atau equivalen: ∀x [DronMusuh(x) ∧ Melewati(x, ZonaPertahanan) ⇒ Terdeteksi(x)]

4. Jawaban yang benar adalah **(b)**: ∀x [Pilot(x) ⇒ ∃y [Pesawat(y) ∧ Memiliki(x, y)]]
   - (a) salah karena menggunakan ∧ setelah ∀x, yang berarti "semua objek di dunia adalah pilot yang memiliki pesawat"
   - (b) benar karena menggunakan ⇒: "untuk semua x, JIKA x pilot MAKA ada pesawat y yang dimiliki x"

### Section 3

1. MGU:
   - (a) P(x, B) dan P(A, y) → **MGU = {x/A, y/B}** → P(A, B)
   - (b) P(x, f(x)) dan P(A, y) → θ₁ = {x/A}, terapkan: P(A, f(A)) dan P(A, y) → θ₂ = {y/f(A)} → **MGU = {x/A, y/f(A)}**
   - (c) P(x, x) dan P(A, B) → θ₁ = {x/A}, terapkan: P(A, A) dan P(A, B) → A ≠ B → **GAGAL**
   - (d) P(f(x), y) dan P(y, f(A)) → θ₁ = {y/f(x)}, terapkan ke argumen 2: f(x) dan f(A) → θ₂ = {x/A} → **MGU = {y/f(A), x/A}** → P(f(A), f(A))

2. Occur check diperlukan untuk mencegah substitusi tak terhingga. Tanpa occur check, UNIFY(x, f(x)) menghasilkan {x/f(x)}, yang berarti x = f(f(f(...))) — substitusi tak terhingga yang membuat term tidak memiliki ground instance.

3. Contoh: P(x, A) dan P(B, y)
   - Unifier 1 (MGU): {x/B, y/A} → P(B, A)
   - Unifier 2 (lebih spesifik): {x/B, y/A, z/C} — menambah substitusi z yang tidak diperlukan
   - MGU adalah yang tidak mengandung substitusi yang tidak perlu

### Section 4

1. Forward Chaining dari KB:

   **Iterasi 1:**
   - Aturan 1: Perwira(Andi) ∧ Terlatih(Andi) ✓ → Fakta baru: **BolehMemimpin(Andi)**
   
   **Iterasi 2:**
   - Aturan 2: BolehMemimpin(Andi) ∧ BerdinasAktif(Andi) ✓ → Fakta baru: **KomandanPleton(Andi)**
   
   **Iterasi 3:**
   - Tidak ada fakta baru → **SELESAI**
   
   Fakta baru: BolehMemimpin(Andi), KomandanPleton(Andi)

2. Backward Chaining proof tree:
   ```
   KomandanPleton(Andi)?
   └── Aturan 2: BolehMemimpin(Andi) ∧ BerdinasAktif(Andi)
       ├── BolehMemimpin(Andi)?
       │   └── Aturan 1: Perwira(Andi) ∧ Terlatih(Andi)
       │       ├── Perwira(Andi)? → Fakta di KB ✓
       │       └── Terlatih(Andi)? → Fakta di KB ✓
       └── BerdinasAktif(Andi)? → Fakta di KB ✓
   Hasil: TERBUKTI ✓
   ```

3. Forward chaining lebih cocok untuk C2 ketika:
   - Data masuk secara kontinu (laporan sensor, intel updates)
   - Sistem harus secara proaktif mengidentifikasi situasi yang memerlukan perhatian
   - Contoh: Sensor radar mendeteksi objek baru → aturan klasifikasi otomatis diterapkan → alert dihasilkan → aksi direkomendasikan — semua tanpa query spesifik dari operator

### Section 5

1. CNF dari ∀x [∃y Friend(x, y) ⇒ ¬Alone(x)]:
   - Eliminasi ⇒: ∀x [¬∃y Friend(x, y) ∨ ¬Alone(x)]
   - Pindahkan negasi: ∀x [∀y ¬Friend(x, y) ∨ ¬Alone(x)]
   - Sudah dalam CNF: **¬Friend(x, y) ∨ ¬Alone(x)**

2. Skolemisasi:
   - (a) ∃x Pilot(x) → Pilot(A), dimana A adalah Skolem constant
   - (b) ∀x ∃y Memimpin(x, y) → Memimpin(x, f(x)), dimana f adalah Skolem function
   - (c) ∀x ∀y ∃z DiAntara(z, x, y) → DiAntara(g(x,y), x, y), dimana g adalah Skolem function 2-argumen

3. Resolution proof untuk Terampil(Citra):
   - KB clause 1: ¬Pilot(x) ∨ Terampil(x) [dari ∀x Pilot(x) ⇒ Terampil(x)]
   - KB clause 2: Pilot(Citra)
   - Negasi goal: ¬Terampil(Citra)
   
   Resolusi langkah 1: Clause 1 + Clause 2, θ = {x/Citra}
   - ¬Pilot(Citra) ∨ Terampil(Citra) + Pilot(Citra) → **Terampil(Citra)**
   
   Resolusi langkah 2: Terampil(Citra) + ¬Terampil(Citra) → **{} (empty clause)**
   
   **TERBUKTI!** ✓

### Section 8

**Soal 1:**
- (a) ∀x [KapalPerang(x) ⇒ ∃y [Komandan(y) ∧ KomandanDari(y, x)]]
- (b) ∃x [Komandan(x) ∧ ∃y ∃z [KapalPerang(y) ∧ KapalPerang(z) ∧ ¬(y = z) ∧ Memimpin(x, y) ∧ Memimpin(x, z)]]
- (c) ∀x [KapalSelam(x) ∧ Menyelam(x, kedalaman) ∧ kedalaman > 500 ⇒ PeralatanKhusus(x)]
  Atau lebih formal: ¬∃x [KapalSelam(x) ∧ MenyelamLebihDari(x, 500) ∧ ¬MemilikiPeralatanKhusus(x)]
- (d) ∀x [Perwira(x) ∧ Terlatih(x) ⇒ BolehOperasiSenjata(x)]

**Soal 2:**
- (a) MGU = {x/Admiral, y/Armada1} → Command(Admiral, Armada1)
- (b) GAGAL — x harus sama dengan Drone1 dan Drone2 sekaligus, tapi Drone1 ≠ Drone2
- (c) MGU = {x/Budi, y/Alpha} → Assign(Budi, squad(Alpha))
- (d) MGU = {y/superior(Andi), x/Andi} → Report(Andi, superior(Andi))
- (e) MGU = {x/A, y/f(A)} → Mission(f(A), g(f(A)))

**Soal 3 (Forward Chaining):**

Iterasi 1:
- Aturan 1: Pilot(Reza) ∧ Sehat(Reza) → **FitToFly(Reza)**

Iterasi 2:
- Aturan 2: FitToFly(Reza) ∧ HasClearance(Reza) ∧ Pesawat(F16Alpha) → **CanFly(Reza, F16Alpha)**

Iterasi 3:
- Aturan 3: CanFly(Reza, F16Alpha) → **Assigned(Reza, F16Alpha)**

Iterasi 4: Tidak ada fakta baru → SELESAI

**Soal 4 (Backward Chaining):**
```
Assigned(Reza, F16Alpha)?
└── Aturan 3: CanFly(Reza, F16Alpha)?
    └── Aturan 2: FitToFly(Reza) ∧ HasClearance(Reza) ∧ Pesawat(F16Alpha)?
        ├── FitToFly(Reza)?
        │   └── Aturan 1: Pilot(Reza) ∧ Sehat(Reza)?
        │       ├── Pilot(Reza) → KB ✓
        │       └── Sehat(Reza) → KB ✓
        ├── HasClearance(Reza) → KB ✓
        └── Pesawat(F16Alpha) → KB ✓
Hasil: TERBUKTI ✓
```

**Soal 5 (Resolution):**

Konversi ke CNF:
1. ¬Soldier(x) ∨ Loyal(x) ∨ Discharged(x)
2. Soldier(Private_Ali)
3. ¬Discharged(Private_Ali)

Negasi goal: ¬Loyal(Private_Ali)

Resolusi:
- Step 1: Clause 1 + Clause 2, θ={x/Private_Ali}: Loyal(Private_Ali) ∨ Discharged(Private_Ali)
- Step 2: Hasil + Clause 3: Loyal(Private_Ali)
- Step 3: Loyal(Private_Ali) + ¬Loyal(Private_Ali): {} → **TERBUKTI** ✓

**Soal 6 (Skolemisasi dan Resolution):**

1. ∀x [∃y Friend(x, y) ⇒ ¬Alone(x)]
   - Eliminasi ⇒: ∀x [¬∃y Friend(x, y) ∨ ¬Alone(x)]
   - Move ¬: ∀x [∀y ¬Friend(x, y) ∨ ¬Alone(x)]
   - CNF: ¬Friend(x, y) ∨ ¬Alone(x) ... (C1)

2. ∀x [Soldier(x) ⇒ ∃y Friend(x, y)]
   - Eliminasi ⇒: ∀x [¬Soldier(x) ∨ ∃y Friend(x, y)]
   - Skolemisasi: ∀x [¬Soldier(x) ∨ Friend(x, f(x))]
   - CNF: ¬Soldier(x) ∨ Friend(x, f(x)) ... (C2)

3. Soldier(Budi) ... (C3)

Negasi goal: Alone(Budi) ... (C4)

Resolusi:
- C2 + C3, θ={x/Budi}: Friend(Budi, f(Budi)) ... (C5)
- C1 + C5, θ={x/Budi, y/f(Budi)}: ¬Alone(Budi) ... (C6)
- C6 + C4: {} → **TERBUKTI** ✓

**Soal 7 (Studi Kasus Militer):**

(a) Forward Chaining:

Iterasi 1:
- Aturan 1: Aircraft(ObjectAlpha) ∧ HighSpeed(ObjectAlpha) ∧ LowAltitude(ObjectAlpha) → **SuspiciousBehavior(ObjectAlpha)**
- Aturan 2: Aircraft(ObjectAlpha) ∧ ForeignTransponder(ObjectAlpha) → **PotentialThreat(ObjectAlpha)**
- Aturan 5: Aircraft(ObjectBeta) ∧ FriendlyTransponder(ObjectBeta) → **Friendly(ObjectBeta)**

Iterasi 2:
- Aturan 3: SuspiciousBehavior(ObjectAlpha) ∧ PotentialThreat(ObjectAlpha) → **HighThreat(ObjectAlpha)**

Iterasi 3:
- Aturan 4: HighThreat(ObjectAlpha) → **AlertLevel(ObjectAlpha, Red)**

Iterasi 4: Tidak ada fakta baru → SELESAI

(b) Backward Chaining:
```
AlertLevel(ObjectAlpha, Red)?
└── Aturan 4: HighThreat(ObjectAlpha)?
    └── Aturan 3: SuspiciousBehavior(ObjectAlpha) ∧ PotentialThreat(ObjectAlpha)?
        ├── SuspiciousBehavior(ObjectAlpha)?
        │   └── Aturan 1: Aircraft(OA) ∧ HighSpeed(OA) ∧ LowAltitude(OA)?
        │       ├── Aircraft(ObjectAlpha) → KB ✓
        │       ├── HighSpeed(ObjectAlpha) → KB ✓
        │       └── LowAltitude(ObjectAlpha) → KB ✓
        └── PotentialThreat(ObjectAlpha)?
            └── Aturan 2: Aircraft(OA) ∧ ForeignTransponder(OA)?
                ├── Aircraft(ObjectAlpha) → KB ✓
                └── ForeignTransponder(ObjectAlpha) → KB ✓
TERBUKTI ✓
```

(c) ObjectBeta: Diklasifikasikan sebagai **Friendly**. ObjectBeta memiliki FriendlyTransponder, sehingga Aturan 5 menghasilkan Friendly(ObjectBeta). Tidak ada aturan yang menghasilkan SuspiciousBehavior atau PotentialThreat untuk ObjectBeta karena tidak memiliki HighSpeed, LowAltitude, atau ForeignTransponder.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
