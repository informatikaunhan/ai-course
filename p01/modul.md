# Modul 01: Pengantar Kecerdasan Artifisial dan Agen Cerdas

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 01  
**Topik:** Pengantar Kecerdasan Artifisial dan Agen Cerdas  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan definisi kecerdasan artifisial dari berbagai perspektif
2. Menguraikan sejarah perkembangan AI dari era Turing hingga era modern
3. Membedakan empat pendekatan dalam AI: thinking humanly, thinking rationally, acting humanly, dan acting rationally
4. Menjelaskan konsep agen cerdas dan interaksinya dengan lingkungan
5. Mengidentifikasi dan mengklasifikasikan lima jenis agen cerdas
6. Menganalisis karakteristik lingkungan tugas berdasarkan enam dimensi
7. Menerapkan kerangka PEAS untuk menganalisis sistem AI nyata

---

## 1. Pendahuluan Kecerdasan Artifisial

### 1.1 Definisi Kecerdasan Artifisial

> **Kecerdasan Artifisial (Artificial Intelligence/AI)** adalah cabang ilmu komputer yang berfokus pada pembuatan sistem yang dapat melakukan tugas-tugas yang biasanya memerlukan kecerdasan manusia, seperti penalaran, pembelajaran, pemecahan masalah, dan pengambilan keputusan.

Tidak ada definisi tunggal yang disepakati secara universal untuk AI. Berbagai definisi mencerminkan pendekatan yang berbeda dalam memahami dan mengembangkan sistem cerdas.

| Perspektif | Fokus | Contoh Definisi |
|------------|-------|-----------------|
| **Thinking Humanly** | Proses kognitif manusia | "Sistem yang berpikir seperti manusia" |
| **Thinking Rationally** | Penalaran logis | "Sistem yang berpikir secara rasional" |
| **Acting Humanly** | Perilaku mirip manusia | "Sistem yang berperilaku seperti manusia" |
| **Acting Rationally** | Tindakan optimal | "Sistem yang bertindak secara rasional" |

#### Solved Problem 1 ⭐

**Soal:** Jelaskan perbedaan antara "thinking humanly" dan "thinking rationally" dalam konteks AI!

**Penyelesaian:**

*Step 1:* Identifikasi fokus masing-masing pendekatan
- **Thinking Humanly**: Fokus pada bagaimana manusia berpikir secara aktual
- **Thinking Rationally**: Fokus pada penalaran yang ideal dan logis

*Step 2:* Analisis metode yang digunakan
- **Thinking Humanly**: Menggunakan cognitive science, psikologi, dan neuroscience untuk memahami proses berpikir manusia
- **Thinking Rationally**: Menggunakan logika formal dan matematika untuk mencapai kesimpulan yang benar

*Step 3:* Berikan contoh
- **Thinking Humanly**: Sistem yang mensimulasikan bias kognitif manusia dalam pengambilan keputusan
- **Thinking Rationally**: Sistem theorem prover yang membuktikan teorema matematika secara logis

**Jawaban:** Thinking humanly berusaha mereplikasi cara berpikir manusia yang aktual (termasuk keterbatasannya), sedangkan thinking rationally berusaha mencapai penalaran ideal berdasarkan logika formal tanpa mempertimbangkan bagaimana manusia sebenarnya berpikir.

---

### 1.2 Sejarah Perkembangan AI

Sejarah AI dapat dibagi menjadi beberapa era penting:

#### 1.2.1 Era Awal (1943-1956)

| Tahun | Tokoh/Event | Kontribusi |
|-------|-------------|------------|
| 1943 | McCulloch & Pitts | Model matematika neuron artifisial pertama |
| 1950 | Alan Turing | Turing Test - "Computing Machinery and Intelligence" |
| 1956 | Dartmouth Conference | Lahirnya istilah "Artificial Intelligence" |

> **Turing Test** adalah metode pengujian yang diusulkan oleh Alan Turing untuk menentukan apakah sebuah mesin dapat menunjukkan perilaku cerdas yang setara dengan manusia. Dalam tes ini, seorang penguji manusia melakukan percakapan dengan mesin dan manusia tanpa mengetahui mana yang mana.

#### 1.2.2 Era Keemasan Awal (1956-1974)

Periode ini ditandai dengan optimisme tinggi dan pencapaian awal:
- **General Problem Solver (GPS)** oleh Newell dan Simon
- **ELIZA** - program chatbot pertama oleh Joseph Weizenbaum
- Pengembangan bahasa pemrograman LISP oleh John McCarthy

#### 1.2.3 AI Winter Pertama (1974-1980)

Periode penurunan pendanaan dan minat karena:
- Keterbatasan komputasi
- Problem kompleksitas kombinatorial
- Kritik dari Lighthill Report

#### 1.2.4 Era Expert Systems (1980-1987)

> **Expert System** adalah program komputer yang mensimulasikan kemampuan pengambilan keputusan seorang ahli manusia dalam domain tertentu.

Contoh: MYCIN (diagnosis medis), DENDRAL (analisis molekul kimia)

#### 1.2.5 AI Winter Kedua (1987-1993)

Penurunan minat terhadap expert systems karena:
- Biaya pemeliharaan tinggi
- Keterbatasan dalam menangani ketidakpastian
- Kebangkrutan industri hardware AI khusus

#### 1.2.6 Era Modern (1993-sekarang)

| Periode | Perkembangan Utama |
|---------|-------------------|
| 1997 | Deep Blue mengalahkan Kasparov |
| 2011 | IBM Watson memenangkan Jeopardy! |
| 2012 | Deep Learning revolution (AlexNet) |
| 2016 | AlphaGo mengalahkan Lee Sedol |
| 2022-sekarang | Era Large Language Models (ChatGPT, dll.) |

#### Solved Problem 2 ⭐

**Soal:** Sebutkan dan jelaskan dua faktor yang menyebabkan AI Winter pertama!

**Penyelesaian:**

*Step 1:* Identifikasi periode AI Winter pertama (1974-1980)

*Step 2:* Analisis faktor-faktor penyebab:

**Faktor 1: Keterbatasan Komputasi**
- Hardware komputer pada masa itu tidak cukup kuat
- Memori dan kecepatan pemrosesan terbatas
- Banyak algoritma AI memerlukan resource yang tidak tersedia

**Faktor 2: Problem Kompleksitas Kombinatorial**
- Banyak masalah AI memiliki ruang pencarian yang eksponensial
- Teknik pencarian yang ada tidak efisien untuk masalah skala besar
- Contoh: permainan catur memiliki lebih dari 10^120 kemungkinan posisi

**Jawaban:** AI Winter pertama disebabkan oleh: (1) Keterbatasan hardware komputasi yang tidak mampu mendukung algoritma AI yang kompleks, dan (2) Problem kompleksitas kombinatorial di mana ruang pencarian untuk banyak masalah terlalu besar untuk dieksplorasi secara efisien.

