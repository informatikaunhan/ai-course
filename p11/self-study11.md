# Panduan Belajar Mandiri Pertemuan 11: Penalaran dengan Ketidakpastian - Probabilitas

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 11  
**Topik:** Penalaran dengan Ketidakpastian - Probabilitas  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  
**Estimasi Waktu:** 420 menit (~7 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan panduan belajar mandiri ini, mahasiswa diharapkan mampu:

1. Menjelaskan mengapa ketidakpastian muncul dalam sistem AI dan keterbatasan logika formal
2. Menerapkan konsep probabilitas dasar: prior, posterior, joint probability
3. Menggunakan Teorema Bayes untuk inferensi probabilistik
4. Memahami konsep independensi dan independensi bersyarat
5. Menerapkan Naive Bayes classifier untuk klasifikasi sederhana
6. Menganalisis aplikasi penalaran probabilistik dalam konteks pertahanan

---

## 1. Review Konsep: Ketidakpastian dalam AI (45 menit)

### Ringkasan Materi

Dalam dunia nyata, sistem AI sering menghadapi **ketidakpastian** (uncertainty). Berbeda dengan logika formal yang hanya mengenal benar atau salah, banyak situasi yang memerlukan penalaran dengan informasi tidak lengkap atau tidak pasti.

**Sumber Ketidakpastian:**

1. **Laziness (Kemalasan Teoritis):** Terlalu kompleks untuk membuat model sempurna. Contoh: Memprediksi cuaca memerlukan model fisika yang sangat detail hingga level molekul — tidak praktis!

2. **Ignorance (Ketidaktahuan Praktis):** Informasi tidak tersedia atau sensor tidak sempurna. Contoh: Radar tidak bisa mendeteksi pesawat stealth dengan sempurna.

**Keterbatasan Logika untuk Ketidakpastian:**

Logika proposisional/predikat hanya menangani pernyataan yang pasti benar atau salah. Tetapi bagaimana kita menyatakan: "Kemungkinan hujan besok adalah 70%"? Di sinilah probabilitas diperlukan.

| Keterbatasan Logika | Penjelasan |
|---------------------|------------|
| **Biner** | Hanya TRUE/FALSE, tidak ada derajat kepercayaan |
| **Monotonic** | Menambah informasi tidak pernah membatalkan kesimpulan lama |
| **Closed-world assumption** | Yang tidak diketahui dianggap salah |
| **Qualification problem** | Tidak mungkin mendaftar semua prasyarat untuk sebuah aturan |

> **Solusi:** Daripada logika biner, kita menggunakan **derajat kepercayaan (degree of belief)** yang direpresentasikan sebagai **probabilitas**.

![Sumber Ketidakpastian AI](images/p11-01-uncertainty-sources.png)

*Gambar 11.1: Dua sumber ketidakpastian dalam sistem AI*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Two sources of uncertainty in AI systems - theoretical laziness and practical ignorance
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Horizontal split showing two main sources with examples
COLORS: 
- Primary: #2563eb (blue) for main boxes
- Secondary: #10b981 (green) for laziness box
- Accent: #f59e0b (orange) for ignorance box
- Warning: #ef4444 (red) for problem indicators
- Neutral: #6b7280 (gray) for text
- Background: #ffffff (white)
ELEMENTS:
1. Left side: Box labeled "LAZINESS (Kemalasan Teoritis)"
   - Icon: Brain with too many connections
   - Example 1: "Model cuaca sempurna terlalu kompleks"
   - Example 2: "Perhitungan terlalu mahal"
2. Right side: Box labeled "IGNORANCE (Ketidaktahuan Praktis)"
   - Icon: Eye with blind spot
   - Example 1: "Sensor radar tidak sempurna"
   - Example 2: "Informasi tersembunyi"
3. Center bottom: "SOLUSI: Penalaran Probabilistik" with probability icon (dice/percentage)
ARROWS/CONNECTIONS: Both boxes pointing down to solution
LABELS: "LAZINESS (Kemalasan Teoritis)", "IGNORANCE (Ketidaktahuan Praktis)", "Model terlalu kompleks", "Sensor tidak sempurna", "SOLUSI: Penalaran Probabilistik"
SIZE: 900x500 pixels
FORMAT: PNG, latar belakang putih
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Probability explained (Bayes Theorem) | 3Blue1Brown | 22:19 | https://www.youtube.com/watch?v=HZGCoVF3YvM |
| 2 | Probability and Statistics in AI | Computerphile | 11:47 | https://www.youtube.com/watch?v=o2VkE1a9uMo |
| 3 | Uncertainty in Artificial Intelligence | MIT OpenCourseWare | 48:12 | https://www.youtube.com/watch?v=8L8i9BNMHk4 |

### ✍️ Latihan Pemahaman

Setelah menonton video, jawab pertanyaan berikut:

1. Mengapa logika proposisional tidak cukup untuk menangani ketidakpastian dalam sistem AI?
2. Berikan contoh situasi "laziness" dalam konteks sistem pertahanan militer!
3. Berikan contoh situasi "ignorance" dalam sistem radar TNI AU!
4. Bagaimana probabilitas dapat membantu mengatasi kedua sumber ketidakpastian tersebut?

---

## 2. Review Konsep: Probabilitas Dasar (60 menit)

### Ringkasan Materi

**Konsep Dasar Probabilitas:**

1. **Prior Probability (Probabilitas Prior):** P(A) — Probabilitas suatu kejadian sebelum melihat bukti baru
   - Contoh: P(Pesawat Musuh) = 0.001 (1 dari 1000 deteksi radar adalah pesawat musuh)

2. **Joint Probability:** P(A ∧ B) — Probabilitas dua kejadian terjadi bersamaan
   - Contoh: P(Deteksi Radar ∧ Pesawat Musuh)

3. **Conditional Probability (Probabilitas Bersyarat):** P(A|B) — Probabilitas A jika B diketahui benar
   - P(A|B) = P(A ∧ B) / P(B)
   - Contoh: P(Pesawat Musuh | Deteksi Radar)

**Aturan Produk:**

$$P(A \wedge B) = P(A|B) \times P(B) = P(B|A) \times P(A)$$

**Aksioma Kolmogorov:**

| Aksioma | Formula | Makna |
|---------|---------|-------|
| Non-negativity | $0 \leq P(A) \leq 1$ | Probabilitas selalu antara 0 dan 1 |
| Normalization | $P(\Omega) = 1$ | Probabilitas total = 1 |
| Additivity | $P(A \cup B) = P(A) + P(B)$ (jika mutually exclusive) | Untuk event saling lepas, jumlahkan |

**Hukum Komplemen:**

$$P(\neg A) = 1 - P(A)$$

**Aturan Inclusion-Exclusion (untuk event yang TIDAK saling lepas):**

$$P(A \cup B) = P(A) + P(B) - P(A \wedge B)$$

![Konsep Probabilitas Bersyarat](images/p11-02-conditional-probability.png)

*Gambar 11.2: Visualisasi probabilitas bersyarat dengan diagram Venn*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Conditional probability visualization using Venn diagram with military context
STYLE: Clean flat vector illustration, educational mathematics diagram, textbook quality, minimal design
LAYOUT: Central Venn diagram with formulas around it
COLORS: 
- Primary: #2563eb (blue) for circle A "Deteksi Radar"
- Secondary: #10b981 (green) for circle B "Pesawat Musuh"
- Accent: #f59e0b (orange) for intersection A∩B
- Neutral: #6b7280 (gray) for labels and formulas
- Background: #ffffff (white)
ELEMENTS:
1. Venn diagram with two overlapping circles
   - Circle A (blue): "Alarm Radar" 
   - Circle B (green): "Pesawat Musuh Sebenarnya"
   - Intersection (orange): "True Positive"
2. Formulas around:
   - Top: "P(A|B) = P(A∩B) / P(B)"
   - Bottom: "P(B|A) = P(A∩B) / P(A)"
3. Labels: "False Alarm" (A only), "Missed Detection" (B only)
ARROWS/CONNECTIONS: Lines from intersection to formula
LABELS: "P(A|B)", "P(B|A)", "True Positive", "False Alarm", "Tidak Terdeteksi"
SIZE: 800x600 pixels
FORMAT: PNG, latar belakang putih
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Conditional Probability Explained | StatQuest | 6:44 | https://www.youtube.com/watch?v=_IgyaD7vOOA |
| 2 | Joint and Conditional Probability | Khan Academy | 9:14 | https://www.youtube.com/watch?v=xPUm5SUVzTE |
| 3 | Probability in Artificial Intelligence | Stanford CS221 | 37:50 | https://www.youtube.com/watch?v=sDNbGCKsMWQ |

### ✍️ Latihan Pemahaman

1. Dua sensor independen masing-masing memiliki probabilitas false alarm 5%. Hitung probabilitas setidaknya satu false alarm terjadi!
2. Jelaskan perbedaan antara P(Hujan | Awan) dan P(Awan | Hujan). Mana yang lebih besar biasanya? Mengapa?
3. Jika P(Serangan) = 0.02 dan P(Alarm | Serangan) = 0.90, hitung P(Alarm ∧ Serangan)!
4. Dalam konteks IFF (Identification Friend or Foe), apa yang direpresentasikan oleh P(Musuh | Sinyal)?

---

## 3. Review Konsep: Teorema Bayes (60 menit)

### Ringkasan Materi

**Teorema Bayes** adalah formula fundamental untuk memperbarui kepercayaan berdasarkan bukti baru:

$$P(H|E) = \frac{P(E|H) \cdot P(H)}{P(E)}$$

| Komponen | Nama | Makna |
|----------|------|-------|
| $P(H \mid E)$ | **Posterior** | Probabilitas hipotesis setelah melihat bukti |
| $P(E \mid H)$ | **Likelihood** | Probabilitas bukti muncul jika hipotesis benar |
| $P(H)$ | **Prior** | Probabilitas hipotesis sebelum bukti |
| $P(E)$ | **Evidence** | Total probabilitas bukti (normalisasi) |

**Hukum Total Probability** untuk menghitung P(E):

$$P(E) = P(E|H) \cdot P(H) + P(E|\neg H) \cdot P(\neg H)$$

**Bayesian Updating:** Posterior dari observasi pertama menjadi prior untuk observasi berikutnya. Proses ini dapat diulang secara sekuensial untuk mengintegrasikan bukti baru.

**Base Rate Fallacy:** Kesalahan umum di mana seseorang mengabaikan prior probability dan terlalu fokus pada likelihood. Sangat berbahaya dalam konteks peringatan dini militer!

**Contoh Klasik — Deteksi Radar:**
- Prior: P(Musuh) = 0.001
- Likelihood: P(Alarm | Musuh) = 0.95
- False alarm: P(Alarm | ¬Musuh) = 0.05

$$P(\text{Musuh} \mid \text{Alarm}) = \frac{0.95 \times 0.001}{0.95 \times 0.001 + 0.05 \times 0.999} = \frac{0.00095}{0.05090} = 0.0187$$

Meskipun radar 95% akurat, hanya **1.87%** dari alarm menunjukkan musuh sebenarnya! Ini adalah base rate effect.

![Teorema Bayes](images/p11-03-bayes-theorem.png)

*Gambar 11.3: Komponen Teorema Bayes dan alur inferensi*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Bayes Theorem components and inference flow in military context
STYLE: Clean flat vector illustration, educational diagram, textbook quality, minimal design
LAYOUT: Horizontal flow diagram with formula in center
COLORS: 
- Primary: #2563eb (blue) for prior
- Secondary: #10b981 (green) for likelihood
- Accent: #f59e0b (orange) for posterior (result)
- Warning: #ef4444 (red) for evidence/denominator
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Left box (blue): "PRIOR P(H)" with label "Kepercayaan Awal" and example "P(Musuh) = 0.001"
2. Top box (green): "LIKELIHOOD P(E|H)" with label "Kekuatan Bukti" and example "P(Alarm|Musuh) = 0.95"
3. Center: Large formula "P(H|E) = P(E|H)×P(H) / P(E)"
4. Bottom box (red): "EVIDENCE P(E)" with label "Normalisasi"
5. Right box (orange, highlighted): "POSTERIOR P(H|E)" with label "Kepercayaan Diperbarui" and example "P(Musuh|Alarm) = ?"
6. Arrow flow: Prior + Likelihood → Formula → Posterior
ARROWS/CONNECTIONS: Arrows from prior and likelihood into formula, output to posterior
LABELS: "Prior", "Likelihood", "Evidence", "Posterior", "Kepercayaan Awal", "Kekuatan Bukti", "Normalisasi", "Kepercayaan Diperbarui"
SIZE: 1000x550 pixels
FORMAT: PNG, latar belakang putih
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Bayes theorem, the geometry of changing beliefs | 3Blue1Brown | 15:11 | https://www.youtube.com/watch?v=lG4VkPoG3ko |
| 2 | A visual guide to Bayesian thinking | Julia Galef | 11:25 | https://www.youtube.com/watch?v=BrK7X_XlGB8 |
| 3 | Bayesian Reasoning in AI | Computerphile | 13:45 | https://www.youtube.com/watch?v=kp1QDjDkHEI |
| 4 | The Bayesian Trap | Veritasium | 10:34 | https://www.youtube.com/watch?v=R13BD8qKeTg |

### ✍️ Latihan Pemahaman

1. Sebuah sensor kebakaran memiliki true positive rate 98% dan false positive rate 3%. Jika probabilitas kebakaran adalah 0.5%, hitung P(Kebakaran | Alarm)!

2. Melanjutkan soal di atas: Jika alarm berbunyi dua kali berturut-turut (deteksi independen), berapa posterior setelah alarm kedua? (Gunakan Bayesian updating!)

3. Jelaskan dengan kata-kata Anda sendiri mengapa base rate fallacy berbahaya untuk operator sistem peringatan dini militer!

4. Kapan prior probability sangat mempengaruhi hasil, dan kapan likelihood lebih dominan? Berikan contoh masing-masing!

---

## 4. Eksplorasi Tools & Visualisasi Interaktif (45 menit)

### 🛠️ Tools yang Direkomendasikan

| No | Tool | Deskripsi | Link |
|----|------|-----------|------|
| 1 | **Seeing Theory (Brown University)** | Visualisasi interaktif konsep probabilitas termasuk Bayesian inference | https://seeing-theory.brown.edu/ |
| 2 | **Bayesian Calculator** | Kalkulator online untuk Teorema Bayes dengan diagram visual | https://www.omnicalculator.com/statistics/bayes-theorem |
| 3 | **Arbital: Bayes' Rule** | Penjelasan intuitif dan interaktif tentang Teorema Bayes | https://arbital.com/p/bayes_rule/ |
| 4 | **GeoGebra Probability** | Tool matematika untuk eksplorasi distribusi probabilitas | https://www.geogebra.org/probability |
| 5 | **Naive Bayes Visualizer** | Visualisasi klasifikasi Naive Bayes step-by-step | https://stanford.edu/~shervine/teaching/cs-229/cheatsheet-naive-bayes |

### Tugas Eksplorasi

**Tugas 1: Seeing Theory — Bayesian Inference (20 menit)**
1. Buka https://seeing-theory.brown.edu/bayesian-inference/index.html
2. Eksplorasi tab "Bayes' Theorem"
3. Atur parameter prior dan likelihood, amati perubahan posterior
4. **Catat:** Apa yang terjadi ketika prior sangat rendah tetapi likelihood sangat tinggi?

**Tugas 2: Bayesian Calculator (15 menit)**
1. Buka https://www.omnicalculator.com/statistics/bayes-theorem
2. Masukkan skenario deteksi radar:
   - P(Event) = 0.001
   - P(Positive | Event) = 0.95
   - P(Positive | No Event) = 0.05
3. Verifikasi bahwa hasilnya ≈ 1.87%
4. **Eksperimen:** Ubah P(Event) menjadi 0.01, lalu 0.10. Bagaimana posterior berubah?

**Tugas 3: Explorasi Naive Bayes (10 menit)**
1. Kunjungi Stanford ML cheatsheet untuk Naive Bayes
2. Pelajari visualisasi decision boundary
3. **Catat:** Apa perbedaan decision boundary Naive Bayes vs Decision Tree?

---

## 5. Review Konsep: Independensi dan Naive Bayes (60 menit)

### Ringkasan Materi

**Independensi:**

Dua event A dan B independen jika:

$$P(A \wedge B) = P(A) \cdot P(B)$$

Atau ekuivalen: $P(A|B) = P(A)$ — mengetahui B tidak mengubah probabilitas A.

**Contoh:** Dua sensor radar yang memantau wilayah berbeda — hasil deteksi satu sensor tidak mempengaruhi yang lain.

**Independensi Bersyarat (Conditional Independence):**

A dan B conditionally independent given C jika:

$$P(A \wedge B \mid C) = P(A \mid C) \cdot P(B \mid C)$$

**Contoh:** Dua sensor radar yang memantau target YANG SAMA. Noise masing-masing sensor independen given keberadaan target. Jika kita sudah tahu ada target, alarm sensor 1 tidak memberikan informasi tambahan tentang alarm sensor 2.

> **Penting:** Independensi dan independensi bersyarat adalah konsep BERBEDA yang tidak saling menyiratkan!

**Naive Bayes Classifier:**

Naive Bayes menggunakan asumsi conditional independence untuk klasifikasi:

$$P(C|F_1, F_2, ..., F_n) \propto P(C) \prod_{i=1}^{n} P(F_i|C)$$

Dimana:
- C = Class (kategori)
- $F_1, F_2, ..., F_n$ = Features (fitur)
- Asumsi "naive": semua fitur independen given kelas

**Mengapa disebut "Naive"?** Karena asumsi independensi hampir tidak pernah benar di dunia nyata. Meskipun demikian, Naive Bayes sering bekerja dengan baik karena:
1. Klasifikasi hanya butuh **ranking** yang benar, bukan probabilitas yang tepat
2. Error overestimate dan underestimate sering saling cancel out
3. Decision boundary masih mendekati optimal

**Laplace Smoothing:**

Mengatasi masalah zero probability (fitur yang tidak muncul di training data):

$$P(F_i | C) = \frac{\text{count}(F_i, C) + \alpha}{N_C + \alpha \cdot k}$$

dimana $\alpha = 1$ (biasanya) dan $k$ = jumlah kemungkinan nilai fitur.

**Aplikasi:**
- Spam filtering
- Text classification
- Sentiment analysis
- Diagnosis medis
- Threat classification

![Naive Bayes Classifier](images/p11-04-naive-bayes.png)

*Gambar 11.4: Proses klasifikasi dengan Naive Bayes*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Naive Bayes classification process showing feature independence assumption
STYLE: Clean flat vector illustration, educational machine learning diagram, textbook quality, minimal design
LAYOUT: Vertical flow diagram showing classification steps
COLORS: 
- Primary: #2563eb (blue) for input features
- Secondary: #10b981 (green) for class 1
- Accent: #ef4444 (red) for class 2
- Warning: #f59e0b (orange) for probability calculations
- Neutral: #6b7280 (gray) for arrows
- Background: #ffffff (white)
ELEMENTS:
1. Top: "INPUT" box with features F1, F2, F3 (blue icons)
   - Label: "Fitur: F1, F2, F3"
2. Middle: "ASUMSI INDEPENDENSI" box (orange)
   - Formula: "P(C|F1,F2,F3) ∝ P(C) × P(F1|C) × P(F2|C) × P(F3|C)"
   - Note: "Semua fitur independen"
3. Left branch: "Class 1" box (green)
   - Show calculation for P(C1|F)
4. Right branch: "Class 2" box (red)
   - Show calculation for P(C2|F)
5. Bottom: "KEPUTUSAN" box
   - "Pilih class dengan P(C|F) tertinggi"
   - Winner icon
ARROWS/CONNECTIONS: Flow from input → calculation → decision
LABELS: "Input", "Fitur", "Asumsi Independensi", "Class 1", "Class 2", "Keputusan", "Probabilitas tertinggi"
SIZE: 700x900 pixels
FORMAT: PNG, latar belakang putih
NEGATIVE: No gradients, no 3D effects, no photorealistic elements, no complex textures
</prompt>

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Naive Bayes, Clearly Explained | StatQuest | 15:12 | https://www.youtube.com/watch?v=O2L2Uv9pdDA |
| 2 | Naive Bayes Classifier | Normalized Nerd | 14:32 | https://www.youtube.com/watch?v=nHIUYwN-5rM |
| 3 | How Naive Bayes Classifiers Work | Computerphile | 11:55 | https://www.youtube.com/watch?v=IlVINQDk4o8 |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 12-13 (Sections 12.1-12.3, 13.1-13.3)
- "The Master Algorithm" by Pedro Domingos — Chapter on Bayesians
- Article: "Bayesian Methods for Hackers" — https://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/

### ✍️ Latihan Pemahaman

1. Dua sensor sonar independen masing-masing memiliki detection rate 80%. Hitung probabilitas setidaknya satu mendeteksi target!
2. Jelaskan mengapa asumsi Naive Bayes disebut "naive" dan berikan contoh pelanggaran asumsi ini!
3. Dalam sistem klasifikasi email militer, kata "rahasia" dan "koordinat" sering muncul bersamaan. Bagaimana ini mempengaruhi klasifikasi Naive Bayes?
4. Apa fungsi Laplace smoothing? Berikan contoh numerik sederhana!

---

## 6. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| Khan Academy | Probability & Statistics | https://www.khanacademy.org/math/statistics-probability |
| Brilliant.org | Bayesian Inference | https://brilliant.org/courses/probability/ |
| Coursera | Probabilistic Graphical Models | https://www.coursera.org/learn/probabilistic-graphical-models |

### Soal Latihan Mandiri

**Soal 1: Diagnosis Medis (⭐⭐)**

Sebuah sistem diagnosis penyakit memiliki data berikut:
- P(Penyakit X) = 0.01 (1% populasi memiliki penyakit X)
- P(Test Positif | Penyakit X) = 0.95 (tes 95% sensitif)
- P(Test Positif | Tidak Penyakit X) = 0.05 (false positive 5%)

Jika seseorang test positif, berapa probabilitas dia benar-benar memiliki penyakit X?

---

**Soal 2: Deteksi Intrusi Cyber (⭐⭐⭐)**

Sistem cyber defense TNI memiliki statistik:
- P(Serangan) = 0.02
- P(Alert | Serangan) = 0.98
- P(Alert | Tidak Serangan) = 0.10

a) Hitung P(Serangan | Alert)  
b) Interpretasikan hasilnya untuk kebijakan respons  
c) Berapa threshold optimal untuk raise full alert?

