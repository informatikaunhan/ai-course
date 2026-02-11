# Latihan Pertemuan 12: Jaringan Bayesian

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 12  
**Topik:** Jaringan Bayesian  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Petunjuk Pengerjaan

1. Kerjakan semua soal secara mandiri
2. Waktu pengerjaan: 120 menit
3. Untuk soal pilihan ganda, pilih satu jawaban yang paling tepat
4. Untuk soal uraian, jawab dengan lengkap dan sistematis
5. Studi kasus memerlukan analisis mendalam dan penerapan konsep
6. Gunakan CPT Alarm Network (diberikan di lampiran) untuk soal yang memerlukannya

---

## Lampiran: Alarm Network

**Struktur:** Burglary → Alarm ← Earthquake, Alarm → JohnCalls, Alarm → MaryCalls

| | P(Burglary) |
|---|:-----------:|
| | 0.001 |

| | P(Earthquake) |
|---|:-------------:|
| | 0.002 |

| Burglary | Earthquake | P(Alarm = T) |
|:--------:|:----------:|:------------:|
| T | T | 0.95 |
| T | F | 0.94 |
| F | T | 0.29 |
| F | F | 0.001 |

| Alarm | P(JohnCalls = T) |
|:-----:|:----------------:|
| T | 0.90 |
| F | 0.05 |

| Alarm | P(MaryCalls = T) |
|:-----:|:----------------:|
| T | 0.70 |
| F | 0.01 |

---

## Bagian A: Soal Pilihan Ganda (20 Soal)

### Soal 1
Jaringan Bayesian adalah representasi grafis dari distribusi probabilitas gabungan yang berbentuk:

A. Undirected cyclic graph  
B. Directed acyclic graph (DAG)  
C. Undirected acyclic graph  
D. Directed cyclic graph  
E. Complete bipartite graph

---

### Soal 2
Dua komponen utama jaringan Bayesian adalah:

A. Adjacency matrix dan weight matrix  
B. Heuristic function dan cost function  
C. Directed acyclic graph (DAG) dan Conditional Probability Tables (CPT)  
D. State space dan transition function  
E. Knowledge base dan inference engine

---

### Soal 3
Dalam Alarm Network, berapa total parameter independen yang diperlukan?

A. 5  
B. 10  
C. 20  
D. 31  
E. 32

---

### Soal 4
Jika sebuah domain memiliki 20 variabel Boolean, full joint distribution memerlukan berapa parameter?

A. 20  
B. 400  
C. 1.023  
D. 1.048.575  
E. 2.097.152

---

### Soal 5
Pada jaringan A → B → C, jika B diobservasi, maka hubungan A dan C adalah:

A. Dependen  
B. Conditionally independent  
C. Selalu independent  
D. Selalu dependen  
E. Tidak dapat ditentukan

---

### Soal 6
Pada pola V-structure (A → B ← C), tanpa observasi apapun, hubungan A dan C adalah:

A. Dependen  
B. Conditionally independent  
C. Marginally independent  
D. Selalu dependen  
E. Bergantung pada CPT

---

### Soal 7
Fenomena "explaining away" terjadi pada pola koneksi:

A. Chain (rantai)  
B. Fork (common cause)  
C. Collider (V-structure)  
D. Semua pola  
E. Tidak ada pola

---

### Soal 8
Dalam Alarm Network, jika kita mengetahui bahwa Alarm berbunyi (A=true), maka:

A. Burglary dan Earthquake menjadi independen  
B. Burglary dan Earthquake menjadi dependen (explaining away)  
C. JohnCalls dan MaryCalls menjadi dependen  
D. Burglary menjadi independen dari JohnCalls  
E. Semua variabel menjadi independen

---

### Soal 9
D-Separation digunakan untuk menentukan:

A. Jarak terpendek antara dua node  
B. Apakah graf bersifat acyclic  
C. Conditional independence antara variabel diberikan set conditioning  
D. Jumlah parameter dalam CPT  
E. Kompleksitas inferensi

---

### Soal 10
Markov Blanket dari suatu node X terdiri dari:

A. Semua ancestor X  
B. Semua descendant X  
C. Parent, children, dan co-parent dari children X  
D. Hanya parent X  
E. Seluruh node dalam jaringan

---

### Soal 11
Dalam inferensi pada jaringan Bayesian, variabel yang nilainya diketahui disebut:

A. Query variable  
B. Hidden variable  
C. Evidence variable  
D. Latent variable  
E. Target variable

---

### Soal 12
Metode inference by enumeration menghitung posterior probability dengan cara:

A. Menghitung semua shortest path  
B. Marginalisasi variabel tersembunyi dari joint distribution  
C. Sampling random dari distribusi  
D. Gradient descent pada loss function  
E. Breadth-first search pada graph

---

### Soal 13
Keunggulan utama Variable Elimination dibandingkan Enumeration adalah:

A. Selalu memberikan hasil exact  
B. Menghindari perhitungan ulang sub-ekspresi yang sama  
C. Tidak memerlukan CPT  
D. Dapat menangani continuous variables  
E. Lebih mudah diimplementasikan

---

### Soal 14
Operasi "summing out" pada Variable Elimination bertujuan untuk:

A. Menambahkan variabel baru ke faktor  
B. Mengeliminasi variabel dengan menjumlahkan semua nilainya  
C. Menormalisasi probabilitas  
D. Menghitung entropy  
E. Mengurutkan variabel secara topologis

---

### Soal 15
Kompleksitas waktu inferensi eksak pada jaringan Bayesian umum (arbitrary) bersifat:

A. O(n)  
B. O(n log n)  
C. O(n²)  
D. Polynomial  
E. NP-hard

---

### Soal 16
Dalam metode Prior Sampling, variabel di-sample berdasarkan urutan:

A. Alfabet  
B. Topologis  
C. Reverse topologis  
D. Random  
E. Berdasarkan jumlah parent

---

### Soal 17
Diberikan jaringan A → B, dengan P(A=T)=0.4, P(B=T|A=T)=0.8, P(B=T|A=F)=0.3. Berapa P(B=T)?

A. 0.30  
B. 0.40  
C. 0.50  
D. 0.55  
E. 0.80

---

### Soal 18
Pada jaringan Bayesian, sebuah node bersifat conditionally independent dari semua node lain dalam jaringan jika diberikan:

A. Parent-nya saja  
B. Children-nya saja  
C. Markov Blanket-nya  
D. Semua ancestor-nya  
E. Seluruh node lain

---

### Soal 19
Dalam Alarm Network, Markov Blanket dari node JohnCalls adalah:

A. {Alarm}  
B. {Alarm, Burglary, Earthquake}  
C. {Alarm, MaryCalls}  
D. {Alarm, Burglary, Earthquake, MaryCalls}  
E. {Burglary, Earthquake}

---

### Soal 20
Ketika membangun jaringan Bayesian, arah panah sebaiknya mengikuti:

A. Urutan alfabet variabel  
B. Arah kausal (cause → effect)  
C. Arah temporal terbalik  
D. Random  
E. Dari variabel dengan domain terbesar ke terkecil

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan apa yang dimaksud dengan "curse of dimensionality" dalam konteks full joint distribution! Mengapa jaringan Bayesian menjadi solusi?

---