---

### 1.3 Empat Pendekatan dalam AI

Russell dan Norvig mengidentifikasi empat pendekatan utama dalam mendefinisikan dan mengembangkan AI:

![Empat Pendekatan AI](images/p01-01-four-approaches-ai.png)

*Gambar 1.1: Empat pendekatan dalam Kecerdasan Artifisial*

#### 1.3.1 Thinking Humanly (Cognitive Modeling Approach)

Pendekatan ini berusaha membuat mesin yang berpikir seperti manusia:
- Memerlukan pemahaman tentang cara kerja pikiran manusia
- Menggunakan introspeksi, eksperimen psikologi, dan brain imaging
- Bidang terkait: Cognitive Science

#### 1.3.2 Thinking Rationally (Laws of Thought Approach)

Pendekatan berbasis logika formal:
- Menggunakan silogisme Aristoteles
- Notasi logika untuk merepresentasikan pengetahuan
- Tantangan: tidak semua pengetahuan dapat direpresentasikan dalam logika formal

#### 1.3.3 Acting Humanly (Turing Test Approach)

Fokus pada perilaku yang tidak dapat dibedakan dari manusia:
- Turing Test sebagai benchmark
- Memerlukan: Natural Language Processing, Knowledge Representation, Automated Reasoning, Machine Learning
- Total Turing Test menambahkan: Computer Vision, Robotics

#### 1.3.4 Acting Rationally (Rational Agent Approach)

> **Rational Agent** adalah agen yang bertindak untuk mencapai hasil terbaik atau, ketika ada ketidakpastian, hasil yang diharapkan terbaik.

Pendekatan ini paling banyak diadopsi dalam AI modern:
- Tidak terbatas pada penalaran logis saja
- Mencakup tindakan refleks yang tidak melibatkan inferensi
- Dapat menangani ketidakpastian dan informasi tidak lengkap

#### Solved Problem 3 ⭐⭐

**Soal:** Sebuah sistem autopilot pesawat tempur harus mengambil keputusan dalam hitungan milidetik untuk menghindari rudal. Pendekatan AI mana yang paling sesuai untuk sistem ini? Jelaskan alasannya!

**Penyelesaian:**

*Step 1:* Identifikasi karakteristik masalah
- Waktu sangat kritis (milidetik)
- Memerlukan tindakan optimal
- Kondisi ketidakpastian (posisi rudal, arah)
- Tidak ada waktu untuk "berpikir seperti manusia"

*Step 2:* Evaluasi setiap pendekatan

| Pendekatan | Kesesuaian | Alasan |
|------------|------------|--------|
| Thinking Humanly | ❌ Tidak sesuai | Pilot manusia tidak cukup cepat |
| Thinking Rationally | ❌ Tidak sesuai | Inferensi logika terlalu lambat |
| Acting Humanly | ❌ Tidak sesuai | Tidak perlu meniru perilaku manusia |
| Acting Rationally | ✅ Sesuai | Fokus pada tindakan optimal |

*Step 3:* Justifikasi pilihan

**Acting Rationally** adalah pendekatan paling sesuai karena:
1. Fokus pada **tindakan optimal** bukan proses berpikir
2. Dapat menggunakan **reactive decision-making** yang sangat cepat
3. Mempertimbangkan **ketidakpastian** dalam lokasi ancaman
4. Tidak memerlukan simulasi proses kognitif manusia

**Jawaban:** Pendekatan Acting Rationally (Rational Agent) paling sesuai karena sistem ini memerlukan tindakan optimal dalam waktu sangat singkat tanpa perlu mensimulasikan proses berpikir manusia atau mengikuti penalaran logis yang memakan waktu.

---

## 2. Konsep Agen Cerdas

### 2.1 Definisi Agen

> **Agen** adalah segala sesuatu yang dapat memandang/mempersepsi lingkungannya melalui **sensor** dan bertindak atas lingkungan tersebut melalui **aktuator**.

![Konsep Agen dan Lingkungan](images/p01-02-agent-environment-interaction.png)

*Gambar 1.2: Interaksi agen dengan lingkungan*

#### Komponen Agen:

| Komponen | Fungsi | Contoh pada Robot |
|----------|--------|-------------------|
| **Sensor** | Menerima input dari lingkungan | Kamera, LIDAR, microphone |
| **Aktuator** | Melakukan tindakan pada lingkungan | Motor, speaker, display |
| **Agent Function** | Memetakan percept ke action | Program kontrol |

#### Solved Problem 4 ⭐

**Soal:** Identifikasi sensor dan aktuator pada sebuah smart thermostat!

**Penyelesaian:**

*Step 1:* Identifikasi apa yang perlu dipersepsi (sensor)
- Suhu ruangan saat ini
- Keberadaan penghuni (occupancy)
- Waktu/jadwal
- Input pengguna

*Step 2:* Identifikasi tindakan yang dapat dilakukan (aktuator)
- Menyalakan/mematikan AC atau heater
- Menampilkan informasi pada layar
- Mengirim notifikasi

**Jawaban:**

| Sensor | Aktuator |
|--------|----------|
| Thermometer (suhu) | Relay untuk AC/heater |
| Motion sensor (keberadaan) | LCD display |
| Clock (waktu) | WiFi transmitter (notifikasi) |
| Touch screen (input) | Speaker (alarm) |

---

### 2.2 Percept dan Percept Sequence

> **Percept** adalah input yang diterima agen pada satu waktu tertentu.

> **Percept Sequence** adalah sejarah lengkap semua percept yang pernah diterima agen.

Secara matematis, **agent function** dapat ditulis sebagai:

$$f: P^* \rightarrow A$$

dimana:
- $P^*$ = himpunan semua percept sequence yang mungkin
- $A$ = himpunan semua tindakan yang mungkin

#### Agent Program vs Agent Function

| Aspek | Agent Function | Agent Program |
|-------|----------------|---------------|
| **Definisi** | Deskripsi matematis abstrak | Implementasi konkret |
| **Representasi** | Tabel mapping (bisa tak terhingga) | Kode program |
| **Ukuran** | Bisa sangat besar/tak terhingga | Terbatas oleh memori |

#### Solved Problem 5 ⭐

**Soal:** Sebuah robot vacuum memiliki sensor debu (binary: ada/tidak ada debu) dan sensor lokasi (2 lokasi: A dan B). Buat tabel agent function sederhana untuk robot ini!

**Penyelesaian:**

*Step 1:* Tentukan percept space
- Sensor debu: {Clean, Dirty}
- Sensor lokasi: {A, B}
- Total kombinasi: 2 × 2 = 4 percept

*Step 2:* Tentukan action space
- Actions: {Suck, MoveLeft, MoveRight}