---

**Soal 3: Naive Bayes Text Classification (⭐⭐⭐)**

Data training email militer:

| Kata | Spam (50 email) | Legitimate (50 email) |
|------|:-----:|:-----:|
| "urgent" | 30 | 5 |
| "classified" | 5 | 40 |
| "click" | 35 | 2 |

Email baru: "urgent classified"

a) Hitung P(Spam | "urgent classified")  
b) Hitung P(Legitimate | "urgent classified")  
c) Klasifikasikan email tersebut!

---

**Soal 4: Multi-Sensor Fusion (⭐⭐⭐)**

Sistem pertahanan mengintegrasikan 3 sensor independen:
- Radar: P(Deteksi | Target) = 0.90, false alarm rate = 0.10
- Infrared: P(Deteksi | Target) = 0.85, false alarm rate = 0.10
- Acoustic: P(Deteksi | Target) = 0.70, false alarm rate = 0.10

Jika ketiga sensor mendeteksi, hitung probabilitas benar-benar ada target! (Prior: P(Target) = 0.05)

---

**Soal 5: Bayesian Update Sequential (⭐⭐⭐)**

Prior: P(Musuh) = 0.10

Observation 1: Deteksi signature → P(Signature | Musuh) = 0.80, P(Signature | Bukan Musuh) = 0.20