### Soal 2 ⭐
Sebutkan dan jelaskan dua komponen utama jaringan Bayesian (DAG dan CPT)! Apa peran masing-masing?

---

### Soal 3 ⭐
Jelaskan perbedaan antara tiga jenis query inferensi pada jaringan Bayesian: posterior probability, most probable explanation, dan joint probability!

---

### Soal 4 ⭐
Sebuah jaringan Bayesian memiliki 6 node Boolean dimana setiap node memiliki paling banyak 2 parent. Berapa jumlah parameter maksimal untuk jaringan ini? Bandingkan dengan full joint distribution!

---

### Soal 5 ⭐⭐
Jelaskan tiga pola koneksi fundamental dalam jaringan Bayesian (chain, common cause, v-structure)! Untuk setiap pola, jelaskan kapan informasi dapat mengalir dan kapan terblokir!

---

### Soal 6 ⭐⭐
Jelaskan fenomena "explaining away" dengan contoh dari domain pertahanan! Mengapa fenomena ini penting dalam penalaran probabilistik?

---

### Soal 7 ⭐⭐
Diberikan jaringan Bayesian:
- A → C
- B → C
- C → D
- C → E

Tentukan apakah pasangan variabel berikut d-separated dan jelaskan alasannya:  
(a) A dan B diberikan {} (kosong)  
(b) A dan B diberikan {C}  
(c) D dan E diberikan {C}  
(d) A dan D diberikan {}

---

### Soal 8 ⭐⭐
Tentukan Markov Blanket untuk setiap node dalam Alarm Network! Jelaskan langkah penentuan untuk node Alarm!

---

### Soal 9 ⭐⭐
Diberikan jaringan sederhana A → B → C dengan:
- P(A=T) = 0.4
- P(B=T|A=T) = 0.7, P(B=T|A=F) = 0.2
- P(C=T|B=T) = 0.8, P(C=T|B=F) = 0.3

Gunakan Variable Elimination untuk menghitung P(A | C=T)!

---

### Soal 10 ⭐⭐
Jelaskan langkah-langkah membangun jaringan Bayesian dari domain! Berikan contoh untuk domain sistem deteksi kebakaran di kapal perang!

---

### Soal 11 ⭐⭐
Gunakan metode prior sampling pada jaringan Hujan (H) → Banjir (B) → Evakuasi (E) dengan:
- P(H=T) = 0.2
- P(B=T|H=T) = 0.9, P(B=T|H=F) = 0.1
- P(E=T|B=T) = 0.8, P(E=T|B=F) = 0.05

Hasilkan 5 sampel menggunakan angka random: (0.3, 0.5, 0.7), (0.1, 0.2, 0.3), (0.6, 0.8, 0.1), (0.9, 0.05, 0.9), (0.15, 0.4, 0.6)

---

### Soal 12 ⭐⭐⭐
Menggunakan Alarm Network, hitung P(Alarm = true | Burglary = true) dengan marginalisasi atas Earthquake! Tunjukkan semua langkah perhitungan!

---

### Soal 13 ⭐⭐⭐
Sebuah jaringan Bayesian untuk sistem sensor militer:
- Target (T): P(T=T) = 0.1
- SensorA (A): P(A=T|T=T) = 0.85, P(A=T|T=F) = 0.1
- SensorB (B): P(B=T|T=T) = 0.90, P(B=T|T=F) = 0.05
- Alert (L): P(L=T|A=T,B=T) = 0.99, P(L=T|A=T,B=F) = 0.70, P(L=T|A=F,B=T) = 0.65, P(L=T|A=F,B=F) = 0.02

Struktur: T → A, T → B, A → L ← B

Hitung P(Target = true | Alert = true) menggunakan Variable Elimination!

---

### Soal 14 ⭐⭐⭐
Diberikan jaringan Bayesian kompleks:
- I → A, C → A, A → D, A → P, D → S, P → S

dimana I = IntelMusuh, C = Cuaca, A = AncamanUdara, D = DeteksiRadar, P = PerintahKomandan, S = ScrambleJet.

Tentukan d-separation untuk:  
(a) I dan C | {A}  
(b) D dan P | {A}  
(c) I dan S | {A, D}  
(d) I dan S | {}  
(e) D dan P | {S}

---

### Soal 15 ⭐⭐⭐
Bandingkan metode inferensi: Enumeration, Variable Elimination, dan Approximate Inference (Prior Sampling)! Untuk setiap metode, jelaskan: prinsip kerja, kompleksitas, kelebihan, dan kekurangan. Kapan masing-masing metode sebaiknya digunakan?

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Deteksi Intrusi Jaringan Siber Militer

**Latar Belakang:**

Pusat Pertahanan Siber TNI mengembangkan Intelligent Intrusion Detection System (IIDS) berbasis jaringan Bayesian untuk melindungi jaringan Command, Control, Communications, Computers, Cyber, Combat Systems, Intelligence, Surveillance, and Reconnaissance (C6ISR).

Sistem harus menganalisis berbagai indikator untuk menentukan apakah aktivitas jaringan merupakan serangan siber yang sesungguhnya atau false alarm. Variabel-variabel yang relevan:

1. **SeranganSiber (S):** Apakah sedang terjadi serangan siber — P(S=T) = 0.03
2. **AnomaliBandwidth (B):** Anomali pada pola traffic bandwidth — P(B=T|S=T) = 0.90, P(B=T|S=F) = 0.08
3. **PortScanDeteksi (P):** Terdeteksi port scanning — P(P=T|S=T) = 0.85, P(P=T|S=F) = 0.04
4. **SignatureMatch (M):** Signature cocok dengan known attack — P(M=T|S=T) = 0.80, P(M=T|S=F) = 0.02
5. **AlertSystem (A):** Sistem mengeluarkan alert — bergantung pada B, P, M
6. **ResponseTeam (R):** Tim respons dikerahkan — bergantung pada A

**CPT AlertSystem:**

| B | P | M | P(A=T) |
|:-:|:-:|:-:|:------:|
| T | T | T | 0.99 |
| T | T | F | 0.90 |
| T | F | T | 0.85 |
| T | F | F | 0.40 |
| F | T | T | 0.80 |
| F | T | F | 0.35 |
| F | F | T | 0.70 |
| F | F | F | 0.01 |

**CPT ResponseTeam:** P(R=T|A=T) = 0.90, P(R=T|A=F) = 0.02

**Pertanyaan:**

**1a.** Gambarkan topologi jaringan Bayesian untuk sistem ini! Hitung total parameter independen dan bandingkan dengan full joint distribution! (10 poin)

**1b.** Analisis karakteristik tiga pola koneksi yang terdapat dalam jaringan ini! Identifikasi minimal satu contoh chain, common cause, dan v-structure! (15 poin)

**1c.** Tentukan Markov Blanket untuk node AlertSystem dan node SeranganSiber! (10 poin)

**1d.** Tentukan d-separation untuk pasangan berikut:  
(i) AnomaliBandwidth dan PortScanDeteksi | {}  
(ii) AnomaliBandwidth dan PortScanDeteksi | {SeranganSiber}  
(iii) AnomaliBandwidth dan SignatureMatch | {AlertSystem}  
(iv) SeranganSiber dan ResponseTeam | {AlertSystem}  
(15 poin)

