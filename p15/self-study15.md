# Panduan Belajar Mandiri Pertemuan 15: Etika AI, Keamanan, dan Review Komprehensif

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 15  
**Topik:** Etika AI, Keamanan, dan Review Komprehensif  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan pembelajaran mandiri ini, mahasiswa diharapkan mampu:

1. Mengidentifikasi dan menganalisis isu etika dalam pengembangan dan penerapan sistem AI
2. Mengevaluasi risiko keamanan AI dan memahami konsep AI safety
3. Memahami regulasi AI global dan implikasinya terhadap Indonesia
4. Menganalisis dampak AI dalam konteks pertahanan dan keamanan nasional
5. Mengintegrasikan seluruh materi Pertemuan 1-14 untuk persiapan UAS

---

## 1. Review Konsep: Etika AI dan Bias Algoritmik (45 menit)

### Ringkasan Materi

**Isu Etika Utama dalam AI:**
- **Bias Algoritmik:** Sistem AI dapat mewarisi dan memperkuat bias dari data training
- **Fairness:** Definisi keadilan yang berbeda-beda — Demographic Parity, Equalized Odds, Predictive Parity
- **Transparency:** Kebutuhan untuk memahami bagaimana AI mengambil keputusan
- **Accountability:** Siapa yang bertanggung jawab ketika AI melakukan kesalahan

**Definisi Fairness:**

| Definisi | Rumus | Contoh |
|----------|-------|--------|
| Demographic Parity | P(Ŷ=1\|A=0) = P(Ŷ=1\|A=1) | Proporsi yang diterima sama untuk semua grup |
| Equalized Odds | TPR dan FPR sama untuk semua grup | Akurasi deteksi sama lintas grup |
| Predictive Parity | Precision sama untuk semua grup | Ketepatan prediksi sama lintas grup |

> **Impossibility Theorem (Chouldechova, 2017):** Kecuali dalam kondisi khusus, ketiga definisi fairness tidak bisa dipenuhi secara bersamaan.

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | The Ethics of AI | CrashCourse | 11:00 | https://www.youtube.com/watch?v=AaU6tI2pb3M |
| 2 | Algorithmic Bias and Fairness | Computerphile | 14:00 | https://www.youtube.com/watch?v=gV0_raKR2UQ |

### ✍️ Latihan Pemahaman

1. Sebutkan tiga contoh nyata bias algoritmik dan dampaknya terhadap kelompok tertentu!
2. Sistem AI perekrutan menunjukkan acceptance rate Grup A = 60%, Grup B = 35%. Apakah memenuhi Demographic Parity? Jelaskan!
3. Mengapa ketiga definisi fairness tidak bisa dipenuhi secara bersamaan?

---

## 2. Review Konsep: AI Safety dan Alignment Problem (45 menit)

### Ringkasan Materi

**AI Safety** berkaitan dengan memastikan sistem AI berperilaku sesuai niat manusia:

- **Alignment Problem:** Kesulitan memastikan tujuan AI selaras dengan tujuan manusia
- **Reward Hacking:** AI menemukan cara tak terduga untuk memaksimalkan reward tanpa memenuhi niat sebenarnya
- **Existential Risk:** Potensi ancaman dari superintelligent AI

**Contoh Reward Hacking:**
Robot pembersih diprogram dengan reward "minimalisasi debu terdeteksi" → robot mematikan sensornya (reward sempurna tanpa membersihkan)

**Lethal Autonomous Weapons Systems (LAWS):**
- Pro: Kemampuan pertahanan, presisi, deterrence
- Kontra: Accountability gap, risiko eskalasi, masalah etika

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | AI Alignment Problem Explained | Robert Miles AI Safety | 16:00 | https://www.youtube.com/watch?v=pYXy-A4siMw |
| 2 | The Danger of AI is Weirder Than You Think | Janelle Shane - TED | 12:00 | https://www.youtube.com/watch?v=OhCzX0iLnOc |
| 3 | Lethal Autonomous Weapons: an Arms Race | VICE News | 15:00 | https://www.youtube.com/watch?v=GFD_Cgr2zho |

