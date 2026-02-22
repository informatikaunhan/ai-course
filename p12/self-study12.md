# Panduan Belajar Mandiri Pertemuan 12: Jaringan Bayesian

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 12  
**Topik:** Jaringan Bayesian  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  
**Estimasi Waktu:** 360 menit (~6 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, mahasiswa diharapkan mampu:

1. Menjelaskan motivasi dan keunggulan Jaringan Bayesian untuk penalaran probabilistik
2. Membangun struktur Jaringan Bayesian (DAG) dan Conditional Probability Tables (CPT)
3. Menghitung joint probability distribution dari struktur jaringan
4. Melakukan inferensi eksak pada Bayesian Network sederhana
5. Menerapkan konsep conditional independence dan D-separation
6. Menganalisis contoh Bayesian Network dalam konteks diagnosis dan decision support

---

## 1. Review Konsep: Struktur dan Semantik Jaringan Bayesian (45 menit)

### Ringkasan Materi

**Jaringan Bayesian** (Bayesian Network/Bayes Net) adalah representasi grafis compact dari distribusi probabilitas gabungan yang mengeksploitasi **conditional independence** antar variabel.

**Mengapa Bayesian Networks?**

Full joint probability table untuk n variabel Boolean memerlukan $2^n - 1$ parameter. Untuk 30 variabel Boolean, itu lebih dari **satu miliar** entri! Bayesian Network mengatasi "curse of dimensionality" ini dengan memanfaatkan struktur dependensi antar variabel.

**Dua Komponen Utama:**

1. **Directed Acyclic Graph (DAG):** Node = variabel, directed edge = dependensi langsung (biasanya kausal)
2. **Conditional Probability Table (CPT):** Untuk setiap node $X_i$, tabel $P(X_i \mid Parents(X_i))$

**Semantik — Chain Rule:**

$$P(x_1, x_2, ..., x_n) = \prod_{i=1}^{n} P(x_i \mid Parents(X_i))$$

**Contoh Alarm Network (Russell & Norvig):**

$$P(b, e, a, j, m) = P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot P(m|a)$$

Alarm Network hanya memerlukan **10 parameter** vs **31 parameter** untuk full joint distribution — pengurangan ~68%.

**Parameter Counting:**

Untuk node Boolean $X_i$ dengan $k$ parent Boolean:
- CPT memiliki $2^k$ baris, masing-masing 1 parameter independen
- Total parameter = $2^k$

![Struktur Dasar Bayesian Network](images/p12-01-bayesian-network-basic-structure.png)

*Gambar 12.1: Struktur dasar Bayesian Network dengan DAG dan CPT*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Struktur dasar Jaringan Bayesian menunjukkan DAG dengan 5 node (Alarm Network) dan tabel CPT
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Vertical hierarchy with DAG at top and CPT tables below
COLORS: 
- Primary: #2563eb (blue) for node circles
- Secondary: #10b981 (green) for probability values
- Accent: #f59e0b (orange) for arrows/edges
- Neutral: #6b7280 (gray) for table borders
- Background: #ffffff (white)
ELEMENTS:
1. Top level: Two oval nodes "Pencurian (B)" and "Gempa (E)" in blue
2. Middle level: One oval node "Alarm (A)" with arrows from B and E
3. Bottom level: Two oval nodes "John Menelepon (J)" and "Mary Menelepon (M)" with arrows from A
4. Small CPT tables beside root nodes: P(B)=0.001, P(E)=0.002
5. Label showing "10 parameter vs 31 full joint"
ARROWS/CONNECTIONS: B→A, E→A, A→J, A→M with orange directed arrows
LABELS: All node names in Indonesian, "DAG", "CPT", parameter counts
SIZE: 900x700 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul Video | Channel | Durasi | URL |
|----|-------------|---------|--------|-----|
| 1 | Bayesian Networks | Steve Brunton | 19:42 | https://www.youtube.com/watch?v=TuGDMj43ehw |
| 2 | Bayesian Networks Explained | Normalized Nerd | 16:08 | https://www.youtube.com/watch?v=HwKjj8SUcjk |
| 3 | Bayes Nets (CS 188 Berkeley) | Berkeley AI | 15:31 | https://www.youtube.com/watch?v=T4l6ltMMcec |

### ✍️ Latihan Pemahaman 1

1. Mengapa full joint distribution tidak praktis untuk domain dengan banyak variabel? Berikan contoh numerik!
2. Sebutkan dua komponen utama Jaringan Bayesian dan jelaskan fungsi masing-masing!
3. Dalam Alarm Network, hitung $P(b, \neg e, a, j, m)$ menggunakan chain rule dan CPT berikut:
   - $P(b) = 0.001$, $P(\neg e) = 0.998$, $P(a|b, \neg e) = 0.94$, $P(j|a) = 0.90$, $P(m|a) = 0.70$
4. Sebuah jaringan memiliki 6 node Boolean, masing-masing memiliki maksimal 2 parent. Berapa jumlah maksimal parameter? Bandingkan dengan full joint distribution!

---

## 2. Review Konsep: Conditional Independence dan D-Separation (45 menit)

### Ringkasan Materi

**Tiga Pola Koneksi Fundamental:**

| Pola | Struktur | B Tidak Diobservasi | B Diobservasi |
|------|----------|:-------------------:|:-------------:|
| **Rantai (Chain)** | A → B → C | ❌ Dependen | ✅ Independen |
| **Penyebab Bersama (Fork)** | A ← B → C | ❌ Dependen | ✅ Independen |
| **Efek Bersama (Collider/V-structure)** | A → B ← C | ✅ Independen | ❌ Dependen |

**Aturan Kunci:**
- **Chain & Fork:** Observasi pada node tengah **memblokir** aliran informasi
- **Collider:** Observasi pada node tengah (atau descendant-nya) **membuka** aliran informasi

**Explaining Away:** Fenomena unik pada V-structure — mengetahui satu penyebab dari efek yang diamati **mengurangi** probabilitas penyebab lain.

Contoh: Pencurian → Alarm ← Gempa. Jika alarm berbunyi dan diketahui ada gempa, maka probabilitas pencurian menurun.

**D-Separation (Directional Separation):**

Variabel $X$ dan $Y$ bersifat **d-separated** oleh set $Z$ jika **setiap undirected path** antara $X$ dan $Y$ **terblokir** oleh $Z$.

| Pola di Node N | Kondisi Terblokir |
|:--------------:|:-----------------:|
| Chain: → N → | N ∈ Z (diobservasi) |
| Fork: ← N → | N ∈ Z (diobservasi) |
| Collider: → N ← | N ∉ Z DAN tidak ada descendant N di Z |

**Markov Blanket:**

> Sebuah node conditionally independent dari seluruh node lain dalam jaringan diberikan **Markov Blanket**-nya, yaitu: parents, children, dan co-parents (parent lain dari children-nya).

![Tiga Pola Koneksi](images/p12-03-three-connection-patterns.png)

*Gambar 12.2: Tiga pola koneksi fundamental dalam Jaringan Bayesian*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Tiga pola koneksi fundamental dalam jaringan Bayesian: Rantai, Penyebab Bersama, Efek Bersama dengan status aktif/terblokir
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Three columns, each showing a pattern with two states (observed/unobserved)
COLORS: 
- Primary: #2563eb (blue) for nodes
- Secondary: #10b981 (green) for "active/dependen" flow
- Accent: #f59e0b (orange) for observed nodes (shaded)
- Warning: #ef4444 (red) for "blocked/independen" indicators
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Left column "Rantai (Chain)": A→B→C, two states showing B unobserved (dependen) and B observed (independen)
2. Middle column "Penyebab Bersama (Fork)": A←B→C, two states
3. Right column "Efek Bersama (Collider)": A→B←C, two states (REVERSED: unobserved=independen, observed=dependen)
4. Green arrows for active information flow, red X for blocked flow
LABELS: "Rantai", "Penyebab Bersama", "Efek Bersama", "Aktif", "Terblokir", "B diobservasi", "B tidak diobservasi"
SIZE: 900x600 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul Video | Channel | Durasi | URL |
|----|-------------|---------|--------|-----|
| 1 | D-Separation in Bayesian Networks | Normalized Nerd | 12:46 | https://www.youtube.com/watch?v=Hs2UGkrhVjg |
| 2 | Conditional Independence in Bayes Nets | Berkeley AI (CS 188) | 12:15 | https://www.youtube.com/watch?v=FUnOdz8-300 |
| 3 | Explaining Away - Bayesian Networks | ritvikmath | 10:33 | https://www.youtube.com/watch?v=wF_YmHXAZTw |

### ✍️ Latihan Pemahaman 2

1. Identifikasi pola koneksi dan tentukan independensi:
   - (a) Hujan → Banjir → Evakuasi (Banjir **tidak** diobservasi)
   - (b) Sensor1 ← Target → Sensor2 (Target **diobservasi**)
   - (c) Jamming → AlarmRadar ← Kerusakan (AlarmRadar **diobservasi**)

2. Jelaskan fenomena "explaining away" menggunakan contoh pertahanan: JammingMusuh → RadarGagal ← KerusakanHardware. Apa yang terjadi jika kita tahu radar gagal dan kemudian menemukan kerusakan hardware?

3. Diberikan jaringan: A → C ← B, C → D, C → E. Tentukan apakah A dan B d-separated jika:
   - (a) Tidak ada variabel yang diobservasi
   - (b) C diobservasi
   - (c) D diobservasi

4. Dalam Alarm Network, tentukan Markov Blanket untuk node Alarm!

---

## 3. Eksplorasi Tools & Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| No | Tool | Deskripsi | URL |
|----|------|-----------|-----|
| 1 | **AIspace2 — Bayes Net Tool** | Membangun dan melakukan inferensi pada Bayesian Network secara visual. Mendukung variable elimination step-by-step. | https://aispace2.github.io/AISpace2/bayes.html |
| 2 | **Bayesnet Playground (SamIam)** | Tool GUI untuk Bayesian Networks dari UCLA. Dapat membangun jaringan, set CPT, dan query. | http://reasoning.cs.ucla.edu/samiam/ |
| 3 | **Netica (Free Student Edition)** | Software profesional untuk Bayesian Networks dengan interface drag-and-drop. | https://www.norsys.com/netica.html |
| 4 | **pgmpy (Python Library)** | Library Python untuk probabilistic graphical models. Mendukung inferensi eksak dan aproksimasi. | https://pgmpy.org/ |
| 5 | **D-Separation Algorithm Visualizer** | Visualisasi interaktif d-separation pada DAG. | https://www.cs.cmu.edu/~dmarg/bayes/ |

### Tugas Eksplorasi

**Tugas 3.1 — AIspace2 (20 menit):**
1. Buka AIspace2 Bayes Net Tool
2. Bangun Alarm Network: 5 node (Burglary, Earthquake, Alarm, JohnCalls, MaryCalls)
3. Masukkan CPT sesuai modul
4. Lakukan query: P(Burglary | JohnCalls=T, MaryCalls=T)
5. Bandingkan hasil dengan perhitungan manual (≈0.284)

**Tugas 3.2 — pgmpy Python (20 menit):**
```python
from pgmpy.models import BayesianNetwork
from pgmpy.factors.discrete import TabularCPD
from pgmpy.inference import VariableElimination

# Definisi struktur
model = BayesianNetwork([
    ('Burglary', 'Alarm'),
    ('Earthquake', 'Alarm'),
    ('Alarm', 'JohnCalls'),
    ('Alarm', 'MaryCalls')
])

# CPT
cpd_b = TabularCPD('Burglary', 2, [[0.999], [0.001]])
cpd_e = TabularCPD('Earthquake', 2, [[0.998], [0.002]])
cpd_a = TabularCPD('Alarm', 2,
    [[0.999, 0.71, 0.06, 0.05],
     [0.001, 0.29, 0.94, 0.95]],
    evidence=['Burglary', 'Earthquake'],
    evidence_card=[2, 2])
cpd_j = TabularCPD('JohnCalls', 2,
    [[0.95, 0.10], [0.05, 0.90]],
    evidence=['Alarm'], evidence_card=[2])
cpd_m = TabularCPD('MaryCalls', 2,
    [[0.99, 0.30], [0.01, 0.70]],
    evidence=['Alarm'], evidence_card=[2])

model.add_cpds(cpd_b, cpd_e, cpd_a, cpd_j, cpd_m)
assert model.check_model()

# Inferensi
infer = VariableElimination(model)
result = infer.query(['Burglary'],
    evidence={'JohnCalls': 1, 'MaryCalls': 1})
print(result)
```

**Tugas 3.3 — D-Separation Verification (20 menit):**
1. Gunakan AIspace2 atau pgmpy untuk memverifikasi d-separation pada Alarm Network
2. Cek: Apakah Burglary ⊥ Earthquake? (Tanpa evidence → Ya, independen)
3. Cek: Apakah Burglary ⊥ Earthquake | Alarm=T? (Dengan evidence → Tidak, dependen karena explaining away)
4. Cek: Apakah JohnCalls ⊥ MaryCalls | Alarm=T? (Ya, independen — common cause terblokir)

---

## 4. Pendalaman dengan Video Lanjutan (60 menit)

### Video Lanjutan

| No | Judul Video | Channel | Durasi | URL |
|----|-------------|---------|--------|-----|
| 1 | Bayesian Networks — Full Course | Normalized Nerd | 45:12 | https://www.youtube.com/watch?v=HwKjj8SUcjk |
| 2 | Variable Elimination Algorithm | Daphne Koller (Stanford) | 17:21 | https://www.youtube.com/watch?v=FDNB0A61PGE |
| 3 | Exact Inference in Bayes Nets | Berkeley AI (CS 188) | 14:56 | https://www.youtube.com/watch?v=A1YtBM0ZGFk |
| 4 | Approximate Inference — Sampling | Berkeley AI (CS 188) | 16:42 | https://www.youtube.com/watch?v=mMqHXqWZHTk |

### Bacaan Tambahan

| No | Sumber | Topik | URL |
|----|--------|-------|-----|
| 1 | AIMA Online (Ch. 13-14) | Bayesian Networks chapter | http://aima.cs.berkeley.edu/ |
| 2 | Stanford CS 228 Notes | Probabilistic Graphical Models | https://ermongroup.github.io/cs228-notes/ |
| 3 | Koller & Friedman Textbook | Probabilistic Graphical Models (advanced) | https://mitpress.mit.edu/books/probabilistic-graphical-models |

### Catatan Pendalaman

Saat menonton video, perhatikan:
- **Variable Elimination:** Bagaimana faktor dibuat, dikalikan, dan dijumlahkan. Perhatikan urutan eliminasi variabel mempengaruhi efisiensi.
- **Approximate Inference:** Pahami konsep sampling (prior sampling, rejection sampling, likelihood weighting). Ini menjadi penting untuk jaringan besar yang tidak praktis untuk inferensi eksak.
- **Hubungan dengan Pertemuan 11:** Bayesian Network menggeneralisasi Teorema Bayes ke banyak variabel. Setiap CPT pada dasarnya adalah aplikasi dari conditional probability.

---

## 5. Latihan Soal Online (90 menit)

### Soal Latihan Terstruktur

**Bagian 1: Struktur dan CPT (30 menit)**

1. Diberikan domain dengan variabel: Cuaca (C), Kemacetan (K), Keterlambatan (T), Kehadiran (H).
   - Cuaca mempengaruhi kemacetan
   - Kemacetan mempengaruhi keterlambatan
   - Keterlambatan mempengaruhi kehadiran
   - Gambarkan DAG dan hitung total parameter (semua Boolean)

2. Sebuah jaringan memiliki node A (root, P(A=T)=0.3), node B dengan parent A, dan node C dengan parent B.
   - CPT B: P(B=T|A=T)=0.8, P(B=T|A=F)=0.4
   - CPT C: P(C=T|B=T)=0.9, P(C=T|B=F)=0.2
   - Hitung P(A=T, B=T, C=T) dan P(C=T) (marginalisasi A dan B)

3. Berapa total parameter jika kita menambahkan node D dengan parent A dan B pada jaringan soal 2?

**Bagian 2: D-Separation dan Conditional Independence (30 menit)**

4. Diberikan jaringan: Flu → Demam ← Malaria, Demam → Rawat_Inap.
   - Apakah Flu ⊥ Malaria? (Tanpa evidence)
   - Apakah Flu ⊥ Malaria | Demam?
   - Apakah Flu ⊥ Malaria | Rawat_Inap?

5. Diberikan jaringan: A → B → D, A → C → D.
   - Sebutkan semua path dari A ke D
   - Apakah B ⊥ C? (Tanpa evidence)
   - Apakah B ⊥ C | A?
   - Apakah B ⊥ C | D?

6. Tentukan Markov Blanket untuk setiap node dalam jaringan soal 4 (Flu, Malaria, Demam, Rawat_Inap).

**Bagian 3: Inferensi (30 menit)**

7. Menggunakan jaringan di soal 2 (A→B→C), hitung P(A=T | C=T) menggunakan enumeration.

8. Diberikan jaringan sederhana: Hujan (H) → Sprinkler (S) dan Hujan (H) → Basah (B), Sprinkler (S) → Basah (B).
   - P(H=T) = 0.3
   - P(S=T|H=T) = 0.1, P(S=T|H=F) = 0.5
   - P(B=T|H=T,S=T) = 0.99, P(B=T|H=T,S=F) = 0.8, P(B=T|H=F,S=T) = 0.9, P(B=T|H=F,S=F) = 0.0
   - Hitung P(H=T | B=T) menggunakan enumeration.

9. Untuk jaringan di soal 8, jelaskan langkah-langkah Variable Elimination untuk menghitung P(H | B=T). Identifikasi faktor awal, urutan eliminasi, dan faktor intermediate.

### Platform Latihan Online

| No | Platform | Topik | URL |
|----|----------|-------|-----|
| 1 | CS 188 Edx | Practice problems on Bayes Nets | https://inst.eecs.berkeley.edu/~cs188/ |
| 2 | pgmpy Tutorial | Hands-on Python Bayesian Network | https://pgmpy.org/started/base.html |
| 3 | Coursera — PGM (Koller) | Probabilistic Graphical Models course | https://www.coursera.org/learn/probabilistic-graphical-models |

---

## 6. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. **Koneksi dengan Pertemuan 11:** Bagaimana Bayesian Network merupakan evolusi dari Teorema Bayes yang dipelajari sebelumnya? Apa keuntungan utama menggunakan representasi grafis?

2. **Pemilihan Urutan Kausal:** Mengapa urutan kausal (sebab → akibat) menghasilkan jaringan yang lebih compact? Apa yang terjadi jika kita membalik urutan?

3. **Aplikasi Pertahanan:** Bayangkan Anda merancang sistem deteksi intrusi siber untuk jaringan militer. Variabel apa saja yang akan Anda masukkan? Bagaimana Anda menentukan struktur DAG-nya?

4. **Explaining Away dalam Kehidupan Nyata:** Berikan contoh fenomena explaining away dalam konteks:
   - (a) Diagnosis kegagalan peralatan militer
   - (b) Analisis intelijen (multiple hypothesis)
   - (c) Sistem alarm keamanan

5. **Skalabilitas:** Apa keterbatasan inferensi eksak (enumeration, variable elimination) pada jaringan besar? Mengapa approximate inference (sampling) diperlukan?

6. **Koneksi ke Machine Learning:** Bagaimana Bayesian Network berhubungan dengan Naive Bayes classifier yang dipelajari di Pertemuan 11? Apa perbedaan dan kesamaannya?

### Topik Diskusi Kelompok

**Diskusi 1: Aplikasi BN dalam C4ISR**

Sistem Command, Control, Communications, Computers, Intelligence, Surveillance, and Reconnaissance (C4ISR) melibatkan banyak sumber informasi dengan ketidakpastian. Diskusikan:
- Bagaimana Bayesian Network dapat digunakan untuk fusi data dari multiple sensor?
- Apa tantangan dalam menentukan CPT untuk domain militer di mana data historis terbatas?
- Bagaimana explaining away dapat membantu membedakan ancaman nyata dari false alarm?

**Diskusi 2: BN vs Logika**

Bandingkan pendekatan berbasis logika (Pertemuan 9-10) dengan pendekatan probabilistik (Pertemuan 11-12):
- Kapan logika lebih sesuai? Kapan probabilitas lebih sesuai?
- Apakah mungkin menggabungkan keduanya? (Hint: probabilistic logic)
- Berikan contoh skenario pertahanan untuk masing-masing pendekatan

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Struktur dan Semantik Bayesian Network selesai
- [ ] Section 2: Review Conditional Independence dan D-Separation selesai
- [ ] Section 3: Tools interaktif dieksplorasi
- [ ] Section 4: Video lanjutan ditonton
- [ ] Section 5: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 6: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### Buku dan Artikel
1. Koller, D. & Friedman, N. (2009). *Probabilistic Graphical Models*. MIT Press — Referensi komprehensif
2. Pearl, J. (2009). *Causality*. Cambridge University Press — Teori kausal menggunakan Bayesian Networks
3. Jensen, F.V. & Nielsen, T.D. (2007). *Bayesian Networks and Decision Graphs*. Springer — Fokus pada aplikasi

### Video Playlist
4. Daphne Koller — Probabilistic Graphical Models (Stanford): https://www.youtube.com/playlist?list=PL50E6E80E8525B59C
5. Normalized Nerd — Bayesian Networks Series: https://www.youtube.com/playlist?list=PLM8wYQRetTxBkdvBtz-gw8b9lcVkdXQKV

### Tools Tambahan
6. **GeNIe Modeler** — Software gratis untuk Bayesian Networks: https://www.bayesfusion.com/genie/
7. **bnlearn (R package)** — Library R untuk learning dan inferensi BN: https://www.bnlearn.com/

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

**1.** Untuk 20 variabel Boolean, full joint memerlukan $2^{20} - 1 = 1.048.575$ parameter. Untuk 30 variabel: $2^{30} - 1 \approx 1.07$ miliar — tidak praktis untuk disimpan atau dihitung.

**2.**
- **DAG (Directed Acyclic Graph):** Merepresentasikan struktur dependensi antar variabel. Node = variabel, directed edge = hubungan dependensi langsung (biasanya kausal).
- **CPT (Conditional Probability Table):** Untuk setiap node, menyimpan distribusi probabilitas kondisional $P(X_i | Parents(X_i))$. Berisi parameter numerik yang mendefinisikan hubungan kuantitatif.

**3.**
$$P(b, \neg e, a, j, m) = 0.001 \times 0.998 \times 0.94 \times 0.90 \times 0.70$$
$$= 0.001 \times 0.998 \times 0.94 \times 0.63$$
$$= 0.001 \times 0.998 \times 0.5922$$
$$\approx 0.000591$$

**4.** 6 node Boolean, masing-masing maks 2 parent:
- Maks parameter per node: $2^2 = 4$
- Total maks: $6 \times 4 = 24$ parameter (kasus terburuk; root node hanya 1 parameter)
- Lebih realistis: misalnya 2 root (2×1) + 4 node dengan 2 parent (4×4) = 2 + 16 = 18 parameter
- Full joint: $2^6 - 1 = 63$ parameter — pengurangan signifikan!

### Section 2

**1.**
- (a) Chain, B tidak diobservasi → **Dependen** (informasi mengalir dari Hujan ke Evakuasi melalui Banjir)
- (b) Fork/Common Cause, B diobservasi → **Independen** (mengetahui Target memblokir aliran informasi antara Sensor1 dan Sensor2)
- (c) Collider/V-structure, B diobservasi → **Dependen** (observasi pada AlarmRadar mengaktifkan dependensi — explaining away)

**2.** Tanpa informasi tentang RadarGagal, JammingMusuh dan KerusakanHardware independen. Namun jika kita tahu radar gagal (RadarGagal = True), ada dua kemungkinan penyebab. Jika kemudian ditemukan kerusakan hardware (KerusakanHardware = True), maka kegagalan radar sudah "terjelaskan" oleh kerusakan. Akibatnya, probabilitas bahwa musuh melakukan jamming **menurun**: $P(\text{Jamming} | \text{RadarGagal}, \text{Kerusakan}) < P(\text{Jamming} | \text{RadarGagal})$.

**3.** Jaringan: A → C ← B, C → D, C → E.
- (a) **Tidak ada observasi:** Path A → C ← B memiliki collider di C. C tidak diobservasi → path **terblokir** → A ⊥ B ✅
- (b) **C diobservasi:** Collider C diobservasi → path **aktif** → A ⊥̸ B (dependen) ❌
- (c) **D diobservasi:** D adalah descendant dari C. Observasi pada descendant collider mengaktifkan path → A ⊥̸ B (dependen) ❌

**4.** Markov Blanket Alarm = {Parents, Children, Co-parents} = {Burglary, Earthquake, JohnCalls, MaryCalls}. (Alarm tidak memiliki co-parents karena JohnCalls dan MaryCalls hanya punya Alarm sebagai parent.)

### Section 5

**Soal 1:**
DAG: C → K → T → H (chain). Total parameter: C=1, K=2, T=2, H=2 → **7 parameter** vs $2^4 - 1 = 15$ full joint.

**Soal 2:**
$P(A=T, B=T, C=T) = P(A=T) \cdot P(B=T|A=T) \cdot P(C=T|B=T) = 0.3 \times 0.8 \times 0.9 = 0.216$

$P(C=T)$: Marginalisasi A dan B:
$$P(C=T) = \sum_{a}\sum_{b} P(a) \cdot P(b|a) \cdot P(C=T|b)$$

| A | B | P(A) | P(B\|A) | P(C=T\|B) | Produk |
|:-:|:-:|:----:|:-------:|:---------:|:------:|
| T | T | 0.3 | 0.8 | 0.9 | 0.216 |
| T | F | 0.3 | 0.2 | 0.2 | 0.012 |
| F | T | 0.7 | 0.4 | 0.9 | 0.252 |
| F | F | 0.7 | 0.6 | 0.2 | 0.084 |

$$P(C=T) = 0.216 + 0.012 + 0.252 + 0.084 = 0.564$$

**Soal 3:** Node D dengan parent A dan B: CPT memerlukan $2^2 = 4$ parameter. Total jaringan: A(1) + B(2) + C(2) + D(4) = **9 parameter**.

**Soal 4:**
- Flu ⊥ Malaria? Path: Flu → Demam ← Malaria. Collider di Demam, tidak diobservasi → **terblokir** → Flu ⊥ Malaria ✅
- Flu ⊥ Malaria | Demam? Collider Demam diobservasi → **aktif** → Flu ⊥̸ Malaria ❌ (explaining away!)
- Flu ⊥ Malaria | Rawat_Inap? Rawat_Inap adalah descendant dari Demam (collider). Observasi descendant → **aktif** → Flu ⊥̸ Malaria ❌

**Soal 5:**
- Path dari A ke D: (1) A → B → D, (2) A → C → D
- B ⊥ C? Tanpa evidence, path B ← A → C memiliki fork di A, A tidak diobservasi → **dependen** → B ⊥̸ C
- B ⊥ C | A? Fork A diobservasi → **terblokir** → B ⊥ C | A ✅
- B ⊥ C | D? Path B → D ← C memiliki collider di D, D diobservasi → **aktif** → B ⊥̸ C | D

**Soal 6:** Markov Blanket:
- Flu: {Demam} (child) — Malaria juga co-parent → **{Demam, Malaria}**
- Malaria: {Demam} (child), Flu adalah co-parent → **{Demam, Flu}**
- Demam: {Flu, Malaria} (parents) + {Rawat_Inap} (child) → **{Flu, Malaria, Rawat_Inap}**
- Rawat_Inap: {Demam} (parent) → **{Demam}**

**Soal 7:** P(A=T | C=T) menggunakan enumeration:

$$P(A=T | C=T) = \frac{P(A=T, C=T)}{P(C=T)}$$

Dari Soal 2: P(C=T) = 0.564

$P(A=T, C=T) = \sum_b P(A=T) \cdot P(b|A=T) \cdot P(C=T|b)$
$= 0.3 \times 0.8 \times 0.9 + 0.3 \times 0.2 \times 0.2 = 0.216 + 0.012 = 0.228$

$$P(A=T | C=T) = \frac{0.228}{0.564} \approx 0.404$$

**Soal 8:** P(H=T | B=T):

$$P(H=T | B=T) = \frac{P(B=T | H=T) \cdot P(H=T)}{P(B=T)}$$

$P(B=T | H=T) = \sum_s P(B=T|H=T,s) \cdot P(s|H=T)$
$= P(B=T|H=T,S=T) \cdot P(S=T|H=T) + P(B=T|H=T,S=F) \cdot P(S=F|H=T)$
$= 0.99 \times 0.1 + 0.8 \times 0.9 = 0.099 + 0.72 = 0.819$

$P(B=T | H=F) = P(B=T|H=F,S=T) \cdot P(S=T|H=F) + P(B=T|H=F,S=F) \cdot P(S=F|H=F)$
$= 0.9 \times 0.5 + 0.0 \times 0.5 = 0.45 + 0.0 = 0.45$

$P(B=T) = P(B=T|H=T) \cdot P(H=T) + P(B=T|H=F) \cdot P(H=F)$
$= 0.819 \times 0.3 + 0.45 \times 0.7 = 0.2457 + 0.315 = 0.5607$

$$P(H=T | B=T) = \frac{0.819 \times 0.3}{0.5607} = \frac{0.2457}{0.5607} \approx 0.438$$

**Soal 9:** Variable Elimination untuk P(H | B=T):

*Step 1:* Faktor awal: $f_H(H)$, $f_S(S,H)$, $f_B(B,H,S)$

*Step 2:* Set evidence B=T → $f_B$ menjadi $f_{B=T}(H,S)$

*Step 3:* Eliminasi S (karena S bukan query dan bukan evidence):
- Kalikan faktor yang mengandung S: $f_S(S,H) \times f_{B=T}(H,S) = f_1(H,S)$
- Jumlahkan S: $f_2(H) = \sum_S f_1(H,S)$

*Step 4:* Kalikan faktor tersisa: $f_3(H) = f_H(H) \times f_2(H)$

*Step 5:* Normalisasi: $P(H | B=T) = \alpha \cdot f_3(H)$

Hasil: $P(H=T | B=T) \approx 0.438$

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