*Step 3:* Buat tabel agent function

| Percept (Location, Status) | Action |
|---------------------------|--------|
| (A, Clean) | MoveRight |
| (A, Dirty) | Suck |
| (B, Clean) | MoveLeft |
| (B, Dirty) | Suck |

**Jawaban:** Tabel di atas menunjukkan agent function sederhana. Robot akan menghisap debu jika lokasi kotor, dan berpindah ke lokasi lain jika lokasi bersih.

---

### 2.3 Rasionalitas

> **Agen Rasional** adalah agen yang memilih tindakan yang diharapkan memaksimalkan **performance measure** berdasarkan percept sequence dan pengetahuan bawaan (built-in knowledge).

Rasionalitas bergantung pada empat hal:
1. **Performance measure** yang mendefinisikan kriteria sukses
2. **Prior knowledge** agen tentang lingkungan
3. **Actions** yang dapat dilakukan agen
4. **Percept sequence** hingga saat ini

> **Perbedaan Rasionalitas dan Omniscience:**
> - **Omniscient agent**: Mengetahui hasil aktual dari tindakannya (tidak mungkin)
> - **Rational agent**: Memaksimalkan hasil yang **diharapkan** berdasarkan informasi yang tersedia

#### Solved Problem 6 ⭐⭐

**Soal:** Seorang pilot UAV (drone pengintai) harus memutuskan apakah akan terbang rendah (untuk gambar lebih jelas) atau tinggi (untuk keamanan). Performance measure adalah kualitas intelijen × probabilitas bertahan. Jika terbang rendah menghasilkan kualitas 0.9 dengan survival 0.6, sedangkan terbang tinggi menghasilkan kualitas 0.5 dengan survival 0.95, manakah tindakan rasional?

**Penyelesaian:**

*Step 1:* Definisikan performance measure
- Performance = Kualitas × Probabilitas Survival

*Step 2:* Hitung expected performance untuk setiap tindakan

**Terbang Rendah:**
$$P_{low} = 0.9 \times 0.6 = 0.54$$

**Terbang Tinggi:**
$$P_{high} = 0.5 \times 0.95 = 0.475$$

*Step 3:* Bandingkan hasil

| Tindakan | Kualitas | Survival | Expected Performance |
|----------|----------|----------|---------------------|
| Terbang Rendah | 0.9 | 0.6 | **0.54** |
| Terbang Tinggi | 0.5 | 0.95 | 0.475 |

*Step 4:* Tentukan tindakan rasional

**Jawaban:** Tindakan rasional adalah **Terbang Rendah** karena expected performance (0.54) lebih tinggi daripada terbang tinggi (0.475).

---

## 3. Jenis-Jenis Agen Cerdas

### 3.1 Simple Reflex Agent

> **Simple Reflex Agent** adalah agen yang memilih tindakan berdasarkan **percept saat ini saja**, mengabaikan percept history.

![Simple Reflex Agent](images/p01-03-simple-reflex-agent.png)

*Gambar 1.3: Arsitektur Simple Reflex Agent*

**Karakteristik:**
- Menggunakan **condition-action rules** (if-then rules)
- Sangat sederhana dan cepat
- Tidak memiliki memori (stateless)
- Hanya bekerja jika lingkungan **fully observable**

**Pseudocode:**
```python
def simple_reflex_agent(percept):
    state = interpret_input(percept)
    rule = rule_match(state, rules)
    action = rule.action
    return action
```

**Contoh Aplikasi:**
- Thermostat sederhana (suhu > threshold → matikan heater)
- Sensor gerak untuk lampu otomatis

#### Solved Problem 7 ⭐

**Soal:** Buat condition-action rules untuk lampu otomatis berbasis sensor gerak!

**Penyelesaian:**

*Step 1:* Identifikasi kondisi yang dapat dipersepsi
- Motion detected (yes/no)
- Current light status (on/off)
- Ambient light level (bright/dark)

*Step 2:* Definisikan rules

```
Rule 1: IF motion_detected AND ambient_dark 
        THEN turn_light_on

Rule 2: IF NOT motion_detected AND light_on AND timer_expired 
        THEN turn_light_off

Rule 3: IF motion_detected AND light_on 
        THEN reset_timer

Rule 4: IF ambient_bright 
        THEN turn_light_off
```

**Jawaban:** Rules di atas mencakup skenario utama: menyalakan lampu saat ada gerakan dalam kondisi gelap, dan mematikan lampu setelah tidak ada gerakan dalam periode tertentu atau saat sudah terang.

---

### 3.2 Model-Based Reflex Agent

> **Model-Based Reflex Agent** adalah agen yang memelihara **internal state** untuk melacak aspek lingkungan yang tidak dapat diamati secara langsung.

![Model-Based Reflex Agent](images/p01-04-model-based-reflex-agent.png)

*Gambar 1.4: Arsitektur Model-Based Reflex Agent*

**Komponen tambahan:**
1. **Transition model**: Bagaimana state berubah berdasarkan aksi
2. **Sensor model**: Bagaimana percept berhubungan dengan state

**Pseudocode:**
```python
def model_based_reflex_agent(percept, state, action):
    state = update_state(state, action, percept, model)
    rule = rule_match(state, rules)
    action = rule.action
    return action
```

**Contoh Aplikasi:**
- Robot yang melacak posisi objek yang pernah dilihat
- Sistem navigasi yang mengingat jalur yang sudah dilalui

#### Solved Problem 8 ⭐⭐

**Soal:** Sebuah drone pengintai memiliki kamera yang hanya melihat 90° ke depan. Jelaskan mengapa simple reflex agent tidak cukup dan bagaimana model-based agent dapat membantu!

**Penyelesaian:**

*Step 1:* Identifikasi keterbatasan simple reflex agent
- Kamera hanya melihat 90° (tidak fully observable)
- Objek di belakang/samping tidak terdeteksi
- Simple reflex agent akan "lupa" objek yang baru saja dilihat

*Step 2:* Jelaskan kebutuhan internal state

Model-based agent dapat menyimpan:
- Posisi objek yang pernah terdeteksi
- Waktu terakhir objek terlihat
- Prediksi posisi objek berdasarkan pergerakan sebelumnya

*Step 3:* Ilustrasikan manfaat

| Skenario | Simple Reflex | Model-Based |
|----------|---------------|-------------|
| Target bergerak ke belakang drone | Kehilangan target | Memprediksi posisi target |
| Target tersembunyi di balik gedung | Menganggap target hilang | Mengingat lokasi terakhir |
| Multiple targets | Hanya track yang terlihat | Track semua, prioritaskan |