**1e.** Hitung P(SeranganSiber = true | AnomaliBandwidth = true, PortScanDeteksi = true) menggunakan Variable Elimination! Eliminasi variabel M, A, dan R. (15 poin)

---

### Studi Kasus 2: Sistem Penilaian Ancaman Maritim

**Latar Belakang:**

TNI Angkatan Laut mengembangkan Maritime Threat Assessment System (MTAS) berbasis jaringan Bayesian untuk membantu pengambilan keputusan di pos komando armada. Sistem ini mengintegrasikan data dari berbagai sensor untuk menilai apakah kontak maritim yang terdeteksi merupakan ancaman.

**Variabel dan CPT:**

1. **KapalAsingHostil (K):** Keberadaan kapal asing dengan niat hostil — P(K=T) = 0.05
2. **KondisiLaut (L):** Kondisi laut buruk yang mempengaruhi sensor — P(L=Buruk) = 0.30
3. **DeteksiRadar (R):** Radar mendeteksi kontak (dipengaruhi K dan L)

| K | L | P(R=T) |
|:-:|:-:|:------:|
| T | Baik | 0.95 |
| T | Buruk | 0.65 |
| F | Baik | 0.08 |
| F | Buruk | 0.20 |

4. **DeteksiSonar (S):** Sonar mendeteksi kontak (dipengaruhi K dan L)

| K | L | P(S=T) |
|:-:|:-:|:------:|
| T | Baik | 0.90 |
| T | Buruk | 0.55 |
| F | Baik | 0.05 |
| F | Buruk | 0.15 |

5. **TingkatAncaman (T):** Penilaian tingkat ancaman tinggi (dipengaruhi R dan S)

| R | S | P(T=T) |
|:-:|:-:|:------:|
| T | T | 0.95 |
| T | F | 0.55 |
| F | T | 0.50 |
| F | F | 0.02 |

6. **KerahkanKapalPerang (P):** Keputusan mengerahkan kapal perang (dipengaruhi T)

P(P=T|T=T) = 0.85, P(P=T|T=F) = 0.05

**Struktur:** K → R ← L, K → S ← L, R → T ← S, T → P

**Pertanyaan:**

**2a.** Gambarkan topologi lengkap jaringan Bayesian ini! Hitung total parameter dan bandingkan dengan full joint distribution! (10 poin)

**2b.** Hitung P(DeteksiRadar = true) dengan marginalisasi! (10 poin)

**2c.** Menggunakan d-separation, tentukan dan jelaskan:  
(i) DeteksiRadar dan DeteksiSonar | {} (kosong)  
(ii) DeteksiRadar dan DeteksiSonar | {KapalAsingHostil, KondisiLaut}  
(iii) DeteksiRadar dan DeteksiSonar | {TingkatAncaman}  
(iv) KapalAsingHostil dan KondisiLaut | {DeteksiRadar}  
(15 poin)

**2d.** Hitung P(KapalAsingHostil = true | DeteksiRadar = true, DeteksiSonar = true) menggunakan Variable Elimination! Eliminasi L, T, dan P. Tunjukkan semua langkah perhitungan faktor! (20 poin)

**2e.** Jelaskan bagaimana fenomena explaining away muncul dalam jaringan ini! Berikan contoh skenario operasional spesifik! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **B** | Jaringan Bayesian menggunakan Directed Acyclic Graph (DAG) — graf berarah tanpa siklus |
| 2 | **C** | Dua komponen utama: DAG (topologi hubungan antar variabel) dan CPT (tabel probabilitas bersyarat) |
| 3 | **B** | Burglary: 1, Earthquake: 1, Alarm: 4 (2² parents), JohnCalls: 2, MaryCalls: 2 = total 10 parameter |
| 4 | **D** | Full joint distribution 20 variabel Boolean: 2²⁰ - 1 = 1.048.575 parameter |
| 5 | **B** | Chain pattern: jika B diobservasi, path terblokir sehingga A dan C conditionally independent |
| 6 | **C** | V-structure: tanpa observasi pada collider B, A dan C marginally independent |
| 7 | **C** | Explaining away terjadi pada V-structure/collider ketika common effect diobservasi |
| 8 | **B** | Alarm adalah collider (B→A←E); mengobservasi A mengaktifkan dependensi antara B dan E (explaining away) |
| 9 | **C** | D-Separation menentukan conditional independence berdasarkan struktur graf |
| 10 | **C** | Markov Blanket = {parents, children, co-parents of children} |
| 11 | **C** | Evidence variable adalah variabel yang nilainya diketahui/diobservasi |
| 12 | **B** | Enumeration menghitung P(X|e) = α Σᵧ P(X, e, y) — marginalisasi hidden variables |
| 13 | **B** | Variable Elimination menyimpan hasil antara (faktor) untuk menghindari perhitungan ulang |
| 14 | **B** | Summing out mengeliminasi variabel dari faktor dengan menjumlahkan semua nilainya |
| 15 | **E** | Inferensi eksak pada jaringan Bayesian umum terbukti NP-hard |
| 16 | **B** | Prior sampling men-sample variabel dalam urutan topologis agar parent sudah memiliki nilai |
| 17 | **C** | P(B=T) = P(B=T|A=T)P(A=T) + P(B=T|A=F)P(A=F) = 0.8×0.4 + 0.3×0.6 = 0.32 + 0.18 = 0.50 |
| 18 | **C** | Markov Blanket membuat node conditionally independent dari semua node lain |
| 19 | **C** | MB(JohnCalls) = parents:{Alarm} ∪ children:{} ∪ co-parents of children:{} = {Alarm}; tapi MaryCalls adalah co-parent (keduanya child dari Alarm) → MB = {Alarm, MaryCalls} |
| 20 | **B** | Arah panah mengikuti hubungan kausal menghasilkan jaringan yang lebih compact dan intuitif |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Curse of Dimensionality:**
Full joint distribution memerlukan $2^n - 1$ parameter untuk n variabel Boolean. Pertumbuhan eksponensial ini membuat representasi, penyimpanan, dan inferensi menjadi tidak praktis untuk domain dengan banyak variabel.

| Variabel | Parameter Full Joint |
|:--------:|:-------------------:|
| 10 | 1.023 |
| 20 | ~1 juta |
| 30 | ~1 miliar |

**Mengapa jaringan Bayesian menjadi solusi:**
Jaringan Bayesian mengeksploitasi conditional independence antar variabel. Dalam banyak domain nyata, setiap variabel hanya bergantung langsung pada sejumlah kecil variabel lain. Dengan hanya menyimpan CPT untuk parent langsung, jumlah parameter berkurang drastis — dari eksponensial menjadi linear terhadap jumlah node (dengan asumsi jumlah parent terbatas).

---

#### Jawaban Soal 2 ⭐

**1. Directed Acyclic Graph (DAG):**
- Merepresentasikan struktur hubungan antar variabel
- Node = variabel random, edge = hubungan ketergantungan langsung
- Arah panah umumnya mengikuti arah kausal (cause → effect)
- Acyclic berarti tidak ada siklus — tidak mungkin kembali ke node yang sama dengan mengikuti arah panah
- Meng-encode asumsi conditional independence