Observation 2: Movement pattern → P(Pattern | Musuh) = 0.70, P(Pattern | Bukan Musuh) = 0.30

a) Hitung posterior setelah observation 1  
b) Gunakan posterior dari (a) sebagai prior baru untuk observation 2  
c) Hitung final posterior setelah kedua observasi

---

## 7. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. **Konsep Sulit:**
   - Apa aspek Teorema Bayes yang paling sulit dipahami? Mengapa?
   - Bagaimana Anda bisa mem-visualisasikan konsep posterior probability?

2. **Aplikasi Pertahanan:**
   - Berikan 3 contoh sistem pertahanan Indonesia yang dapat di-improve dengan penalaran probabilistik
   - Bagaimana Naive Bayes dapat digunakan untuk klasifikasi ancaman cyber?

3. **Trade-off:**
   - Dalam sistem deteksi ancaman, jelaskan trade-off antara false positive dan false negative
   - Threshold probability berapa yang Anda anggap appropriate untuk sistem early warning?

4. **Keterbatasan:**
   - Apa keterbatasan asumsi independensi dalam Naive Bayes?
   - Kapan Naive Bayes mungkin tidak cocok untuk aplikasi tertentu?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/probabilitytheory, r/MachineLearning
- Stack Overflow: tag [bayesian], [naive-bayes]
- Discord: AI/ML Learning Community
- Cross Validated (Stack Exchange for statistics)