**Jawaban:** Simple reflex agent tidak cukup karena lingkungan drone hanya **partially observable** (kamera 90°). Model-based agent dapat memelihara **internal state** yang menyimpan informasi tentang objek yang pernah terdeteksi, memungkinkan drone untuk terus melacak target meskipun tidak terlihat dalam percept saat ini.

---

### 3.3 Goal-Based Agent

> **Goal-Based Agent** adalah agen yang mempertimbangkan **tujuan (goal)** dalam pengambilan keputusan, tidak hanya condition-action rules.

![Goal-Based Agent](images/p01-05-goal-based-agent.png)

*Gambar 1.5: Arsitektur Goal-Based Agent*

**Karakteristik:**
- Memiliki representasi **goal state** yang ingin dicapai
- Menggunakan **search** dan **planning** untuk mencapai goal
- Lebih fleksibel dari reflex agent
- Lebih mudah diubah perilakunya (ganti goal)

**Contoh:**
- Robot navigasi dengan tujuan mencapai lokasi tertentu
- Game playing agent yang bertujuan memenangkan permainan

**Catatan:** Algoritma pencarian (search) untuk goal-based agent akan dibahas secara mendalam pada **Pertemuan 2-4**.

#### Solved Problem 9 ⭐⭐

**Soal:** Bandingkan bagaimana model-based reflex agent dan goal-based agent akan berperilaku dalam skenario robot pengantar di rumah sakit!

**Penyelesaian:**

*Step 1:* Definisikan skenario
- Robot harus mengantarkan obat dari farmasi ke kamar pasien
- Terdapat koridor, lift, dan hambatan

*Step 2:* Analisis perilaku masing-masing agen

**Model-Based Reflex Agent:**
```
IF at_pharmacy AND has_medicine THEN move_toward_elevator
IF at_elevator AND destination_floor_different THEN enter_elevator
IF obstacle_ahead THEN turn_left
...
```
- Memerlukan banyak rules untuk setiap situasi
- Sulit menangani situasi baru
- Rules harus di-hardcode

**Goal-Based Agent:**
```
Goal: deliver_medicine_to_room(305)
State: current_location, medicine_status, hospital_map
Planning: search for path from pharmacy to room 305
```
- Secara otomatis menemukan jalur
- Dapat menangani situasi baru (jalur diblokir → cari jalur alternatif)
- Lebih fleksibel

*Step 3:* Ringkasan perbandingan

| Aspek | Model-Based Reflex | Goal-Based |
|-------|-------------------|------------|
| Jumlah rules | Banyak (setiap situasi) | Sedikit (goal + planning) |
| Fleksibilitas | Rendah | Tinggi |
| Penanganan hambatan baru | Perlu rules baru | Otomatis re-plan |
| Kompleksitas implementasi | Rules banyak | Planning algorithm |

**Jawaban:** Goal-based agent lebih unggul untuk robot pengantar karena dapat secara dinamis merencanakan jalur berdasarkan goal (tujuan pengantaran) tanpa memerlukan rules eksplisit untuk setiap situasi yang mungkin terjadi.

---

### 3.4 Utility-Based Agent

> **Utility-Based Agent** adalah agen yang menggunakan **utility function** untuk mengukur "seberapa baik" suatu state, memungkinkan perbandingan antara beberapa pilihan yang mencapai goal.

![Utility-Based Agent](images/p01-06-utility-based-agent.png)

*Gambar 1.6: Arsitektur Utility-Based Agent*

**Keunggulan dibanding Goal-Based:**
1. Dapat membandingkan **multiple goals** yang saling berkonflik
2. Dapat menangani **probabilitas keberhasilan**
3. Menghasilkan keputusan **optimal** bukan hanya feasible

> **Utility Function** adalah fungsi yang memetakan state ke bilangan real yang merepresentasikan tingkat kepuasan atau kebahagiaan agen pada state tersebut.

**Contoh:**
- Mobil self-driving yang mempertimbangkan kecepatan, keamanan, dan kenyamanan
- Sistem investasi yang menyeimbangkan return dan risiko

#### Solved Problem 10 ⭐⭐⭐

**Soal:** Sebuah drone militer harus memilih antara tiga target. Buatkan utility function dan tentukan target optimal!

| Target | Military Value | Distance | Enemy AA Coverage |
|--------|---------------|----------|-------------------|
| A | 80 | 10 km | 30% |
| B | 60 | 5 km | 10% |
| C | 100 | 15 km | 50% |

Asumsikan:
- Fuel penalty = 2 per km
- Survival probability = 1 - AA coverage

**Penyelesaian:**

*Step 1:* Definisikan utility function

$$U(target) = Military\_Value \times Survival\_Prob - Fuel\_Cost$$

dimana:
- $Survival\_Prob = 1 - AA\_Coverage$
- $Fuel\_Cost = Distance \times 2$

*Step 2:* Hitung utility untuk setiap target

**Target A:**
$$U(A) = 80 \times (1 - 0.30) - (10 \times 2)$$
$$U(A) = 80 \times 0.70 - 20 = 56 - 20 = 36$$

**Target B:**
$$U(B) = 60 \times (1 - 0.10) - (5 \times 2)$$
$$U(B) = 60 \times 0.90 - 10 = 54 - 10 = 44$$

**Target C:**
$$U(C) = 100 \times (1 - 0.50) - (15 \times 2)$$
$$U(C) = 100 \times 0.50 - 30 = 50 - 30 = 20$$

*Step 3:* Bandingkan dan pilih

| Target | Military Value | Survival | Fuel Cost | **Utility** |
|--------|---------------|----------|-----------|-------------|
| A | 80 | 0.70 | 20 | 36 |
| **B** | 60 | 0.90 | 10 | **44** |
| C | 100 | 0.50 | 30 | 20 |

**Jawaban:** Target optimal adalah **Target B** dengan utility tertinggi (44). Meskipun Target C memiliki military value tertinggi (100), kombinasi jarak jauh dan AA coverage tinggi membuatnya kurang optimal dibandingkan Target B.

---

### 3.5 Learning Agent

> **Learning Agent** adalah agen yang dapat meningkatkan kinerjanya berdasarkan pengalaman.

![Learning Agent](images/p01-07-learning-agent.png)

*Gambar 1.7: Arsitektur Learning Agent*

**Empat komponen Learning Agent:**

| Komponen | Fungsi |
|----------|--------|
| **Performance Element** | Memilih tindakan berdasarkan percept |
| **Learning Element** | Memperbaiki performance element |
| **Critic** | Mengevaluasi kinerja berdasarkan performance standard |
| **Problem Generator** | Menyarankan tindakan eksplorasi |

**Catatan:** Algoritma pembelajaran (machine learning) untuk learning agent akan dibahas lebih mendalam pada **Pertemuan 13-14**.

#### Solved Problem 11 ⭐⭐

**Soal:** Identifikasi keempat komponen learning agent pada sistem rekomendasi Netflix!