**2. Conditional Probability Tables (CPT):**
- Tabel numerik yang menyimpan distribusi probabilitas bersyarat
- Setiap node memiliki CPT: P(Node | Parents)
- Root node (tanpa parent): CPT berisi probabilitas prior
- Node dengan k parent Boolean: CPT memiliki $2^k$ baris
- CPT menyediakan informasi kuantitatif untuk inferensi

---

#### Jawaban Soal 3 ⭐

| Jenis Query | Notasi | Deskripsi | Contoh |
|:-----------:|:------:|-----------|--------|
| **Posterior probability** | P(X \| e) | Distribusi probabilitas X diberikan evidence | P(Burglary \| JohnCalls=T) |
| **Most probable explanation** | argmax_x P(x \| e) | Nilai X yang paling mungkin | Apakah pencurian lebih mungkin terjadi atau tidak? |
| **Joint probability** | P(X, Y \| e) | Distribusi gabungan X dan Y diberikan evidence | P(Burglary, Earthquake \| JohnCalls=T) |

Posterior probability adalah query paling umum, digunakan untuk memperbarui keyakinan berdasarkan bukti baru. Most probable explanation berguna untuk diagnosis. Joint probability digunakan ketika hubungan antar beberapa variabel perlu dianalisis secara simultan.

---

#### Jawaban Soal 4 ⭐

**Parameter per node:**
- Node tanpa parent: 1 parameter
- Node dengan 1 parent Boolean: 2 parameter
- Node dengan 2 parent Boolean: 4 parameter (maksimal)

**Kasus terburuk** (setiap node memiliki 2 parent, kecuali 2 root):
- 2 root nodes: 2 × 1 = 2 parameter
- 4 node lainnya masing-masing 4 parameter: 4 × 4 = 16 parameter
- **Total maksimal: 18 parameter**

Catatan: Tidak semua konfigurasi mungkin menghasilkan DAG valid dengan tepat 2 parent per non-root. Konfigurasi realistis bisa bervariasi. Estimasi atas: 2 + 4×4 = 18.

**Full joint distribution:**
$$2^6 - 1 = 63 \text{ parameter}$$

**Perbandingan:** 18 vs 63 — pengurangan ~71%.

---

#### Jawaban Soal 5 ⭐⭐

**1. Chain (Rantai): A → B → C**

| Kondisi | A dan C | Alasan |
|---------|:-------:|--------|
| B tidak diobservasi | Dependen | Informasi mengalir dari A melalui B ke C |
| B diobservasi | Independen | B memblokir aliran informasi; mengetahui B membuat A tidak menambah info tentang C |

Contoh: PesawatMusuh → DeteksiRadar → Sirene

**2. Common Cause (Fork): A ← B → C**

| Kondisi | A dan C | Alasan |
|---------|:-------:|--------|
| B tidak diobservasi | Dependen | A dan C berkorelasi melalui penyebab bersama B |
| B diobservasi | Independen | Mengetahui penyebab B memutus korelasi antara A dan C |

Contoh: Macet ← Hujan → Banjir

**3. V-structure (Collider): A → B ← C**

| Kondisi | A dan C | Alasan |
|---------|:-------:|--------|
| B tidak diobservasi | Independen | Dua penyebab independen jika efek tidak diketahui |
| B diobservasi | Dependen | Explaining away — mengetahui efek menciptakan dependensi antar penyebab |

Contoh: Pencurian → Alarm ← Gempa

---

#### Jawaban Soal 6 ⭐⭐

**Explaining Away** adalah fenomena di mana mengetahui satu penyebab dari suatu efek yang diamati mengurangi probabilitas penyebab lain.

**Contoh Pertahanan:**

Jaringan: JammingMusuh → RadarGagal ← KerusakanHardware

- Tanpa informasi tentang RadarGagal: JammingMusuh dan KerusakanHardware independen — kemungkinan jamming tidak bergantung pada kondisi hardware.
- Jika RadarGagal = true: ada dua kemungkinan penyebab. Keduanya menjadi dependen.
- Jika kemudian ditemukan KerusakanHardware = true: kegagalan radar sudah "terjelaskan" oleh kerusakan hardware, sehingga P(JammingMusuh | RadarGagal, KerusakanHardware) < P(JammingMusuh | RadarGagal).

**Pentingnya dalam penalaran probabilistik:**
Explaining away memungkinkan sistem melakukan diagnosis yang lebih akurat. Dalam contoh di atas, teknisi tidak perlu panik tentang ancaman jamming musuh jika ternyata hardware radar memang rusak. Ini mencegah false alarm dan respons yang tidak proporsional.

---

#### Jawaban Soal 7 ⭐⭐

**Jaringan:** A → C ← B, C → D, C → E

**(a) A dan B | {} (kosong)**
- Path: A → C ← B
- C adalah collider, C ∉ {} dan tidak ada descendant C di {}
- Path **terblokir**
- **A ⊥ B | {}** ✅ (d-separated)

**(b) A dan B | {C}**
- Path: A → C ← B
- C adalah collider, C ∈ {C} → path menjadi **aktif**
- **A ⊥̸ B | {C}** ❌ (tidak d-separated — explaining away)

**(c) D dan E | {C}**
- Path: D ← C → E
- C adalah common cause (fork), C ∈ {C} → path **terblokir**
- **D ⊥ E | {C}** ✅ (d-separated)

**(d) A dan D | {} (kosong)**
- Path: A → C → D
- C adalah chain node, C ∉ {} → path **aktif**
- **A ⊥̸ D | {}** ❌ (tidak d-separated)

---

#### Jawaban Soal 8 ⭐⭐

**Markov Blanket = Parents ∪ Children ∪ Co-parents of Children**

**MB(Burglary):**
- Parents: {} (root)
- Children: {Alarm}
- Co-parents of Alarm: {Earthquake}
- **MB(Burglary) = {Alarm, Earthquake}**

**MB(Earthquake):**
- Parents: {} (root)
- Children: {Alarm}
- Co-parents of Alarm: {Burglary}
- **MB(Earthquake) = {Alarm, Burglary}**

**MB(Alarm) — langkah detail:**
- Step 1 — Parents: {Burglary, Earthquake}
- Step 2 — Children: {JohnCalls, MaryCalls}
- Step 3 — Co-parents of JohnCalls: parent JohnCalls = {Alarm} saja → tidak ada co-parent
- Step 3 — Co-parents of MaryCalls: parent MaryCalls = {Alarm} saja → tidak ada co-parent
- **MB(Alarm) = {Burglary, Earthquake, JohnCalls, MaryCalls}**

**MB(JohnCalls):**
- Parents: {Alarm}
- Children: {} (leaf)
- Co-parents: tidak ada children, jadi tidak ada co-parent → tetapi MaryCalls juga child dari Alarm, sehingga MaryCalls adalah "sibling" yang berbagi parent Alarm
- Koreksi: Co-parents of children = {} (JohnCalls tidak punya children), tapi JohnCalls juga co-parent of MaryCalls: MaryCalls's parent = {Alarm}; JohnCalls bukan parent MaryCalls
- **MB(JohnCalls) = {Alarm, MaryCalls}**

Penjelasan: MaryCalls masuk MB karena keduanya children dari Alarm. Mengetahui Alarm dan MaryCalls membuat JohnCalls independen dari Burglary dan Earthquake.