### Topik Diskusi

1. **Perbandingan Metode:** Kapan menggunakan Naive Bayes vs Decision Tree untuk klasifikasi?

2. **Real-world Challenge:** Bagaimana menangani data training yang tidak balanced (misal: 99% legitimate email, 1% spam)?

3. **Defense Application:** Desain sistem threat assessment berbasis Bayesian untuk C2 system TNI

4. **Ethical Consideration:** Implikasi menggunakan probabilitas dalam keputusan militer yang melibatkan nyawa manusia

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Ketidakpastian dalam AI selesai
- [ ] Section 2: Review Probabilitas Dasar selesai
- [ ] Section 3: Review Teorema Bayes selesai
- [ ] Section 4: Tools interaktif dieksplorasi
- [ ] Section 5: Review Independensi dan Naive Bayes selesai
- [ ] Section 6: Latihan soal dikerjakan (min. 3 soal)
- [ ] Section 7: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| Probability and Statistics | Khan Academy | https://www.khanacademy.org/math/statistics-probability |
| Bayesian Statistics | Coursera (Duke) | https://www.coursera.org/learn/bayesian-statistics |
| Probabilistic Graphical Models | Stanford (Coursera) | https://www.coursera.org/specializations/probabilistic-graphical-models |

### 📚 Buku & Artikel