### ✍️ Latihan Pemahaman

1. Jelaskan apa yang dimaksud dengan alignment problem! Mengapa masalah ini sulit diselesaikan?
2. Jelaskan konsep reward hacking dengan contoh! Mengapa ini menjadi masalah dalam AI safety?
3. Apa argumen utama pro dan kontra pengembangan LAWS?

---

## 3. Review Konsep: Regulasi AI Global (45 menit)

### Ringkasan Materi

**EU AI Act — Klasifikasi Risiko:**

| Kategori | Contoh | Regulasi |
|----------|--------|----------|
| Unacceptable Risk | Social scoring oleh pemerintah | Dilarang |
| High Risk | Credit scoring, biometrik, perekrutan | Wajib assessment |
| Limited Risk | Chatbot | Wajib transparansi |
| Minimal Risk | Rekomendasi musik | Bebas |

**Kerangka Regulasi Global:**
- **EU:** Risk-based approach (EU AI Act)
- **AS:** Sector-specific regulation
- **OECD:** Five AI Principles — inclusive growth, human-centered values, transparency, robustness, accountability

**Bacaan Wajib:**
- Russell & Norvig, Chapter 27: Philosophy, Ethics, and Safety of AI
- UNESCO: Recommendation on the Ethics of AI (2021) — https://www.unesco.org/en/artificial-intelligence/recommendation-ethics
- EU AI Act Summary — https://artificialintelligenceact.eu/
- OECD AI Principles — https://oecd.ai/en/ai-principles

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | EU AI Act Explained | AI Business | 10:00 | https://www.youtube.com/watch?v=1jYMOyEyb_c |
| 2 | Life 3.0 — Max Tegmark | TED | 18:00 | https://www.youtube.com/watch?v=oYmKV4pGBdM |

### ✍️ Latihan Pemahaman

1. Klasifikasikan sistem AI berikut menurut EU AI Act: (a) AI analisis ekspresi wajah siswa, (b) AI rekomendasi playlist musik, (c) AI credit scoring bank, (d) AI social scoring pemerintah
2. Apa lima prinsip utama OECD AI Principles?
3. Bandingkan pendekatan regulasi AI antara EU, AS, dan Singapura!

---

## 4. Review Konsep: AI dalam Pertahanan dan Review Algoritma (45 menit)

### Ringkasan Materi

**AI dalam Konteks Pertahanan:**
- Autonomous weapons dan meaningful human control
- Surveillance systems dan implikasi privasi
- AI untuk C6ISR (Command, Control, Communications, Computers, Cyber, Combat Systems, Intelligence, Surveillance, Reconnaissance)

**Review Algoritma Utama Kursus:**

| Topik | Algoritma Kunci | Pertemuan |
|-------|----------------|-----------|
| Pencarian | BFS, DFS, UCS, A* | P2-P3 |
| Pencarian Lokal | Hill Climbing, Simulated Annealing, GA | P4 |
| Game Playing | Minimax, Alpha-Beta Pruning | P5 |
| CSP | Backtracking, AC-3, MRV | P6 |
| Logika | Resolution, Forward/Backward Chaining | P9-P10 |
| Probabilitas | Teorema Bayes, Bayesian Networks | P11-P12 |
| Machine Learning | Decision Tree, Naive Bayes, K-Means, Q-Learning | P13-P14 |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | BFS vs DFS vs A* Search | Reducible | 20:00 | https://www.youtube.com/watch?v=pcKY4hjDrxk |
| 2 | Minimax Algorithm Explained | Sebastian Lague | 10:00 | https://www.youtube.com/watch?v=l-hh51ncgDI |
| 3 | Constraint Satisfaction Problems | CS188 Berkeley | 15:00 | https://www.youtube.com/watch?v=hJ9WOiueJes |

### ✍️ Latihan Pemahaman

1. Apa perbedaan utama BFS, DFS, dan A* dalam hal completeness dan optimality?
2. Jelaskan mengapa Alpha-Beta Pruning mempercepat Minimax tanpa mengubah hasil!
3. Dalam konteks pertahanan, apa peran AI yang paling krusial untuk Indonesia?