**MB(MaryCalls):**
- Parents: {Alarm}
- Children: {} (leaf)
- **MB(MaryCalls) = {Alarm, JohnCalls}**

Koreksi penting: Untuk leaf node, MB = parents ∪ co-children (node lain yang berbagi parent yang sama). JohnCalls dan MaryCalls masuk ke MB masing-masing karena keduanya children dari Alarm — perubahan satu memberikan informasi tentang Alarm yang relevan untuk yang lain.

---

#### Jawaban Soal 9 ⭐⭐

**Jaringan:** A → B → C, Query: P(A | C=T), Hidden: B

**Step 1:** Faktor awal
- $f_1(A) = P(A)$
- $f_2(A, B) = P(B|A)$
- $f_3(B, C) = P(C|B)$

**Step 2:** Masukkan evidence C=T

$f_3'(B) = P(C=T|B)$:

| B | $f_3'(B)$ |
|:-:|:---------:|
| T | 0.8 |
| F | 0.3 |

**Step 3:** Eliminasi B — kalikan $f_2 × f_3'$, lalu jumlahkan atas B

$f_4(A, B) = f_2(A, B) × f_3'(B)$:

| A | B | $f_2(A,B)$ | $f_3'(B)$ | $f_4(A,B)$ |
|:-:|:-:|:----------:|:---------:|:-----------:|
| T | T | 0.7 | 0.8 | 0.56 |
| T | F | 0.3 | 0.3 | 0.09 |
| F | T | 0.2 | 0.8 | 0.16 |
| F | F | 0.8 | 0.3 | 0.24 |

$f_5(A) = \sum_B f_4(A, B)$:

| A | $f_5(A)$ |
|:-:|:--------:|
| T | 0.56 + 0.09 = 0.65 |
| F | 0.16 + 0.24 = 0.40 |

**Step 4:** Kalikan dengan prior dan normalisasi

$f_6(A) = f_1(A) × f_5(A)$:

| A | $f_1(A)$ | $f_5(A)$ | $f_6(A)$ |
|:-:|:--------:|:--------:|:--------:|
| T | 0.4 | 0.65 | 0.260 |
| F | 0.6 | 0.40 | 0.240 |

Normalisasi: α = 1/(0.260 + 0.240) = 1/0.500 = 2

$$P(A=T | C=T) = 0.260/0.500 = 0.520$$
$$P(A=F | C=T) = 0.240/0.500 = 0.480$$

**Jawaban:** P(A=T | C=T) = 0.520. Mengetahui C=true meningkatkan probabilitas A=true dari 0.4 (prior) menjadi 0.52 (posterior).

---

#### Jawaban Soal 10 ⭐⭐

**Langkah-langkah membangun jaringan Bayesian:**

1. **Identifikasi variabel relevan**: Tentukan semua variabel yang perlu dimodelkan
2. **Tentukan hubungan kausal**: Analisis variabel mana yang secara langsung mempengaruhi variabel lain
3. **Buat topologi (DAG)**: Gambar graf berarah mengikuti arah kausal
4. **Tentukan CPT**: Dari data historis, ahli domain, atau literatur
5. **Validasi**: Periksa apakah conditional independence yang tersirat masuk akal

**Contoh: Sistem Deteksi Kebakaran di Kapal Perang**

Step 1 — Variabel:
- K: Kebakaran (ada/tidak)
- S: SensorAsap (aktif/tidak)
- T: SensorSuhu (aktif/tidak)
- A: AlarmKebakaran (berbunyi/tidak)
- P: SistemPemadamOtomatis (aktif/tidak)

Step 2 — Hubungan kausal:
- Kebakaran menyebabkan asap dan kenaikan suhu
- Sensor asap dan suhu memicu alarm
- Alarm memicu sistem pemadam

Step 3 — Topologi:
K → S, K → T, S → A ← T, A → P

Step 4 — CPT contoh:
- P(K=T) = 0.01
- P(S=T|K=T) = 0.95, P(S=T|K=F) = 0.05 (false alarm)
- P(T=T|K=T) = 0.90, P(T=T|K=F) = 0.03
- Dan seterusnya untuk A dan P

Step 5 — Validasi: S ⊥ T | K ✅ (jika kita tahu ada kebakaran atau tidak, sensor asap dan suhu independen — masuk akal karena keduanya dipengaruhi oleh penyebab yang sama).

---

#### Jawaban Soal 11 ⭐⭐

**Jaringan:** H → B → E, dengan aturan: r < P(variabel) → True

**Sampel 1:** (0.3, 0.5, 0.7)
- H: 0.3 > 0.2 → H=F
- B: P(B=T|H=F)=0.1, 0.5 > 0.1 → B=F
- E: P(E=T|B=F)=0.05, 0.7 > 0.05 → E=F
- Hasil: **(F, F, F)**

**Sampel 2:** (0.1, 0.2, 0.3)
- H: 0.1 < 0.2 → H=T
- B: P(B=T|H=T)=0.9, 0.2 < 0.9 → B=T
- E: P(E=T|B=T)=0.8, 0.3 < 0.8 → E=T
- Hasil: **(T, T, T)**

**Sampel 3:** (0.6, 0.8, 0.1)
- H: 0.6 > 0.2 → H=F
- B: P(B=T|H=F)=0.1, 0.8 > 0.1 → B=F
- E: P(E=T|B=F)=0.05, 0.1 > 0.05 → E=F
- Hasil: **(F, F, F)**

**Sampel 4:** (0.9, 0.05, 0.9)
- H: 0.9 > 0.2 → H=F
- B: P(B=T|H=F)=0.1, 0.05 < 0.1 → B=T
- E: P(E=T|B=T)=0.8, 0.9 > 0.8 → E=F
- Hasil: **(F, T, F)**

**Sampel 5:** (0.15, 0.4, 0.6)
- H: 0.15 < 0.2 → H=T
- B: P(B=T|H=T)=0.9, 0.4 < 0.9 → B=T
- E: P(E=T|B=T)=0.8, 0.6 < 0.8 → E=T
- Hasil: **(T, T, T)**

**Ringkasan:**

| # | H | B | E |
|:-:|:-:|:-:|:-:|
| 1 | F | F | F |
| 2 | T | T | T |
| 3 | F | F | F |
| 4 | F | T | F |
| 5 | T | T | T |

**Estimasi:** P̂(H=T) = 2/5 = 0.40 (aktual: 0.20), P̂(E=T) = 2/5 = 0.40. Estimasi belum akurat karena hanya 5 sampel — akan konvergen dengan lebih banyak sampel.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Query:** P(Alarm=T | Burglary=T)

$$P(A=T | B=T) = \sum_{e} P(A=T | B=T, e) \cdot P(e)$$

**Step 1:** Enumerasi atas Earthquake

| Earthquake | P(e) | P(A=T \| B=T, e) | Produk |
|:----------:|:----:|:----------------:|:------:|
| T | 0.002 | 0.95 | 0.002 × 0.95 = 0.00190 |
| F | 0.998 | 0.94 | 0.998 × 0.94 = 0.93812 |

**Step 2:** Jumlahkan

$$P(A=T | B=T) = 0.00190 + 0.93812 = 0.94002$$