**Penyelesaian:**

*Step 1:* Identifikasi Performance Element
- Sistem yang merekomendasikan film kepada pengguna
- Menggunakan model rekomendasi (collaborative filtering, content-based)

*Step 2:* Identifikasi Learning Element
- Algoritma yang memperbarui model berdasarkan feedback
- Menyesuaikan weights dan parameters

*Step 3:* Identifikasi Critic
- Mengukur apakah rekomendasi diterima (diklik, ditonton)
- Performance metrics: click-through rate, watch time, ratings

*Step 4:* Identifikasi Problem Generator
- Sesekali merekomendasikan film di luar preferensi untuk eksplorasi
- A/B testing untuk mencoba strategi rekomendasi baru

**Jawaban:**

| Komponen | Implementasi di Netflix |
|----------|------------------------|
| **Performance Element** | Model rekomendasi yang memprediksi rating dan menghasilkan daftar film |
| **Learning Element** | ML training pipeline yang memperbarui model dari data baru |
| **Critic** | Sistem yang mengukur engagement (watch time, ratings, clicks) |
| **Problem Generator** | Exploration strategy yang menyarankan konten di luar comfort zone untuk mengumpulkan data baru |

---

### 3.6 Ringkasan Jenis-Jenis Agen

| Jenis Agen | Menggunakan State? | Menggunakan Goal? | Menggunakan Utility? | Belajar? |
|------------|:------------------:|:-----------------:|:--------------------:|:--------:|
| Simple Reflex | ❌ | ❌ | ❌ | ❌ |
| Model-Based Reflex | ✅ | ❌ | ❌ | ❌ |
| Goal-Based | ✅ | ✅ | ❌ | ❌ |
| Utility-Based | ✅ | ✅ | ✅ | ❌ |
| Learning | ✅ | ✅ | ✅ | ✅ |

#### Solved Problem 12 ⭐⭐⭐

**Soal:** Sebuah sistem pertahanan rudal harus: (1) mendeteksi ancaman, (2) melacak multiple targets, (3) memprioritaskan target berdasarkan tingkat bahaya, (4) belajar dari serangan sebelumnya. Tentukan jenis agen minimum yang diperlukan dan jelaskan!

**Penyelesaian:**

*Step 1:* Analisis setiap requirement

| Requirement | Kemampuan yang Diperlukan |
|-------------|---------------------------|
| (1) Deteksi ancaman | Sensor dan condition-action |
| (2) Track multiple targets | Internal state (model) |
| (3) Prioritaskan berdasarkan bahaya | Utility function |
| (4) Belajar dari serangan sebelumnya | Learning component |

*Step 2:* Tentukan jenis agen minimum untuk setiap requirement

1. **Deteksi ancaman**: Simple Reflex Agent cukup
2. **Track multiple targets**: Memerlukan Model-Based Agent
3. **Prioritaskan target**: Memerlukan Utility-Based Agent
4. **Belajar**: Memerlukan Learning Agent

*Step 3:* Tentukan jenis agen yang memenuhi semua requirement

Karena requirement (4) memerlukan kemampuan learning, dan learning agent mencakup semua kemampuan agen lainnya:

**Jawaban:** Sistem ini memerlukan **Learning Agent** sebagai minimum. Learning agent dapat:
- Memelihara state untuk melacak multiple targets
- Menggunakan utility function untuk memprioritaskan target
- Belajar dari serangan sebelumnya untuk meningkatkan deteksi dan response
- Komponen problem generator dapat mengeksplorasi strategi pertahanan baru

---

## 4. Karakteristik Lingkungan Tugas

### 4.1 Fully Observable vs Partially Observable

> **Fully Observable**: Agen dapat melihat seluruh state lingkungan pada setiap waktu.

> **Partially Observable**: Agen hanya dapat melihat sebagian dari state lingkungan.

| Karakteristik | Fully Observable | Partially Observable |
|---------------|------------------|---------------------|
| Sensor | Melihat semua state | Terbatas/noisy |
| Kebutuhan memori | Tidak perlu state | Perlu internal state |
| Kompleksitas | Lebih sederhana | Lebih kompleks |
| Contoh | Catur | Poker |

#### Solved Problem 13 ⭐

**Soal:** Klasifikasikan lingkungan berikut sebagai fully atau partially observable: (a) Permainan catur, (b) Mobil self-driving di jalan raya, (c) Permainan Poker!

**Penyelesaian:**

*Step 1:* Analisis observability masing-masing

**(a) Permainan Catur:**
- Semua posisi bidak terlihat di papan
- Tidak ada informasi tersembunyi
- **Fully Observable** ✅

**(b) Mobil Self-Driving:**
- Sensor tidak bisa melihat di balik gedung
- Niat driver lain tidak diketahui
- Kondisi jalan di depan mungkin tidak terdeteksi
- **Partially Observable** ⚠️

**(c) Permainan Poker:**
- Kartu lawan tersembunyi
- Kartu di deck tidak diketahui
- **Partially Observable** ⚠️

**Jawaban:** (a) Fully Observable, (b) Partially Observable, (c) Partially Observable

---

### 4.2 Deterministic vs Stochastic

> **Deterministic**: State berikutnya sepenuhnya ditentukan oleh state saat ini dan aksi agen.

> **Stochastic**: Ada elemen ketidakpastian dalam transisi state.

| Karakteristik | Deterministic | Stochastic |
|---------------|---------------|------------|
| Prediksi | Pasti | Probabilistik |
| Planning | Lebih mudah | Lebih kompleks |
| Contoh | Catur | Backgammon (ada dadu) |

> **Strategic**: Lingkungan deterministic kecuali untuk aksi agen lain (multi-agent).

#### Solved Problem 14 ⭐

**Soal:** Apakah lingkungan radar pertahanan udara bersifat deterministic atau stochastic? Jelaskan!

**Penyelesaian:**

*Step 1:* Identifikasi sumber ketidakpastian

1. **Noise pada sensor radar**: Deteksi tidak 100% akurat
2. **Pergerakan target**: Tidak bisa diprediksi dengan pasti
3. **Cuaca**: Mempengaruhi propagasi sinyal radar
4. **Electronic countermeasures**: Musuh dapat menggunakan jamming

*Step 2:* Evaluasi

Semua faktor di atas menunjukkan adanya ketidakpastian yang signifikan.

**Jawaban:** Lingkungan radar pertahanan udara bersifat **Stochastic** karena:
1. Sensor radar memiliki noise dan kemungkinan false positive/negative
2. Pergerakan objek (pesawat, rudal) memiliki elemen unpredictable
3. Faktor lingkungan (cuaca) mempengaruhi performa sensor secara tidak pasti
4. Adanya kemungkinan electronic warfare dari musuh menambah ketidakpastian