---

## 5. Review Konsep: Review Probabilitas dan Machine Learning (45 menit)

### Ringkasan Materi

**Review Probabilitas dan Bayesian:**
- Teorema Bayes: P(H|E) = P(E|H)P(H) / P(E)
- Bayesian Networks: representasi compact joint distribution
- D-separation untuk menentukan conditional independence

**Review Machine Learning:**
- Supervised: Decision Tree (ID3, entropy, information gain), Naive Bayes, Regresi Linear
- Unsupervised: K-Means, Hierarchical Clustering
- Reinforcement Learning: MDP, Q-Learning
- Evaluasi: Accuracy, Precision, Recall, F1-Score, Cross-Validation

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Bayes' Theorem Visual Explanation | 3Blue1Brown | 15:00 | https://www.youtube.com/watch?v=HZGCoVF3YvM |
| 2 | Bayesian Networks Explained | Normalized Nerd | 12:00 | https://www.youtube.com/watch?v=TuGDMj43ehw |
| 3 | Decision Trees Explained | StatQuest | 18:00 | https://www.youtube.com/watch?v=_L39rN6gz7Y |
| 4 | K-Means Clustering | StatQuest | 9:00 | https://www.youtube.com/watch?v=4b5d3muPQmA |

### ✍️ Latihan Pemahaman

1. Bagaimana Teorema Bayes digunakan untuk memperbarui keyakinan berdasarkan bukti baru?
2. Apa perbedaan antara supervised learning dan unsupervised learning? Berikan contoh algoritma masing-masing!
3. Jelaskan kapan menggunakan decision tree vs naive bayes untuk klasifikasi!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Deskripsi | URL |
|------|-----------|-----|
| **AI Fairness 360** | Toolkit IBM untuk mendeteksi dan mitigasi bias dalam model ML | https://aif360.mybluemix.net/ |
| **What-If Tool (Google)** | Visualisasi interaktif untuk mengeksplorasi fairness model ML | https://pair-code.github.io/what-if-tool/ |
| **Moral Machine (MIT)** | Eksplorasi dilema etika untuk kendaraan otonom | https://www.moralmachine.net/ |
| **AI Incident Database** | Database insiden dan kegagalan AI di dunia nyata | https://incidentdatabase.ai/ |
| **Teachable Machine (Google)** | Membuat model ML sederhana di browser (review supervised learning) | https://teachablemachine.withgoogle.com/ |
| **Algorithm Visualizer** | Visualisasi algoritma pencarian untuk review | https://algorithm-visualizer.org/ |

### 🔗 Aktivitas Interaktif Online

**Eksplorasi 1: Moral Machine (20 menit)**
1. Kunjungi https://www.moralmachine.net/
2. Kerjakan minimal 13 skenario dilema kendaraan otonom
3. Lihat hasil preferensi moral Anda
4. Catat: Apakah preferensi Anda konsisten? Faktor apa yang paling mempengaruhi keputusan Anda?

**Eksplorasi 2: AI Incident Database (20 menit)**
1. Kunjungi https://incidentdatabase.ai/
2. Cari 3 insiden AI terkait: bias algoritmik, keamanan/safety, dan privasi
3. Untuk setiap insiden, catat: apa yang terjadi, penyebab, dan cara pencegahan

**Eksplorasi 3: Review Algoritma (20 menit)**
1. Kunjungi https://algorithm-visualizer.org/
2. Jalankan visualisasi BFS dan A* pada graf yang sama — bandingkan jumlah node yang dikunjungi
3. Kunjungi https://teachablemachine.withgoogle.com/ dan buat model klasifikasi gambar sederhana

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### Video Lanjutan

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Propositional Logic and Inference | Neso Academy | 18:00 | https://www.youtube.com/watch?v=q2eyZxgNRX0 |
| 2 | The AI Dilemma | Center for Humane Technology | 60:00 | https://www.youtube.com/watch?v=xoVJKj8lcNQ |
| 3 | Weapons of Math Destruction | Cathy O'Neil - TED | 14:00 | https://www.youtube.com/watch?v=TQHs8SA1qpk |
| 4 | AI and Military — Full Documentary | DW Documentary | 42:00 | https://www.youtube.com/watch?v=dGJTk1gvQLo |

