# Panduan Belajar Mandiri Pertemuan 01: Pengantar Kecerdasan Artifisial dan Agen Cerdas

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**Pertemuan:** 01  
**Topik:** Pengantar Kecerdasan Artifisial dan Agen Cerdas  
**Estimasi Waktu:** 495 menit (~8 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, Anda diharapkan mampu:

1. Mendefinisikan kecerdasan artifisial dari berbagai perspektif
2. Menjelaskan tonggak sejarah perkembangan AI
3. Membedakan empat pendekatan dalam AI
4. Menjelaskan konsep agen dan lingkungannya
5. Mengidentifikasi lima jenis agen cerdas dan enam karakteristik lingkungan

---

## 1. Review Konsep: Definisi dan Sejarah AI (45 menit)

### Ringkasan Materi

**Kecerdasan Artifisial (AI)** adalah cabang ilmu komputer yang bertujuan membuat sistem yang dapat melakukan tugas yang memerlukan kecerdasan manusia. Tidak ada definisi tunggal yang disepakati universal—berbagai definisi mencerminkan pendekatan berbeda dalam memahami dan mengembangkan sistem cerdas.

**Empat kemampuan utama yang ditiru AI:**
- **Penalaran (Reasoning):** Kemampuan menarik kesimpulan dari premis
- **Pembelajaran (Learning):** Kemampuan memperoleh pengetahuan dari pengalaman
- **Pemecahan Masalah (Problem Solving):** Kemampuan menemukan solusi
- **Pengambilan Keputusan (Decision Making):** Kemampuan memilih tindakan terbaik

**Timeline Sejarah AI:**

| Era | Periode | Karakteristik Utama |
|-----|---------|---------------------|
| Lahirnya AI | 1943-1956 | Model neuron, Turing Test, Dartmouth Conference |
| Keemasan Awal | 1956-1974 | Optimisme tinggi, GPS, ELIZA, LISP |
| AI Winter 1 | 1974-1980 | Keterbatasan hardware, kompleksitas kombinatorial |
| Expert Systems | 1980-1987 | MYCIN, DENDRAL, sistem berbasis aturan |
| AI Winter 2 | 1987-1993 | Biaya tinggi, keterbatasan expert systems |
| Modern AI | 1993-sekarang | Deep Blue, Watson, AlphaGo, LLMs |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | What is Artificial Intelligence? In 5 minutes | BBC Ideas | 5:00 | https://www.youtube.com/watch?v=2ePf9rue1Ao |
| 2 | AI vs Machine Learning vs Deep Learning | IBM Technology | 8:00 | https://www.youtube.com/watch?v=4RixMPF4xis |
| 3 | The History of Artificial Intelligence | ColdFusion | 15:00 | https://www.youtube.com/watch?v=056v4OxKwlI |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Turing Test Game | Human or Not? | Uji kemampuan membedakan AI dan manusia | https://www.humanornot.ai/ |
| Chatbot Experiment | Cleverbot | Bicara dengan chatbot dan evaluasi Turing Test | https://www.cleverbot.com/ |

### ✍️ Latihan Pemahaman


1. Sebutkan empat kemampuan utama yang ditiru AI!
2. Apa penyebab utama AI Winter pertama (1974-1980)?
3. Siapa yang mengusulkan Turing Test dan pada tahun berapa?

---

## 2. Review Konsep: Empat Pendekatan AI (45 menit)

### Ringkasan Materi

Russell dan Norvig mengidentifikasi empat pendekatan dalam AI berdasarkan dua dimensi: (1) berpikir vs bertindak, dan (2) mirip manusia vs rasional/ideal.

![Matriks Empat Pendekatan AI](images/ss01-01-four-approaches-matrix.png)

*Gambar 1.1: Matriks empat pendekatan dalam Kecerdasan Artifisial*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Matriks empat pendekatan AI dalam format grid 2x2
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
TATA LETAK: Grid 2x2 dengan pemisahan kuadran yang jelas
WARNA:
- Utama: #2563eb (biru) untuk elemen utama dan border
- Sekunder: #10b981 (hijau) untuk kuadran terkait manusia
- Aksen: #f59e0b (oranye) untuk kuadran terkait rasionalitas
- Netral: #6b7280 (abu-abu) untuk label
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Kuadran kiri atas: Ikon otak dengan gelembung pikiran, label "Berpikir seperti Manusia"
2. Kuadran kanan atas: Ikon logika/gear, label "Berpikir Rasional"
3. Kuadran kiri bawah: Siluet manusia dengan robot, label "Bertindak seperti Manusia"
4. Kuadran kanan bawah: Ikon target dengan centang, label "Bertindak Rasional" dengan highlight bintang
5. Header kolom: "Mirip Manusia" (kiri), "Ideal/Rasional" (kanan)
6. Header baris: "Berpikir" (atas), "Bertindak" (bawah)
LABEL: "Berpikir seperti Manusia", "Berpikir Rasional", "Bertindak seperti Manusia", "Bertindak Rasional"
UKURAN: 800x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik, tanpa tekstur kompleks
</prompt>

| Pendekatan | Fokus | Metode | Contoh |
|------------|-------|--------|--------|
| Berpikir seperti Manusia | Cara manusia berpikir | Cognitive science, neuroscience | Cognitive architecture (ACT-R) |
| Berpikir Rasional | Penalaran logis ideal | Logika formal, matematika | Theorem prover |
| Bertindak seperti Manusia | Perilaku mirip manusia | Turing Test | Chatbot, virtual assistant |
| **Bertindak Rasional** | Tindakan optimal | Utility maximization | AlphaGo, self-driving car |

> **Penting:** Pendekatan **Bertindak Rasional** (Rational Agent) adalah yang paling banyak diadopsi dalam AI modern karena fokus pada hasil optimal tanpa terbatas pada meniru cara berpikir manusia.

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | The Turing Test - Computerphile | Computerphile | 10:00 | https://www.youtube.com/watch?v=3wLqsRLvV-c |
| 2 | Chinese Room Argument - Computerphile | Computerphile | 12:00 | https://www.youtube.com/watch?v=D0MD4sRHj1M |

### ✍️ Latihan Pemahaman

1. Pendekatan AI mana yang paling banyak diadopsi dalam AI modern? Mengapa?
2. Apa perbedaan utama antara "Berpikir seperti Manusia" dan "Bertindak Rasional"?

---

## 3. Review Konsep: Agen Cerdas dan Lingkungan (45 menit)

### Ringkasan Materi

> **Agen** adalah entitas yang mempersepsi lingkungan melalui **sensor** dan bertindak melalui **aktuator**.

**Komponen Agen:**
- **Sensor:** Menerima input dari lingkungan (kamera, microphone, thermometer)
- **Aktuator:** Melakukan tindakan ke lingkungan (motor, speaker, display)
- **Agent Function:** Memetakan percept sequence ke action

![Siklus Interaksi Agen-Lingkungan](images/ss01-02-agent-environment-cycle.png)

*Gambar 1.2: Siklus interaksi agen dengan lingkungan*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram siklus interaksi agen-lingkungan dengan sensor dan aktuator
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
TATA LETAK: Susunan horizontal dengan loop umpan balik melingkar
WARNA:
- Utama: #2563eb (biru) untuk kotak agen
- Sekunder: #10b981 (hijau) untuk lingkungan
- Aksen: #f59e0b (oranye) untuk panah dan alur data
- Merah: #ef4444 untuk aktuator
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Kotak biru tengah: "AGEN" berisi "Agent Function"
2. Kotak hijau di kanan: "LINGKUNGAN"
3. Panah atas dari lingkungan ke agen: "Percept" dengan ikon sensor
4. Panah bawah dari agen ke lingkungan: "Action" dengan ikon aktuator
5. Label: "Sensor", "Aktuator"
LABEL: "Agen", "Lingkungan", "Percept", "Action", "Sensor", "Aktuator"
UKURAN: 800x500 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien, tanpa efek 3D, tanpa elemen fotorealistik
</prompt>

**Rational Agent vs Omniscient Agent:**
- **Rational Agent:** Memaksimalkan hasil yang diharapkan berdasarkan informasi yang tersedia
- **Omniscient Agent:** Mengetahui hasil aktual (tidak mungkin dalam kenyataan)

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Intelligent Agents in AI | Gate Smashers | 10:00 | https://www.youtube.com/watch?v=nDiCxqmDWHQ |
| 2 | Reinforcement Learning Intro | CrashCourse | 11:00 | https://www.youtube.com/watch?v=nIgIv4IfJ6s |

### ✍️ Latihan Pemahaman

1. Apa perbedaan antara Rational Agent dan Omniscient Agent?
2. Sebutkan contoh sensor dan aktuator pada robot vacuum cleaner!

---

## 4. Review Konsep: Lima Jenis Agen (45 menit)

### Ringkasan Materi

| Jenis Agen | Karakteristik | Contoh |
|------------|---------------|--------|
| **Simple Reflex** | Condition-action rules, tanpa memori | Thermostat |
| **Model-Based Reflex** | Memiliki internal state | Robot dengan memory |
| **Goal-Based** | Mempertimbangkan goal/tujuan | Navigation system |
| **Utility-Based** | Menggunakan utility function | Self-driving car |
| **Learning** | Dapat meningkatkan performa | Recommendation system |

![Lima Jenis Agen Cerdas](images/ss01-03-five-agent-types.png)

*Gambar 1.3: Hierarki lima jenis agen cerdas*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJEK: Diagram hierarki lima jenis agen cerdas dari Simple Reflex hingga Learning Agent
GAYA: Ilustrasi vektor datar yang bersih, diagram ilmu komputer edukatif, kualitas buku teks, desain minimal
TATA LETAK: Tangga naik dari kiri bawah ke kanan atas menunjukkan kompleksitas meningkat
WARNA:
- Level 1: #10b981 (hijau) untuk Simple Reflex
- Level 2: #3b82f6 (biru) untuk Model-Based
- Level 3: #f59e0b (oranye) untuk Goal-Based
- Level 4: #ef4444 (merah) untuk Utility-Based
- Level 5: #8b5cf6 (ungu) untuk Learning
- Latar belakang: #ffffff (putih)
ELEMEN:
1. Lima kotak bertingkat naik:
   - "Simple Reflex Agent" (hijau)
   - "Model-Based Reflex Agent" (biru)
   - "Goal-Based Agent" (oranye)
   - "Utility-Based Agent" (merah)
   - "Learning Agent" (ungu)
2. Panah menunjukkan "Kompleksitas Meningkat →"
3. Karakteristik kunci di samping setiap kotak
LABEL: Nama kelima jenis agen, "Kompleksitas Meningkat"
UKURAN: 900x600 piksel
FORMAT: PNG, latar belakang putih
NEGATIF: Tanpa gradien kompleks, tanpa efek 3D
</prompt>

**Kapan menggunakan jenis agen tertentu:**
- **Simple Reflex:** Lingkungan fully observable, sederhana
- **Model-Based:** Lingkungan partially observable
- **Goal-Based:** Perlu planning untuk mencapai tujuan
- **Utility-Based:** Perlu menyeimbangkan multiple objectives
- **Learning:** Perlu beradaptasi dari pengalaman

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | Types of Agents in AI | Gate Smashers | 15:00 | https://www.youtube.com/watch?v=WKMO8jC5OFQ |
| 2 | MarI/O - Machine Learning for Video Games | SethBling | 5:00 | https://www.youtube.com/watch?v=qv6UVOQ0F44 |

### ✍️ Latihan Pemahaman

1. Sistem rekomendasi Netflix yang belajar dari rating user termasuk jenis agen apa?
2. Kapan Model-Based Reflex Agent diperlukan dibanding Simple Reflex Agent?

---

## 5. Review Konsep: Karakteristik Lingkungan dan PEAS (45 menit)

### Ringkasan Materi

**Enam Karakteristik Lingkungan:**

| Karakteristik | Spektrum | Implikasi |
|---------------|----------|-----------|
| Observable | Fully ↔ Partially | Partial → perlu internal state |
| Deterministic | Deterministic ↔ Stochastic | Stochastic → perlu probabilistic reasoning |
| Episode | Episodic ↔ Sequential | Sequential → perlu planning |
| Static | Static ↔ Dynamic | Dynamic → perlu real-time decision |
| Discrete | Discrete ↔ Continuous | Continuous → perlu discretization |
| Agents | Single ↔ Multi | Multi → perlu game theory |

**Kerangka PEAS:**

| Komponen | Pertanyaan Kunci |
|----------|------------------|
| **P**erformance | Bagaimana mengukur kesuksesan agen? |
| **E**nvironment | Apa saja yang ada di lingkungan? |
| **A**ctuators | Apa yang dapat dilakukan agen? |
| **S**ensors | Apa yang dapat dipersepsi agen? |

### 🎬 Video Pembelajaran

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | PEAS in AI | Gate Smashers | 12:00 | https://www.youtube.com/watch?v=WKMO8jC5OFQ |
| 2 | Task Environment Properties | AI Course | 10:00 | https://www.youtube.com/watch?v=nDiCxqmDWHQ |

### 🔗 Aktivitas Interaktif Online

| Aktivitas | Platform | Deskripsi | Link |
|-----------|----------|-----------|------|
| Chess vs AI | Chess.com | Analisis lingkungan game catur | https://www.chess.com/play/computer |
| 2048 Game | Play2048 | Analisis karakteristik lingkungan | https://play2048.co/ |

### ✍️ Latihan Pemahaman

1. Permainan catur memiliki karakteristik lingkungan seperti apa? (semua 6 dimensi)
2. Buat analisis PEAS untuk sistem autopilot pesawat!

---

## 6. Eksplorasi Tools dan Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| Tool | Deskripsi | Link |
|------|-----------|------|
| Teachable Machine | Buat ML model tanpa coding | https://teachablemachine.withgoogle.com/ |
| Quick, Draw! | Neural network menebak gambar | https://quickdraw.withgoogle.com/ |
| AI Experiments | Koleksi demo AI Google | https://experiments.withgoogle.com/collection/ai |
| Neural Network Playground | TensorFlow visual | https://playground.tensorflow.org/ |

### Tugas Eksplorasi

1. Buka **Teachable Machine** dan buat model klasifikasi gambar sederhana (misalnya: gestur tangan)
2. Screenshot hasil dan catat observasi Anda tentang bagaimana sistem "belajar"
3. Coba **Quick, Draw!** dan perhatikan bagaimana AI menebak gambar Anda
4. Refleksikan: Jenis agen apa yang digunakan dalam aplikasi ini?

---

## 7. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Playlist/Series

| No | Judul | Channel | Durasi | Link |
|----|-------|---------|--------|------|
| 1 | How AlphaGo Mastered the Game of Go | DeepMind | 5:00 | https://www.youtube.com/watch?v=WXuK6gekU1Y |
| 2 | Neural Networks Intro | 3Blue1Brown | 19:00 | https://www.youtube.com/watch?v=aircAruvnKk |
| 3 | Multi-Agent Hide & Seek | OpenAI | 4:00 | https://www.youtube.com/watch?v=kopoLzvh5jY |
| 4 | Boston Dynamics Robots | Boston Dynamics | 4:00 | https://www.youtube.com/watch?v=fn3KWM1kuAw |

### 📖 Bacaan Tambahan

- Russell & Norvig, Chapter 1-2 (Artificial Intelligence: A Modern Approach)
- Artikel: "Computing Machinery and Intelligence" by Alan Turing (1950)

---

## 8. Latihan Soal Online (90 menit)

### Platform Latihan

| Platform | Topik | Link |
|----------|-------|------|
| CS188 Practice | AI Concepts | https://inst.eecs.berkeley.edu/~cs188/ |
| Stanford CS221 | AI Fundamentals | https://stanford-cs221.github.io/ |

### Soal Latihan Mandiri

**Soal 1:** Sebuah drone pengintai TNI AU harus: (1) mendeteksi objek mencurigakan, (2) melacak pergerakan target, (3) menghindari obstacle. Tentukan jenis agen minimum yang diperlukan dan jelaskan alasannya!

**Soal 2:** Buat analisis PEAS lengkap untuk sistem pertahanan udara radar yang harus mendeteksi dan mengklasifikasikan objek terbang!

**Soal 3:** Jelaskan mengapa game Poker termasuk lingkungan "partially observable" sedangkan catur termasuk "fully observable"!

**Soal 4:** Rancang utility function untuk robot pengantar obat di rumah sakit yang harus menyeimbangkan: kecepatan pengantaran, keamanan pasien, dan efisiensi baterai!

**Soal 5:** Bandingkan karakteristik lingkungan untuk: (a) Sistem rekomendasi Netflix, (b) Self-driving car, (c) Chatbot customer service!

---

## 9. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

1. Apa konsep yang paling sulit dipahami dari materi Pertemuan 01? Mengapa?
2. Bagaimana konsep agen cerdas dapat diterapkan dalam konteks pertahanan Indonesia?
3. Menurut Anda, pendekatan AI mana yang akan dominan di masa depan? Mengapa?

### 💬 Forum Diskusi Online

Diskusikan dengan teman atau di forum:
- Reddit: r/artificial, r/learnmachinelearning
- Stack Overflow: tag [artificial-intelligence]
- Discord: AI/ML community servers

### Topik Diskusi

- Apakah AI akan menggantikan pekerjaan manusia?
- Bagaimana memastikan AI tetap "rasional" dan aman?
- Aplikasi AI apa yang paling bermanfaat untuk pertahanan Indonesia?

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Definisi dan Sejarah AI selesai
- [ ] Section 2: Review Empat Pendekatan AI selesai
- [ ] Section 3: Review Agen Cerdas dan Lingkungan selesai
- [ ] Section 4: Review Lima Jenis Agen selesai
- [ ] Section 5: Review Karakteristik Lingkungan dan PEAS selesai
- [ ] Section 6: Tools interaktif dieksplorasi
- [ ] Section 7: Video lanjutan ditonton
- [ ] Section 8: Latihan soal dikerjakan (min. 5 soal)
- [ ] Section 9: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| CS188: Introduction to AI | Berkeley (edX) | https://inst.eecs.berkeley.edu/~cs188/ |
| AI For Everyone | Coursera | https://www.coursera.org/learn/ai-for-everyone |
| Elements of AI | University of Helsinki | https://www.elementsofai.com/ |

### 📚 Buku & Artikel

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Chapter 1-2.
- Turing, A. (1950). "Computing Machinery and Intelligence"

### 🎥 Channel YouTube Rekomendasi

- **3Blue1Brown** - Visualisasi matematika dan neural networks
- **Computerphile** - Konsep computer science
- **Two Minute Papers** - AI research updates
- **Sentdex** - Python & ML tutorials

---

## Kunci Jawaban Latihan Pemahaman

### Section 1
1. Empat kemampuan utama: Penalaran, Pembelajaran, Pemecahan Masalah, Pengambilan Keputusan (RLPD)
2. Penyebab AI Winter 1: Keterbatasan hardware, kompleksitas kombinatorial, ekspektasi tidak realistis
3. Alan Turing mengusulkan Turing Test pada tahun 1950

### Section 2
1. Bertindak Rasional (Rational Agent) paling dominan karena fokus pada hasil optimal tanpa terbatas meniru manusia
2. "Berpikir seperti Manusia" fokus pada proses kognitif, "Bertindak Rasional" fokus pada hasil/tindakan optimal

### Section 3
1. Rational Agent memaksimalkan hasil berdasarkan informasi tersedia; Omniscient Agent mengetahui hasil aktual (tidak mungkin)
2. Robot vacuum: Sensor = kamera, sensor debu, bumper; Aktuator = motor roda, motor penyedot

### Section 4
1. Netflix recommendation system = Learning Agent (belajar dari rating dan perilaku user)
2. Model-Based diperlukan ketika lingkungan partially observable (perlu menyimpan informasi yang tidak terlihat)

### Section 5
1. Catur: Fully Observable, Deterministic, Sequential, Static, Discrete, Multi-Agent (Competitive)
2. Contoh PEAS Autopilot: P=keselamatan, efisiensi; E=udara, cuaca, pesawat lain; A=kontrol terbang; S=radar, GPS, altimeter

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