- **Online Book:** "Think Bayes" by Allen B. Downey — http://greenteapress.com/wp/think-bayes/
- **Tutorial:** "An Intuitive Explanation of Bayes' Theorem" — https://arbital.com/p/bayes_rule/
- **Paper:** "Naive Bayes at Forty" — exploring the history and applications

### 🎥 Channel YouTube Rekomendasi

- **3Blue1Brown** — Visualisasi matematika yang indah
- **StatQuest** — Penjelasan statistik yang jelas dan engaging
- **Khan Academy** — Tutorial terstruktur probability
- **Computerphile** — AI dan CS concepts
- **Two Minute Papers** — Latest AI research

### 🛠️ Tools & Libraries

- **Python Libraries:**
  - `scipy.stats` — Statistical functions
  - `sklearn.naive_bayes` — Naive Bayes implementation
  - `pgmpy` — Probabilistic Graphical Models
  - `pymc3` — Bayesian statistical modeling

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

1. **Mengapa logika tidak cukup?**
   Logika proposisional hanya menangani nilai benar/salah yang pasti. Dalam dunia nyata, banyak situasi yang tidak pasti atau informasi tidak lengkap. Logika tidak memiliki mekanisme untuk menyatakan "mungkin 70% benar" — hanya TRUE atau FALSE.