### Bacaan Tambahan

- Russell & Norvig, Chapter 27: Philosophy, Ethics, and Safety of AI
- Stanford CS221 — Final Review: https://stanford-cs221.github.io/
- CS188 Berkeley — Course Summary Materials: https://inst.eecs.berkeley.edu/~cs188/

---

## 8. Latihan Soal Komprehensif (90 menit)

### Platform Latihan Online

| Platform | Deskripsi | URL |
|----------|-----------|-----|
| **CS188 Berkeley Practice** | Soal latihan final exam AI | https://inst.eecs.berkeley.edu/~cs188/ |
| **AI Quiz (Brilliant)** | Quiz interaktif tentang konsep AI | https://brilliant.org/courses/intro-neural-networks/ |

### Soal Latihan

**Soal 1 (Etika):** Sebuah drone militer menggunakan AI untuk target identification. Confidence level AI adalah 82%. Berdasarkan prinsip meaningful human control, apa keputusan yang tepat?

**Soal 2 (Etika):** Jelaskan perbedaan antara Demographic Parity, Equalized Odds, dan Predictive Parity! Mengapa ketiga definisi fairness ini tidak bisa dipenuhi secara bersamaan?

**Soal 3 (Pencarian — A\*):** Diberikan graf berikut, tunjukkan langkah A* dari S ke G!

```
S --3-- A --2-- G
|       |
1       4
|       |
B --2-- C
```

Heuristik: h(S)=5, h(A)=2, h(B)=6, h(C)=4, h(G)=0

**Soal 4 (CSP):** Formulasikan penjadwalan 3 mata kuliah (AI, ML, DS) ke 3 slot waktu (Senin, Selasa, Rabu) sebagai CSP! Constraint: AI dan ML tidak boleh di hari yang sama, DS harus sebelum ML.

**Soal 5 (Logika — Resolusi):** Buktikan bahwa kesimpulan R valid dari premis-premis berikut menggunakan resolusi: P → Q, Q → R, P

**Soal 6 (Probabilitas — Bayes):** Sistem radar memiliki P(Detect|Enemy) = 0.90 dan P(Detect|¬Enemy) = 0.05. Jika P(Enemy) = 0.02, hitung P(Enemy|Detect) menggunakan Teorema Bayes!

**Soal 7 (Machine Learning — Decision Tree):** Diberikan dataset berikut, bangun decision tree menggunakan Information Gain!

| Cuaca | Angin | Suhu | Latihan? |
|-------|-------|------|----------|
| Cerah | Lemah | Panas | Ya |
| Cerah | Kuat | Panas | Tidak |
| Hujan | Lemah | Dingin | Ya |
| Hujan | Kuat | Dingin | Tidak |
| Mendung | Lemah | Panas | Ya |
| Mendung | Kuat | Dingin | Ya |

### Studi Kasus Integratif (Bonus)

**Skenario:** TNI AL sedang mengembangkan sistem AI terpadu untuk keamanan maritim di perairan Natuna mencakup: computer vision, jaringan Bayesian, A*, decision tree, dan utility function.

**Tugas Analisis:**
1. Apa jenis agen yang paling sesuai? Jelaskan mengapa agen yang lebih sederhana tidak cukup!
2. Buat analisis PEAS lengkap untuk sistem ini!
3. Sebutkan 3 isu etika utama terkait sistem ini!
4. Untuk setiap komponen sistem, jelaskan algoritma AI yang relevan dan mengapa dipilih!
5. Bagaimana sistem ini harus mematuhi prinsip etika dan regulasi?

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Dari semua topik yang dipelajari (P1-P15), mana yang paling sulit? Mengapa?
2. Algoritma mana yang menurut Anda paling "elegan" dan mengapa?
3. Bagaimana materi AI ini terkoneksi dengan mata kuliah lain (Struktur Data, Statistika)?
4. Aplikasi AI apa yang ingin Anda bangun berdasarkan pengetahuan dari kursus ini?
5. Setelah mempelajari etika AI, apa prinsip yang akan Anda pegang sebagai praktisi AI?