---

### 4.3 Episodic vs Sequential

> **Episodic**: Pengalaman agen terbagi dalam episode independen. Keputusan saat ini tidak mempengaruhi episode berikutnya.

> **Sequential**: Keputusan saat ini dapat mempengaruhi semua keputusan di masa depan.

| Karakteristik | Episodic | Sequential |
|---------------|----------|------------|
| Dependensi | Episode independen | Terhubung |
| Kompleksitas keputusan | Lebih sederhana | Lebih kompleks |
| Contoh | Klasifikasi gambar | Permainan catur |

#### Solved Problem 15 ⭐⭐

**Soal:** Sistem pengenal wajah untuk akses gedung militer bersifat episodic atau sequential? Bagaimana jika ditambahkan fitur tracking behavior?

**Penyelesaian:**

*Step 1:* Analisis sistem pengenal wajah dasar
- Setiap proses pengenalan independen
- Hasil pengenalan wajah A tidak mempengaruhi pengenalan wajah B
- **Episodic** ✅

*Step 2:* Analisis dengan fitur tracking behavior
- Sistem mencatat pola akses setiap individu
- Akses abnormal di masa lalu mempengaruhi keputusan saat ini
- Contoh: Jika seseorang sering akses di waktu tidak biasa, tingkatkan level verifikasi
- **Sequential** karena keputusan bergantung pada history

**Jawaban:**
- Sistem pengenal wajah dasar: **Episodic** - setiap pengenalan independen
- Dengan tracking behavior: **Sequential** - keputusan akses saat ini dipengaruhi oleh pola perilaku historis

---

### 4.4 Static vs Dynamic

> **Static**: Lingkungan tidak berubah saat agen sedang mempertimbangkan tindakan.

> **Dynamic**: Lingkungan dapat berubah saat agen sedang berpikir.

> **Semi-dynamic**: Lingkungan tidak berubah, tetapi skor/performance agen berubah seiring waktu.

| Karakteristik | Static | Dynamic |
|---------------|--------|---------|
| Waktu berpikir | Unlimited | Limited |
| Contoh | Crossword puzzle | Real-time strategy game |

#### Solved Problem 16 ⭐

**Soal:** Klasifikasikan: (a) Permainan catur dengan timer, (b) Analisis citra satelit, (c) Autonomous combat drone!

**Penyelesaian:**

**(a) Permainan catur dengan timer:**
- Papan tidak berubah saat pemain berpikir
- Tetapi waktu berkurang (performance affected)
- **Semi-dynamic**

**(b) Analisis citra satelit:**
- Gambar satelit statis (sudah diambil)
- Agen bisa menganalisis selama yang diperlukan
- **Static**

**(c) Autonomous combat drone:**
- Target dan ancaman bergerak
- Kondisi medan berubah
- Musuh merespons tindakan drone
- **Dynamic**

**Jawaban:** (a) Semi-dynamic, (b) Static, (c) Dynamic

---

### 4.5 Discrete vs Continuous

> **Discrete**: State, waktu, percept, dan action terbatas dan dapat dihitung.

> **Continuous**: State, waktu, percept, dan/atau action kontinu.

| Aspek | Discrete | Continuous |
|-------|----------|------------|
| State space | Terbatas | Tak terhingga |
| Action space | Terbatas | Tak terhingga |
| Contoh | Permainan papan | Robot navigasi |

#### Solved Problem 17 ⭐

**Soal:** Tentukan apakah sistem guidance system untuk torpedo bersifat discrete atau continuous dalam hal state dan action!

**Penyelesaian:**

*Step 1:* Analisis state
- Posisi torpedo: koordinat x, y, z (continuous)
- Kecepatan: magnitude dan arah (continuous)
- Posisi target: koordinat kontinu
- **State: Continuous**

*Step 2:* Analisis action
- Sudut kemudi: bisa diatur secara kontinu
- Kecepatan propulsi: bisa diatur secara kontinu
- **Action: Continuous**

**Jawaban:** Torpedo guidance system bersifat **Continuous** baik dalam state (posisi, kecepatan dalam ruang 3D kontinu) maupun action (sudut kemudi dan kecepatan yang dapat diatur secara kontinu).

---

### 4.6 Single Agent vs Multi-Agent

> **Single Agent**: Hanya ada satu agen di lingkungan.

> **Multi-Agent**: Terdapat beberapa agen yang berinteraksi.

Multi-agent dapat bersifat:
- **Competitive**: Utility satu agen berlawanan dengan yang lain (zero-sum)
- **Cooperative**: Agen bekerja sama untuk tujuan bersama
- **Mixed**: Kombinasi kompetitif dan kooperatif

#### Solved Problem 18 ⭐⭐

**Soal:** Sistem pertahanan udara melibatkan beberapa radar dan SAM (Surface-to-Air Missile). Analisis karakteristik multi-agent-nya!

**Penyelesaian:**

*Step 1:* Identifikasi agen
- Multiple radar stations
- Multiple SAM launchers
- Enemy aircraft (agen lawan)

*Step 2:* Analisis hubungan antar agen

**Radar dan SAM (Internal):**
- Bekerja sama (cooperative)
- Radar berbagi data untuk tracking
- SAM berbagi tanggung jawab target

**Sistem pertahanan vs Enemy aircraft:**
- Kompetitif (competitive/adversarial)
- Zero-sum: keberhasilan satu pihak = kegagalan pihak lain

*Step 3:* Ringkasan

**Jawaban:**
- **Intra-team (radar-radar, SAM-SAM, radar-SAM)**: **Cooperative multi-agent** - berbagi informasi dan koordinasi untuk efektivitas pertahanan
- **Inter-team (sistem pertahanan vs musuh)**: **Competitive multi-agent** - adversarial relationship dengan zero-sum outcome

---

### 4.7 Ringkasan Karakteristik Lingkungan

| Dimensi | Spektrum |
|---------|----------|
| Observability | Fully Observable ↔ Partially Observable |
| Determinism | Deterministic ↔ Stochastic |
| Episode | Episodic ↔ Sequential |
| Time | Static ↔ Dynamic |
| State/Action | Discrete ↔ Continuous |
| Agents | Single ↔ Multi-Agent |

![Dimensi Karakteristik Lingkungan](images/p01-08-environment-characteristics.png)

*Gambar 1.8: Enam dimensi karakteristik lingkungan tugas*

---

## 5. Kerangka PEAS

### 5.1 Definisi PEAS

> **PEAS** adalah kerangka untuk menspesifikasikan lingkungan tugas secara lengkap, terdiri dari:
> - **P**erformance measure
> - **E**nvironment
> - **A**ctuators
> - **S**ensors