**Jawaban:** P(Alarm=T | Burglary=T) ≈ 0.940. Jika terjadi pencurian, probabilitas alarm berbunyi sangat tinggi (94%), yang masuk akal karena P(A|B=T, E=T)=0.95 dan P(A|B=T, E=F)=0.94 keduanya tinggi.

---

#### Jawaban Soal 13 ⭐⭐⭐

**Jaringan:** T → A, T → B, A → L ← B. Query: P(T=T | L=T). Hidden: A, B.

**Step 1:** Faktor awal
- $f_1(T) = P(T)$
- $f_2(T, A) = P(A|T)$
- $f_3(T, B) = P(B|T)$
- $f_4(A, B, L) = P(L|A, B)$

**Step 2:** Masukkan evidence L=T

$f_4'(A, B) = P(L=T|A, B)$:

| A | B | $f_4'$ |
|:-:|:-:|:------:|
| T | T | 0.99 |
| T | F | 0.70 |
| F | T | 0.65 |
| F | F | 0.02 |

**Step 3:** Eliminasi A — kalikan $f_2 × f_4'$, jumlahkan atas A

$f_5(T, A, B) = f_2(T,A) × f_4'(A,B)$, lalu $f_6(T, B) = \sum_A f_5$

Untuk T=T:

| A | B | $f_2(T,A)$ | $f_4'(A,B)$ | Produk |
|:-:|:-:|:----------:|:-----------:|:------:|
| T | T | 0.85 | 0.99 | 0.8415 |
| T | F | 0.85 | 0.70 | 0.5950 |
| F | T | 0.15 | 0.65 | 0.0975 |
| F | F | 0.15 | 0.02 | 0.0030 |

$f_6(T=T, B=T) = 0.8415 + 0.0975 = 0.9390$
$f_6(T=T, B=F) = 0.5950 + 0.0030 = 0.5980$

Untuk T=F:

| A | B | $f_2(F,A)$ | $f_4'(A,B)$ | Produk |
|:-:|:-:|:----------:|:-----------:|:------:|
| T | T | 0.10 | 0.99 | 0.0990 |
| T | F | 0.10 | 0.70 | 0.0700 |
| F | T | 0.90 | 0.65 | 0.5850 |
| F | F | 0.90 | 0.02 | 0.0180 |

$f_6(T=F, B=T) = 0.0990 + 0.5850 = 0.6840$
$f_6(T=F, B=F) = 0.0700 + 0.0180 = 0.0880$

**Step 4:** Eliminasi B — kalikan $f_3 × f_6$, jumlahkan atas B

Untuk T=T:
$$f_7(T=T) = P(B=T|T=T) × f_6(T=T,T) + P(B=F|T=T) × f_6(T=T,F)$$
$$= 0.90 × 0.9390 + 0.10 × 0.5980 = 0.8451 + 0.0598 = 0.9049$$

Untuk T=F:
$$f_7(T=F) = P(B=T|T=F) × f_6(T=F,T) + P(B=F|T=F) × f_6(T=F,F)$$
$$= 0.05 × 0.6840 + 0.95 × 0.0880 = 0.0342 + 0.0836 = 0.1178$$

**Step 5:** Kalikan dengan prior dan normalisasi

| T | $f_1(T)$ | $f_7(T)$ | $f_8(T)$ |
|:-:|:--------:|:--------:|:--------:|
| T | 0.1 | 0.9049 | 0.09049 |
| F | 0.9 | 0.1178 | 0.10602 |

$$P(T=T | L=T) = \frac{0.09049}{0.09049 + 0.10602} = \frac{0.09049}{0.19651} ≈ 0.461$$

**Jawaban:** P(Target=T | Alert=T) ≈ 0.461 (46.1%). Alert meningkatkan probabilitas target dari 10% (prior) menjadi ~46%. Tidak mencapai mayoritas karena sensor memiliki false positive rate yang signifikan.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Jaringan:** I → A ← C, A → D, A → P, D → S ← P

**(a) I dan C | {A}**
- Path: I → A ← C
- A adalah collider, A ∈ {A} → path **aktif**
- **I ⊥̸ C | {A}** ❌ (explaining away: jika ancaman tinggi dan cuaca baik, intelijen musuh lebih mungkin benar)

**(b) D dan P | {A}**
- Path: D ← A → P
- A adalah common cause, A ∈ {A} → path **terblokir**
- **D ⊥ P | {A}** ✅ (jika level ancaman diketahui, deteksi radar dan perintah komandan independen)

**(c) I dan S | {A, D}**
- Path 1: I → A → D → S — A ∈ {A}, chain di A → **terblokir** ✅
- Path 2: I → A → P → S — A ∈ {A}, chain di A → **terblokir** ✅
- Semua path terblokir
- **I ⊥ S | {A, D}** ✅

**(d) I dan S | {} (kosong)**
- Path 1: I → A → D → S — tidak ada node diobservasi, chain di A → **aktif**
- **I ⊥̸ S | {}** ❌ (informasi mengalir bebas dari I ke S)

**(e) D dan P | {S}**
- Path 1: D ← A → P — A tidak diobservasi, common cause → **aktif**
- Path 2: D → S ← P — S adalah collider, S ∈ {S} → **aktif**
- Ada path aktif
- **D ⊥̸ P | {S}** ❌ (dua jalur aktif: melalui common cause A, dan explaining away di S)

---

#### Jawaban Soal 15 ⭐⭐⭐

| Aspek | Enumeration | Variable Elimination | Approximate (Sampling) |
|-------|------------|---------------------|----------------------|
| **Prinsip** | Menjumlahkan semua kombinasi hidden variables dari joint distribution | Eliminasi variabel satu per satu, menyimpan faktor antara | Menghasilkan sampel dari distribusi dan mengestimasi probabilitas |
| **Kompleksitas** | O(d^n) — eksponensial terhadap jumlah variabel | O(d^w) — eksponensial terhadap treewidth w | O(N) per query — linear terhadap jumlah sampel |
| **Hasil** | Eksak | Eksak | Aproksimasi (konvergen ke eksak) |
| **Kelebihan** | Sederhana, mudah dipahami, selalu benar | Jauh lebih efisien dari enumeration, menghindari redundansi | Scalable untuk jaringan besar, tidak tergantung treewidth |
| **Kekurangan** | Sangat lambat untuk jaringan besar, banyak perhitungan redundan | Tetap eksponensial pada worst case (treewidth besar) | Tidak eksak, konvergensi lambat untuk event langka |

**Kapan menggunakan:**
- **Enumeration:** Jaringan sangat kecil (< 10 variabel), untuk tujuan edukasi/verifikasi
- **Variable Elimination:** Jaringan menengah dengan treewidth rendah, ketika hasil eksak diperlukan
- **Approximate Inference:** Jaringan besar atau treewidth tinggi, ketika aproksimasi dapat diterima

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Deteksi Intrusi Jaringan Siber Militer

**1a. Topologi dan Parameter (10 poin)**

**Topologi:**
- S → B, S → P, S → M, B → A ← P, M → A, A → R

**Total parameter:**
- SeranganSiber (S): 1 parameter (root)
- AnomaliBandwidth (B): 2 parameter (1 parent: S)
- PortScanDeteksi (P): 2 parameter (1 parent: S)
- SignatureMatch (M): 2 parameter (1 parent: S)
- AlertSystem (A): 8 parameter (3 parents: B, P, M → 2³ = 8)
- ResponseTeam (R): 2 parameter (1 parent: A)