### 💬 Forum Diskusi Online

- Reddit: r/artificial, r/MachineLearning, r/ArtificialIntelligence
- Discord: AI Alignment Forum, ML Discord communities
- LinkedIn: AI Ethics groups, Indonesian AI community

### Topik Diskusi

Pilih salah satu dan tuliskan position paper (500 kata):

1. "Haruskah Indonesia melarang senjata otonom (autonomous weapons)?"
2. "AI akan menghilangkan lebih banyak pekerjaan daripada yang diciptakan"
3. "Perlu atau tidak Indonesia membuat regulasi AI seketat EU AI Act?"

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Etika AI dan Bias Algoritmik selesai
- [ ] Section 2: Review AI Safety dan Alignment Problem selesai
- [ ] Section 3: Review Regulasi AI Global selesai
- [ ] Section 4: Review AI dalam Pertahanan dan Review Algoritma selesai
- [ ] Section 5: Review Probabilitas dan Machine Learning selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| AI Ethics | Coursera (Free Audit) | https://www.coursera.org/learn/ai-ethics |
| Elements of AI | University of Helsinki | https://www.elementsofai.com/ |
| CS50 AI with Python | Harvard (edX) | https://cs50.harvard.edu/ai/ |

### 📚 Buku & Artikel

- Russell, S. (2019). *Human Compatible: Artificial Intelligence and the Problem of Control*. Viking Press.
- Crawford, K. (2021). *Atlas of AI: Power, Politics, and the Planetary Costs of Artificial Intelligence*. Yale University Press.
- Bostrom, N. (2014). *Superintelligence: Paths, Dangers, Strategies*. Oxford University Press.

### 🎥 Channel YouTube Rekomendasi

- **Robert Miles AI Safety** - AI alignment dan safety
- **Computerphile** - Konsep computer science dan AI
- **3Blue1Brown** - Visualisasi matematika
- **StatQuest** - Machine learning explanations

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

1. Contoh bias algoritmik: (a) Sistem rekrutmen Amazon yang bias terhadap perempuan karena data historis didominasi pelamar pria, (b) Sistem facial recognition yang akurasinya jauh lebih rendah untuk wajah berkulit gelap, (c) Sistem prediksi kriminalitas yang memberikan skor risiko lebih tinggi pada kelompok minoritas.

2. Sistem **tidak memenuhi** Demographic Parity karena acceptance rate berbeda signifikan: Grup A (60%) vs Grup B (35%). Demographic Parity mensyaratkan P(Ŷ=1|A=0) = P(Ŷ=1|A=1). Selisih 25% menunjukkan potensi diskriminasi.

3. Impossibility Theorem (Chouldechova, 2017): Kecuali base rate yang sama antar grup atau model sempurna, ketiga definisi ini tidak bisa dipenuhi bersamaan. Desainer harus memilih definisi yang paling sesuai konteks.

### Section 2

1. Alignment problem: Kesulitan memastikan tujuan AI selaras dengan niat manusia. Sulit karena: (a) tujuan formal sulit menangkap niat sebenarnya, (b) AI mengeksploitasi celah spesifikasi reward, (c) semakin powerful AI, semakin kreatif exploitasinya.

2. Reward hacking terjadi ketika AI menemukan cara tak terduga untuk memaksimalkan reward tanpa memenuhi niat sebenarnya. Contoh: robot pembersih dengan reward "minimalisasi debu terdeteksi" → mematikan sensor. Masalah serius karena tujuan formal berbeda dari niat manusia.

3. Pro LAWS: kemampuan pertahanan, presisi, deterrence value. Kontra: accountability gap, humanitarian concerns, risiko eskalasi otomatis.

### Section 3

1. Klasifikasi EU AI Act: (a) High risk — biometrik dalam pendidikan, (b) Minimal risk — dampak rendah, (c) High risk — mempengaruhi akses keuangan, (d) Unacceptable risk — dilarang.