2. **Laziness (pertahanan):** Aturan IFF (Identification Friend or Foe) tidak bisa mendaftar semua kemungkinan pola terbang, formasi, dan sinyal dari seluruh jenis pesawat militer dan sipil di dunia — terlalu banyak kombinasi.

3. **Ignorance (radar):** Kemampuan pesawat stealth musuh tidak diketahui secara pasti, propagasi sinyal radar terpengaruh cuaca dan terrain yang tidak terprediksi, serta musuh dapat menggunakan electronic countermeasures yang tidak diketahui.

4. **Solusi probabilitas:** Probabilitas memungkinkan kita menyatakan derajat kepercayaan numerik (0-1) alih-alih benar/salah. Kita dapat mengatakan "probabilitas ini pesawat musuh = 0.15 berdasarkan pola terbang" dan memperbarui estimasi ini ketika bukti baru muncul.

### Section 2

1. **Setidaknya satu false alarm:** $P(\text{min 1}) = 1 - P(\text{tidak ada}) = 1 - (0.95)^2 = 1 - 0.9025 = 0.0975$ atau 9.75%.

2. **P(Hujan|Awan) vs P(Awan|Hujan):** P(Awan|Hujan) biasanya LEBIH BESAR karena hujan hampir selalu disertai awan, tetapi awan tidak selalu menghasilkan hujan. Ini mengilustrasikan bahwa P(A|B) ≠ P(B|A).