| Komponen | Pertanyaan Kunci |
|----------|------------------|
| **Performance** | Bagaimana mengukur kesuksesan agen? |
| **Environment** | Apa saja yang ada di lingkungan? |
| **Actuators** | Apa yang dapat dilakukan agen? |
| **Sensors** | Apa yang dapat dipersepsi agen? |

### 5.2 Contoh Analisis PEAS

#### Contoh 1: Automated Taxi Driver

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Keselamatan, waktu tempuh, kepatuhan hukum, kenyamanan penumpang, minimalisasi bahan bakar |
| **Environment** | Jalan, lalu lintas, pejalan kaki, rambu, penumpang, cuaca |
| **Actuators** | Kemudi, akselerator, rem, klakson, display |
| **Sensors** | Kamera, LIDAR, GPS, speedometer, engine sensors |

#### Contoh 2: Medical Diagnosis System

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Akurasi diagnosis, minimalisasi biaya tes, waktu diagnosis |
| **Environment** | Pasien, rumah sakit, dokter, database medis |
| **Actuators** | Display (diagnosis, rekomendasi tes), printer (resep) |
| **Sensors** | Input keyboard (gejala), sensor medis, akses rekam medis |

#### Solved Problem 19 ⭐⭐

**Soal:** Buat analisis PEAS untuk sistem autopilot pesawat tempur!

**Penyelesaian:**

*Step 1:* Identifikasi Performance measures
- Keselamatan pilot dan pesawat
- Keberhasilan misi (target acquired/destroyed)
- Minimalisasi kerusakan collateral
- Efisiensi bahan bakar
- Manuver evasif yang berhasil

*Step 2:* Identifikasi Environment
- Ruang udara (altitude, weather)
- Pesawat musuh dan rudal
- Target darat
- Pesawat kawan
- Terrain
- Electronic warfare environment

*Step 3:* Identifikasi Actuators
- Flight control surfaces (aileron, elevator, rudder)
- Throttle
- Weapon systems (missile launch, gun fire)
- Countermeasures (chaff, flares)
- Communication systems

*Step 4:* Identifikasi Sensors
- Radar (air-to-air, ground)
- Infrared sensors (IRST)
- Radar Warning Receiver (RWR)
- GPS/INS
- Altimeter
- Airspeed indicators
- Missile approach warning system

**Jawaban:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Keselamatan, mission success rate, survival rate, fuel efficiency, precision |
| **Environment** | Airspace, enemy aircraft/missiles, targets, friendly forces, terrain, weather, EW environment |
| **Actuators** | Flight controls, throttle, weapons, countermeasures, communications |
| **Sensors** | Radar, IRST, RWR, GPS/INS, altimeter, airspeed, missile warning |

---

### 5.3 PEAS dan Karakteristik Lingkungan

Setelah mendefinisikan PEAS, kita dapat menganalisis karakteristik lingkungan:

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Berdasarkan PEAS autopilot pesawat tempur di atas, analisis keenam karakteristik lingkungannya!

**Penyelesaian:**

*Step 1:* Analisis setiap karakteristik

| Karakteristik | Nilai | Justifikasi |
|---------------|-------|-------------|
| **Observable** | Partially | Radar tidak bisa melihat semua (stealth, terrain masking) |
| **Deterministic** | Stochastic | Pergerakan musuh unpredictable, kondisi cuaca berubah |
| **Episode** | Sequential | Keputusan saat ini (posisi, bahan bakar) mempengaruhi opsi masa depan |
| **Static** | Dynamic | Situasi berubah terus-menerus saat sistem berpikir |
| **Discrete/Continuous** | Continuous | Posisi, kecepatan, arah dalam ruang kontinu |
| **Agents** | Multi-Agent | Pesawat kawan (cooperative), musuh (competitive) |

*Step 2:* Implikasi untuk desain agen

Karena lingkungan:
- Partially observable → Perlu internal state (model-based minimum)
- Stochastic → Perlu penalaran probabilistik
- Sequential → Perlu planning
- Dynamic → Perlu real-time decision making
- Continuous → Perlu discretization atau continuous control
- Multi-agent → Perlu game theory dan coordination

**Jawaban:** Lingkungan autopilot pesawat tempur adalah salah satu yang paling kompleks: **Partially Observable, Stochastic, Sequential, Dynamic, Continuous, Multi-Agent**. Ini memerlukan agen yang sangat sophisticated dengan kemampuan tracking state, penalaran probabilistik, planning real-time, dan koordinasi multi-agen.

---

### 5.4 Contoh PEAS dalam Konteks Pertahanan

#### Solved Problem 21 ⭐⭐

**Soal:** Buat analisis PEAS untuk Unmanned Ground Vehicle (UGV) untuk patroli perbatasan!

**Penyelesaian:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | - Area coverage (km² per jam)<br>- Detection rate (intrusions identified)<br>- False alarm rate<br>- Response time<br>- Operational endurance<br>- Stealth (tidak terdeteksi penyusup) |
| **Environment** | - Terrain (hutan, padang rumput, pegunungan)<br>- Cuaca (hujan, kabut, malam)<br>- Wildlife (hewan liar yang bisa trigger sensor)<br>- Penyusup (manusia, kendaraan)<br>- Pos jaga kawan<br>- Civilian areas |
| **Actuators** | - Motor penggerak (roda/track)<br>- Spotlight/infrared illuminator<br>- Communication system (alert to command)<br>- Loudspeaker (warning)<br>- Camera gimbal (arah kamera) |
| **Sensors** | - Cameras (visible, thermal, night vision)<br>- LIDAR untuk navigasi<br>- Motion sensors<br>- Acoustic sensors<br>- GPS<br>- Terrain sensors (incline, surface type) |

**Karakteristik lingkungan:**
- Partially Observable (area luas, sensor terbatas)
- Stochastic (pergerakan penyusup unpredictable)
- Sequential (rute patrol mempengaruhi future coverage)
- Dynamic (lingkungan berubah: cuaca, wildlife)
- Continuous (posisi, navigasi)
- Multi-agent (koordinasi dengan UGV lain, post jaga)

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Sebuah Command and Control (C2) system harus membantu komandan dalam pengambilan keputusan operasi militer. Buat analisis PEAS lengkap dan tentukan jenis agen yang paling sesuai!

**Penyelesaian:**

*Step 1:* Definisikan PEAS

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | - Mission success rate<br>- Minimalisasi casualties (friendly)<br>- Maksimalisasi combat effectiveness<br>- Resource efficiency (ammo, fuel, personnel)<br>- Kecepatan dan akurasi situational awareness<br>- Kualitas recommendation |
| **Environment** | - Friendly forces (locations, status, capabilities)<br>- Enemy forces (known and estimated)<br>- Terrain and weather<br>- Civilians<br>- Communication network<br>- Intelligence reports<br>- Rules of engagement |
| **Actuators** | - Display systems (map, status, recommendations)<br>- Alert systems<br>- Communication channels to units<br>- Report generation<br>- Simulation/war gaming output |
| **Sensors** | - ISR feeds (satellite, drone, HUMINT)<br>- Unit reports (voice, data)<br>- Intelligence database<br>- Weather data<br>- Logistics database<br>- Historical engagement data |