**Total: 1 + 2 + 2 + 2 + 8 + 2 = 17 parameter**

**Full joint distribution:** 6 variabel Boolean → 2⁶ - 1 = 63 parameter

**Perbandingan:** 17 vs 63 — pengurangan ~73%.

**1b. Pola Koneksi (15 poin)**

**Chain:** S → B → A → R
- Jika B diobservasi, S dan A menjadi conditionally independent melalui path ini
- Contoh operasional: Jika kita tahu ada anomali bandwidth, mengetahui ada serangan tidak mengubah probabilitas alert (melalui jalur ini)

**Common Cause:** B ← S → P
- SeranganSiber sebagai penyebab bersama
- Jika S diobservasi, B dan P independen
- Contoh: Jika sudah dikonfirmasi ada serangan, anomali bandwidth dan port scan independen (keduanya sudah dijelaskan oleh serangan)

**V-structure:** B → A ← P (dan M → A)
- AlertSystem sebagai common effect dari B, P, M
- Jika A diobservasi, B, P, M menjadi dependen (explaining away)
- Contoh: Jika alert aktif dan anomali bandwidth terdeteksi, mengetahui port scan juga terdeteksi mengurangi kemungkinan bahwa anomali bandwidth sendiri yang menyebabkan alert

**1c. Markov Blanket (10 poin)**

**MB(AlertSystem):**
- Parents: {B, P, M}
- Children: {R}
- Co-parents of R: {} (hanya A yang parent R)
- **MB(AlertSystem) = {B, P, M, R}**

**MB(SeranganSiber):**
- Parents: {} (root)
- Children: {B, P, M}
- Co-parents of B: {} (hanya S parent B)
- Co-parents of P: {} (hanya S parent P)
- Co-parents of M: {} (hanya S parent M)
- **MB(SeranganSiber) = {B, P, M}**

**1d. D-Separation (15 poin)**

**(i) B dan P | {} (kosong)**
- Path: B ← S → P
- S adalah common cause, S ∉ {} → path **aktif**
- Path: B → A ← P — A adalah collider, A ∉ {} → path **terblokir**
- Ada path aktif (melalui S)
- **B ⊥̸ P | {}** ❌ (dependen — keduanya dipengaruhi S)

**(ii) B dan P | {S}**
- Path: B ← S → P — S ∈ {S}, common cause → **terblokir**
- Path: B → A ← P — A collider, A ∉ {S} → **terblokir**
- Semua path terblokir
- **B ⊥ P | {S}** ✅ (independen — jika kita tahu ada/tidak serangan, indikator independen)

**(iii) B dan M | {A}**
- Path 1: B ← S → M — S common cause, S ∉ {A} → **aktif**
- Path 2: B → A ← M — A collider, A ∈ {A} → **aktif**
- Ada path aktif
- **B ⊥̸ M | {A}** ❌

**(iv) S dan R | {A}**
- Path 1: S → B → A → R — A ∈ {A}, chain di A → **terblokir** ✅
- Path 2: S → P → A → R — A ∈ {A}, chain di A → **terblokir** ✅
- Path 3: S → M → A → R — A ∈ {A}, chain di A → **terblokir** ✅
- Semua path terblokir
- **S ⊥ R | {A}** ✅ (jika kita tahu alert status, serangan dan respons independen)

**1e. Perhitungan P(S=T | B=T, P=T) (15 poin)**

Query: P(S=T | B=T, P=T). Hidden: M, A, R.

Karena R hanya child dari A dan tidak ancestor dari query/evidence, R tidak mempengaruhi perhitungan dan dapat diabaikan.

**Step 1:** Masukkan evidence B=T, P=T

$$P(S | b, p) = \alpha \sum_m \sum_a P(S) \cdot P(b|S) \cdot P(p|S) \cdot P(m|S) \cdot P(a|b,p,m)$$

**Step 2:** Untuk S=T:

$$P(S=T) \cdot P(b|S=T) \cdot P(p|S=T) = 0.03 × 0.90 × 0.85 = 0.02295$$

Eliminasi M dan A:

$$\sum_m \sum_a P(m|S=T) \cdot P(a|b,p,m)$$

| m | P(m\|S=T) | $\sum_a P(a\|b,p,m)$ | Produk |
|:-:|:---------:|:-------------------:|:------:|
| T | 0.80 | 1.0 (summing a=T + a=F) | 0.80 × 1.0 = 0.80 |
| F | 0.20 | 1.0 | 0.20 × 1.0 = 0.20 |

Tunggu — karena A juga hidden dan bukan evidence, kita perlu menjumlahkan atas A juga, tetapi $\sum_a P(a|b,p,m) = 1$ untuk setiap kombinasi b,p,m.

Karena A dan R bukan evidence dan bukan ancestor dari evidence, mereka tidak mempengaruhi posterior P(S|B,P). Maka:

$$P(S|b,p) = \alpha \cdot P(S) \cdot P(b|S) \cdot P(p|S) \cdot \underbrace{\sum_m P(m|S)}_{=1}$$

Sederhananya:

$$P(S=T|b,p) = \alpha \cdot P(S=T) \cdot P(b|S=T) \cdot P(p|S=T)$$
$$= \alpha \cdot 0.03 \times 0.90 \times 0.85 = \alpha \cdot 0.02295$$

$$P(S=F|b,p) = \alpha \cdot P(S=F) \cdot P(b|S=F) \cdot P(p|S=F)$$
$$= \alpha \cdot 0.97 \times 0.08 \times 0.04 = \alpha \cdot 0.003104$$

**Step 3:** Normalisasi

$$\alpha = \frac{1}{0.02295 + 0.003104} = \frac{1}{0.026054}$$

$$P(S=T | b, p) = \frac{0.02295}{0.026054} \approx 0.881$$

$$P(S=F | b, p) = \frac{0.003104}{0.026054} \approx 0.119$$

**Jawaban:** P(SeranganSiber=T | AnomaliBandwidth=T, PortScanDeteksi=T) ≈ 0.881 (88.1%). Ketika anomali bandwidth dan port scan terdeteksi bersamaan, probabilitas serangan siber meningkat drastis dari 3% (prior) menjadi 88.1%. Ini menunjukkan kekuatan kombinasi evidence — dua indikator independen yang positif secara bersamaan sangat kuat mengindikasikan serangan.

---

#### Studi Kasus 2: Sistem Penilaian Ancaman Maritim

**2a. Topologi dan Parameter (10 poin)**

**Topologi:**
- K → R ← L, K → S ← L, R → T ← S, T → P

**Total parameter:**
- KapalAsingHostil (K): 1 parameter
- KondisiLaut (L): 1 parameter
- DeteksiRadar (R): 4 parameter (2 parents: K, L)
- DeteksiSonar (S): 4 parameter (2 parents: K, L)
- TingkatAncaman (T): 4 parameter (2 parents: R, S)
- KerahkanKapalPerang (P): 2 parameter (1 parent: T)

**Total: 1 + 1 + 4 + 4 + 4 + 2 = 16 parameter**

**Full joint distribution:** 6 variabel Boolean → 2⁶ - 1 = 63 parameter