3. **P(Alarm ∧ Serangan):** $P(A \wedge S) = P(A|S) \times P(S) = 0.90 \times 0.02 = 0.018$

4. **P(Musuh|Sinyal)** merepresentasikan probabilitas bahwa objek yang terdeteksi adalah musuh GIVEN sinyal tertentu teramati. Ini adalah posterior yang harus dihitung menggunakan Bayes, bukan disamakan dengan P(Sinyal|Musuh).

### Section 3

1. **Sensor kebakaran:**
$$P(\text{Keb}|\text{Alarm}) = \frac{0.98 \times 0.005}{0.98 \times 0.005 + 0.03 \times 0.995} = \frac{0.0049}{0.0049 + 0.02985} = \frac{0.0049}{0.03475} = 0.141$$
Probabilitas ≈ **14.1%**

2. **Bayesian updating (alarm kedua):**
   - Prior baru = 0.141
   - $P(\text{Keb}|\text{Alarm}_2) = \frac{0.98 \times 0.141}{0.98 \times 0.141 + 0.03 \times 0.859} = \frac{0.1382}{0.1382 + 0.02577} = \frac{0.1382}{0.1640} = 0.843$
   - Posterior setelah alarm kedua ≈ **84.3%**

3. **Base rate fallacy:** Operator yang hanya melihat "sensor 95% akurat" mungkin berasumsi 95% alarm adalah nyata, padahal karena serangan sangat jarang (prior rendah), sebagian besar alarm adalah false alarm. Ini menyebabkan: (a) overreaction yang membuang resource, atau (b) alert fatigue yang menyebabkan ancaman nyata diabaikan.