*Step 2:* Analisis karakteristik lingkungan

| Karakteristik | Nilai | Justifikasi |
|---------------|-------|-------------|
| Observable | Partially | "Fog of war" - banyak informasi tidak diketahui |
| Deterministic | Stochastic | Chaos dalam pertempuran |
| Episode | Sequential | Keputusan strategis mempengaruhi situasi jangka panjang |
| Static | Dynamic | Situasi berubah rapidly |
| Discrete/Continuous | Mixed | Posisi unit (continuous), status (discrete) |
| Agents | Multi-Agent | Friendly units (cooperative), enemy (competitive) |

*Step 3:* Tentukan jenis agen

Karena sistem harus:
1. Memelihara situational awareness → Model-based
2. Mencapai tujuan misi → Goal-based
3. Menyeimbangkan multiple objectives → Utility-based
4. Belajar dari operasi sebelumnya → Learning

**Jawaban:** C2 system memerlukan **Learning Agent** dengan:
- **Performance Element**: Menghasilkan recommendation berdasarkan situational picture
- **Learning Element**: Memperbaiki model prediksi musuh dan strategy dari historical data
- **Critic**: Membandingkan predicted outcomes dengan actual outcomes
- **Problem Generator**: Mengeksplorasi course of action alternatif melalui simulation

Arsitektur spesifik dapat menggabungkan:
- **Model-based component** untuk tracking situasi
- **Utility function** untuk menyeimbangkan objectives
- **Planning algorithm** untuk course of action generation
- **Machine learning** untuk pattern recognition dan prediction

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Sebutkan tiga contoh sistem AI yang menggunakan pendekatan "Acting Rationally" dan jelaskan mengapa pendekatan ini sesuai!

**Jawaban:** 
1. **Autonomous vehicle**: Memerlukan tindakan optimal real-time tanpa perlu meniru cara manusia berkendara
2. **Stock trading bot**: Fokus pada maksimalisasi profit, bukan meniru trader manusia
3. **Game AI (AlphaGo)**: Mencari langkah optimal, bahkan menemukan strategi yang tidak pernah digunakan manusia

---

### Problem S2 ⭐⭐
**Soal:** Jelaskan mengapa Deep Blue (yang mengalahkan Kasparov) bukan contoh sempurna dari "Thinking Humanly"!

**Jawaban:** Deep Blue menggunakan brute-force search dengan evaluasi jutaan posisi per detik, pendekatan yang sangat berbeda dari cara grandmaster manusia berpikir. Manusia menggunakan pattern recognition, intuisi, dan hanya mengevaluasi sedikit posisi yang "menarik". Deep Blue adalah contoh "Acting Rationally" (mencapai goal menang) bukan "Thinking Humanly".

---

### Problem S3 ⭐⭐
**Soal:** Dalam konteks sistem radar pertahanan udara, jelaskan perbedaan antara menggunakan goal-based agent vs utility-based agent untuk engagement decision!

**Jawaban:**
- **Goal-based**: Goal = "destroy all threats". Tidak membedakan prioritas, semua target sama pentingnya. Mungkin tidak optimal jika resources terbatas.
- **Utility-based**: Utility function mempertimbangkan: nilai strategis target, probabilitas hit, consumption of resources, collateral damage risk. Dapat memprioritaskan target berdasarkan trade-off berbagai faktor.

---

### Problem S4 ⭐⭐⭐
**Soal:** Rancang utility function untuk drone delivery yang harus menyeimbangkan: kecepatan pengantaran, efisiensi baterai, dan keselamatan (menghindari tabrakan). Berikan contoh perhitungan!

**Jawaban:**
Utility function:
$$U(delivery) = w_1 \cdot \frac{1}{time} + w_2 \cdot battery\_remaining + w_3 \cdot safety\_margin$$

Dengan weights: $w_1 = 0.3$, $w_2 = 0.2$, $w_3 = 0.5$

Contoh: Route A (time=10min, battery=60%, safety=0.9), Route B (time=15min, battery=80%, safety=0.7)
- $U(A) = 0.3(1/10) + 0.2(0.6) + 0.5(0.9) = 0.03 + 0.12 + 0.45 = 0.60$
- $U(B) = 0.3(1/15) + 0.2(0.8) + 0.5(0.7) = 0.02 + 0.16 + 0.35 = 0.53$

Route A optimal dengan utility lebih tinggi.

---

### Problem S5 ⭐⭐⭐
**Soal:** Buat analisis PEAS lengkap untuk AI assistant seperti ChatGPT dalam konteks membantu analis intelijen militer!

**Jawaban:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Akurasi informasi, relevansi jawaban, kecepatan respons, kepatuhan klasifikasi keamanan, kemampuan sintesis multi-source |
| **Environment** | Database intelijen, dokumen klasifikasi berbagai level, internet (OSINT), analis (user), regulasi keamanan informasi |
| **Actuators** | Text output, visualisasi data, alert generation, report generation, query ke database |
| **Sensors** | Text input (query analis), dokumen yang di-upload, database access, context dari percakapan sebelumnya |

Karakteristik: Partially Observable (tidak semua database terakses), Stochastic (query bervariasi), Sequential (context percakapan penting), Static (user menunggu respons), Discrete (text), Single Agent (satu AI assistant).

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Kecerdasan Artifisial** | Cabang ilmu komputer untuk membuat sistem yang menunjukkan kecerdasan |
| **Empat Pendekatan AI** | Thinking Humanly, Thinking Rationally, Acting Humanly, Acting Rationally |
| **Agen** | Entitas yang mempersepsi (sensor) dan bertindak (aktuator) pada lingkungan |
| **Rational Agent** | Agen yang memilih tindakan untuk memaksimalkan expected performance |
| **Simple Reflex Agent** | Agen dengan condition-action rules tanpa memori |
| **Model-Based Reflex Agent** | Agen yang memelihara internal state |
| **Goal-Based Agent** | Agen yang mempertimbangkan goal dalam pengambilan keputusan |
| **Utility-Based Agent** | Agen yang menggunakan utility function untuk membandingkan pilihan |
| **Learning Agent** | Agen yang dapat meningkatkan kinerja dari pengalaman |
| **PEAS** | Performance, Environment, Actuators, Sensors |
| **Karakteristik Lingkungan** | Observable, Deterministic, Episodic, Static, Discrete, Single/Multi-Agent |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. Chapter 1-2.
2. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press. Chapter 1.
3. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. Chapter 1.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