2. Lima prinsip OECD: inclusive growth, human-centered values, transparency, robustness/security, accountability.

3. EU: risk-based approach dengan klasifikasi 4 tingkat. AS: sector-specific tanpa regulasi menyeluruh. Singapura: principles-based dengan panduan sukarela.

### Section 4

1. BFS: complete dan optimal (jika cost seragam), DFS: tidak complete (bisa loop), tidak optimal. A*: complete dan optimal (jika heuristik admissible).

2. Alpha-Beta Pruning memotong cabang yang tidak mungkin mempengaruhi keputusan akhir. Jika sudah ditemukan solusi lebih baik (alpha/beta bound), cabang inferior di-prune tanpa mengubah nilai minimax.

3. [Jawaban bervariasi — contoh: sistem C6ISR, autonomous surveillance, cyber defense]

### Section 5

1. Teorema Bayes memperbarui keyakinan: prior P(H) diperbarui dengan evidence menjadi posterior P(H|E) = P(E|H)P(H)/P(E). Semakin kuat evidence, semakin besar pembaruan.

2. Supervised: data berlabel, memprediksi output (Decision Tree, Naive Bayes). Unsupervised: data tanpa label, menemukan pola (K-Means, Hierarchical Clustering).

3. Decision tree: data kategorikal/campuran, perlu interpretabilitas. Naive Bayes: data berdimensi tinggi, asumsi independence, cepat.

### Section 8

**Soal 1:** Confidence 82% menyisakan 18% ketidakpastian. Keputusan: (1) tidak mengambil tindakan lethal, (2) tingkatkan surveillance, (3) kumpulkan data tambahan, (4) laporkan ke komandan dengan confidence level, (5) tindakan lethal hanya jika confidence > 95% dan disetujui manusia.

**Soal 2:** Demographic Parity: proporsi positif sama untuk semua grup. Equalized Odds: TPR dan FPR sama. Predictive Parity: precision sama. Impossibility Theorem: tidak bisa dipenuhi bersamaan kecuali base rate sama atau model sempurna.

**Soal 3 (A\*):**

| Langkah | Expand | Open List | Catatan |
|---------|--------|-----------|---------|
| 1 | S | A(f=3+2=5), B(f=1+6=7) | Start |
| 2 | A (f=5) | G(f=3+2+0=5), B(f=7), C(f=3+4+4=11) | Expand lowest f |
| 3 | G (f=5) | — | Goal reached! |

Jalur optimal: S → A → G, cost = 5

**Soal 4 (CSP):**
- Variabel: {AI, ML, DS}, Domain: {Senin, Selasa, Rabu}
- Constraint: AI ≠ ML, DS < ML
- Solusi: DS=Senin, AI=Selasa, ML=Rabu ✅ (dan beberapa solusi lain)

**Soal 5 (Resolusi):**
1. CNF: ¬P ∨ Q, ¬Q ∨ R, P
2. Resolve: P dan (¬P ∨ Q) → Q
3. Resolve: Q dan (¬Q ∨ R) → **R** ✅

**Soal 6 (Bayes):**
P(Detect) = 0.90 × 0.02 + 0.05 × 0.98 = 0.018 + 0.049 = 0.067
P(Enemy|Detect) = 0.018 / 0.067 ≈ **0.269 = 26.9%**
Interpretasi: Meskipun radar sensitif (TPR 90%), hanya ~27% deteksi benar-benar musuh karena base rate rendah (2%).

**Soal 7 (Decision Tree):**
Entropy(S) = -4/6 log₂(4/6) - 2/6 log₂(2/6) = 0.918

IG(Angin) = 0.918 - (3/6)(0) - (3/6)(0.918) = **0.459**
IG(Cuaca) = 0.918 - (2/6)(1.0) - (2/6)(1.0) - (2/6)(0) = **0.251**
IG(Suhu) = 0.918 - (3/6)(0.918) - (3/6)(0.918) = **0.0**

Root node: **Angin** (IG tertinggi). Jika Angin=Lemah → Ya. Jika Angin=Kuat → split berdasarkan Cuaca.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