**Perbandingan:** 16 vs 63 — pengurangan ~75%.

**2b. P(DeteksiRadar = true) (10 poin)**

$$P(R=T) = \sum_k \sum_l P(R=T|k, l) \cdot P(k) \cdot P(l)$$

| K | L | P(K) | P(L) | P(R=T\|K,L) | Produk |
|:-:|:-:|:----:|:----:|:-----------:|:------:|
| T | Baik | 0.05 | 0.70 | 0.95 | 0.05×0.70×0.95 = 0.03325 |
| T | Buruk | 0.05 | 0.30 | 0.65 | 0.05×0.30×0.65 = 0.00975 |
| F | Baik | 0.95 | 0.70 | 0.08 | 0.95×0.70×0.08 = 0.05320 |
| F | Buruk | 0.95 | 0.30 | 0.20 | 0.95×0.30×0.20 = 0.05700 |

$$P(R=T) = 0.03325 + 0.00975 + 0.05320 + 0.05700 = 0.15320$$

**Jawaban:** P(DeteksiRadar=T) ≈ 0.153 (15.3%).

**2c. D-Separation (15 poin)**

**(i) R dan S | {} (kosong)**
- Path 1: R ← K → S — K common cause, K ∉ {} → **aktif**
- Path 2: R ← L → S — L common cause, L ∉ {} → **aktif**
- Path 3: R → T ← S — T collider, T ∉ {} → **terblokir**
- Ada path aktif (path 1 dan 2)
- **R ⊥̸ S | {}** ❌ (berkorelasi karena penyebab bersama K dan L)

**(ii) R dan S | {K, L}**
- Path 1: R ← K → S — K ∈ {K,L}, common cause → **terblokir**
- Path 2: R ← L → S — L ∈ {K,L}, common cause → **terblokir**
- Path 3: R → T ← S — T collider, T ∉ {K,L}, no descendant of T in {K,L} → **terblokir**
- Semua path terblokir
- **R ⊥ S | {K, L}** ✅ (jika K dan L diketahui, radar dan sonar independen)

**(iii) R dan S | {T}**
- Path 1: R ← K → S — K common cause, K ∉ {T} → **aktif**
- Path 2: R ← L → S — L common cause, L ∉ {T} → **aktif**
- Path 3: R → T ← S — T collider, T ∈ {T} → **aktif** (explaining away!)
- Ada multiple path aktif
- **R ⊥̸ S | {T}** ❌ (dependen — baik melalui common causes maupun explaining away di T)

**(iv) K dan L | {R}**
- Path 1: K → R ← L — R collider, R ∈ {R} → **aktif**
- **K ⊥̸ L | {R}** ❌ (explaining away: jika radar mendeteksi, mengetahui kondisi laut buruk mengurangi probabilitas kapal asing)

**2d. P(K=T | R=T, S=T) menggunakan Variable Elimination (20 poin)**

Query: P(K | r, s). Hidden: L, T, P.

Karena P hanya child dari T dan tidak evidence/ancestor evidence, P tidak mempengaruhi perhitungan. Begitu pula T, karena T child dari R dan S (yang sudah evidence), dan T hanya parent dari P.

Jadi: $\sum_T \sum_P$ hanya menghasilkan 1 untuk setiap kasus. Maka cukup eliminasi L:

$$P(K | r, s) = \alpha \cdot P(K) \cdot \sum_l P(l) \cdot P(r|K,l) \cdot P(s|K,l)$$

**Step 1:** Hitung untuk K=T

| L | P(L) | P(R=T\|K=T,L) | P(S=T\|K=T,L) | Produk |
|:-:|:----:|:-------------:|:-------------:|:------:|
| Baik | 0.70 | 0.95 | 0.90 | 0.70×0.95×0.90 = 0.5985 |
| Buruk | 0.30 | 0.65 | 0.55 | 0.30×0.65×0.55 = 0.10725 |

$$\sum_l = 0.5985 + 0.10725 = 0.70575$$

$$f(K=T) = P(K=T) \times 0.70575 = 0.05 \times 0.70575 = 0.035288$$

**Step 2:** Hitung untuk K=F

| L | P(L) | P(R=T\|K=F,L) | P(S=T\|K=F,L) | Produk |
|:-:|:----:|:-------------:|:-------------:|:------:|
| Baik | 0.70 | 0.08 | 0.05 | 0.70×0.08×0.05 = 0.00280 |
| Buruk | 0.30 | 0.20 | 0.15 | 0.30×0.20×0.15 = 0.00900 |

$$\sum_l = 0.00280 + 0.00900 = 0.01180$$

$$f(K=F) = P(K=F) \times 0.01180 = 0.95 \times 0.01180 = 0.011210$$

**Step 3:** Normalisasi

$$\alpha = \frac{1}{0.035288 + 0.011210} = \frac{1}{0.046498}$$

$$P(K=T | r, s) = \frac{0.035288}{0.046498} \approx 0.759$$

$$P(K=F | r, s) = \frac{0.011210}{0.046498} \approx 0.241$$

**Jawaban:** P(KapalAsingHostil=T | DeteksiRadar=T, DeteksiSonar=T) ≈ 0.759 (75.9%). Ketika radar dan sonar keduanya mendeteksi kontak, probabilitas kapal asing hostil meningkat dari 5% (prior) menjadi ~76%. Dual-sensor confirmation memberikan confidence yang tinggi. Namun masih ada ~24% kemungkinan false alarm, terutama karena kondisi laut buruk (P=0.30) dapat meningkatkan false positive di kedua sensor.

**2e. Explaining Away (10 poin)**

**Fenomena explaining away** muncul di beberapa tempat dalam jaringan ini:

**1. K → R ← L (di node DeteksiRadar):**
- Tanpa observasi pada R: K dan L independen
- Jika radar mendeteksi kontak (R=T): mengetahui kondisi laut buruk (L=Buruk) **mengurangi** probabilitas kapal asing hostil
- Penjelasan: Jika laut buruk, radar lebih mungkin memberikan false positive, sehingga deteksi sudah "terjelaskan" oleh kondisi buruk

**Skenario operasional:** Pos komando menerima laporan deteksi radar. Sebelum mengambil tindakan, mereka mengecek kondisi laut. Jika laut bergelombang tinggi (L=Buruk), komandan menilai bahwa deteksi kemungkinan false alarm akibat sea clutter, dan probabilitas ancaman nyata menurun.

**2. R → T ← S (di node TingkatAncaman):**
- Jika TingkatAncaman = tinggi (T=T): mengetahui radar mendeteksi (R=T) **mengurangi** pentingnya konfirmasi sonar
- Penjelasan: Tingkat ancaman tinggi sudah bisa dijelaskan oleh deteksi radar saja

**Skenario operasional:** Alert tingkat ancaman tinggi aktif. Jika dikonfirmasi bahwa deteksi radar valid, kebutuhan menunggu konfirmasi sonar berkurang karena satu sensor sudah cukup menjelaskan tingkat ancaman. Namun jika radar tidak mendeteksi, sonar menjadi satu-satunya penjelasan sehingga bobotnya meningkat.

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 125 poin

### Studi Kasus
- Studi Kasus 1: 65 poin
- Studi Kasus 2: 65 poin
- Total: 130 poin

### Total Keseluruhan: 295 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