4. **Prior vs Likelihood dominance:** Prior dominan ketika prior sangat kuat dan bukti lemah (contoh: P(Meteor menghantam | bunyi keras) — prior meteorite sangat rendah). Likelihood dominan ketika bukti sangat kuat dan prior moderat (contoh: DNA match di forensik — likelihood ratio sangat tinggi).

### Section 5

1. **Setidaknya satu deteksi:** $P(\text{min 1}) = 1 - (1-0.80)^2 = 1 - 0.04 = 0.96$ atau 96%.

2. **Naive:** Asumsi bahwa fitur independen given kelas hampir tidak pernah benar. Contoh: "gratis" dan "diskon" sangat berkorelasi di email spam — keduanya sering muncul bersama. Naive Bayes menganggap keduanya sebagai bukti independen, sehingga meng-overcount evidence.

3. **Dampak korelasi:** Jika "rahasia" dan "koordinat" sering muncul bersama di email rahasia, Naive Bayes meng-overestimate probabilitas kelas "Rahasia" karena menghitung keduanya sebagai bukti independen. Meskipun demikian, ranking klasifikasi biasanya tetap benar.

4. **Laplace smoothing:** Menambahkan pseudocount untuk menghindari P = 0. Contoh: kata "torpedo" tidak pernah muncul di 50 email spam → tanpa smoothing: P("torpedo"|Spam) = 0/50 = 0, yang membuat seluruh produk = 0. Dengan Laplace (α=1): P("torpedo"|Spam) = (0+1)/(50+2) = 1/52 ≈ 0.019 — kecil tapi bukan nol.

### Section 6

**Soal 1:** $P(\text{Penyakit}|\text{Pos}) = \frac{0.95 \times 0.01}{0.95 \times 0.01 + 0.05 \times 0.99} = \frac{0.0095}{0.0095+0.0495} = \frac{0.0095}{0.0590} = 0.161$ atau **16.1%**

**Soal 2:**
a) $P(\text{Serangan}|\text{Alert}) = \frac{0.98 \times 0.02}{0.98 \times 0.02 + 0.10 \times 0.98} = \frac{0.0196}{0.0196+0.098} = \frac{0.0196}{0.1176} = 0.167$ atau **16.7%**
b) Hanya ~17% alert menunjukkan serangan nyata → perlu verifikasi sebelum full response, tetapi jangan abaikan!
c) Threshold tergantung cost ratio: jika cost miss >> cost false alarm, threshold rendah (~10%). Untuk cyber, karena serangan bisa sangat merusak, threshold 15-20% sudah cukup untuk eskalasi.

**Soal 3:**
- P(Spam) = P(Legit) = 0.5
- P("urgent"|Spam) = 30/50 = 0.60; P("urgent"|Legit) = 5/50 = 0.10
- P("classified"|Spam) = 5/50 = 0.10; P("classified"|Legit) = 40/50 = 0.80
- Score(Spam) = 0.5 × 0.60 × 0.10 = 0.030
- Score(Legit) = 0.5 × 0.10 × 0.80 = 0.040
- P(Spam|email) = 0.030 / (0.030 + 0.040) = 0.030/0.070 = **42.9%**
- P(Legit|email) = 0.040/0.070 = **57.1%**
- Klasifikasi: **Legitimate** — kata "classified" yang kuat mengarah ke legitimate mengalahkan "urgent" yang mengarah spam

**Soal 4:**
- Combined likelihood (target): 0.90 × 0.85 × 0.70 = 0.5355
- Combined false alarm: 0.10 × 0.10 × 0.10 = 0.001
- $P(\text{Target}|3 \text{ alarm}) = \frac{0.5355 \times 0.05}{0.5355 \times 0.05 + 0.001 \times 0.95} = \frac{0.02678}{0.02678 + 0.00095} = \frac{0.02678}{0.02773} = 0.966$ atau **96.6%**

**Soal 5:**
a) $P(\text{Musuh}|S_1) = \frac{0.80 \times 0.10}{0.80 \times 0.10 + 0.20 \times 0.90} = \frac{0.08}{0.08+0.18} = \frac{0.08}{0.26} = 0.308$ atau **30.8%**
b) Prior baru = 0.308, P(¬Musuh) = 0.692
c) $P(\text{Musuh}|S_1,S_2) = \frac{0.70 \times 0.308}{0.70 \times 0.308 + 0.30 \times 0.692} = \frac{0.2156}{0.2156+0.2076} = \frac{0.2156}{0.4232} = 0.510$ atau **51.0%**

Posterior meningkat dari 10% → 30.8% → 51.0% setelah dua bukti yang mendukung.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
