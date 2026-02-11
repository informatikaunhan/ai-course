# Modul 15: Etika AI, Keamanan, dan Review Komprehensif

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 15  
**Topik:** Etika AI, Keamanan, dan Review Komprehensif  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Mengidentifikasi isu etika utama dalam pengembangan sistem AI termasuk bias algoritmik, fairness, dan transparency
2. Menjelaskan konsep AI safety termasuk alignment problem dan existential risk
3. Menganalisis implikasi privasi dan surveillance dalam penerapan AI
4. Mengevaluasi penggunaan AI dalam konteks pertahanan termasuk autonomous weapons dan surveillance systems
5. Menjelaskan kerangka regulasi AI global dan nasional
6. Mendiskusikan masa depan AI termasuk AGI dan dampak sosial-ekonomi
7. Mengintegrasikan seluruh konsep dari Pertemuan 1-14 untuk persiapan UAS

---

## 1. Etika dalam Kecerdasan Artifisial

### 1.1 Mengapa Etika AI Penting?

> **Etika AI** adalah cabang etika terapan yang mempelajari implikasi moral dari desain, pengembangan, dan penggunaan sistem kecerdasan artifisial.

Seiring AI semakin berperan dalam pengambilan keputusan yang berdampak langsung pada kehidupan manusia, pertanyaan etika menjadi sangat kritis. Sistem AI kini digunakan untuk menentukan kelayakan kredit, diagnosis medis, keputusan peradilan, dan bahkan keputusan militer. Kesalahan atau bias dalam sistem ini dapat berdampak pada jutaan orang.

Terdapat beberapa alasan mengapa etika AI menjadi topik yang mendesak:

| Faktor | Penjelasan |
|--------|------------|
| **Skala dampak** | Satu model AI dapat mempengaruhi jutaan keputusan secara simultan |
| **Opaqueness** | Banyak model AI bersifat "black box" yang sulit dipahami prosesnya |
| **Otomatisasi keputusan** | Keputusan yang dulunya diambil manusia kini didelegasikan ke mesin |
| **Feedback loop** | Bias dalam data dapat diperkuat dan diperluas oleh sistem AI |
| **Irreversibilitas** | Beberapa keputusan AI sulit atau tidak mungkin dibatalkan |

#### Solved Problem 1 ⭐

**Soal:** Sebutkan tiga contoh nyata di mana keputusan AI berdampak langsung pada kehidupan manusia!

**Penyelesaian:**

*Step 1:* Identifikasi domain di mana AI digunakan untuk pengambilan keputusan kritis

*Step 2:* Berikan contoh spesifik

1. **Sistem kredit scoring**: Bank menggunakan model AI untuk menentukan apakah seseorang layak mendapat pinjaman. Keputusan ini mempengaruhi kemampuan seseorang membeli rumah atau memulai bisnis.

2. **Diagnosis medis**: Sistem AI seperti IBM Watson for Oncology digunakan untuk merekomendasikan pengobatan kanker. Rekomendasi yang salah dapat mengancam jiwa pasien.

3. **Sistem peradilan pidana**: COMPAS (Correctional Offender Management Profiling for Alternative Sanctions) digunakan di AS untuk memprediksi risiko residivisme. Skor tinggi dapat menyebabkan hukuman lebih berat.

**Jawaban:** Tiga contoh nyata adalah sistem kredit scoring (keputusan keuangan), diagnosis medis AI (keputusan kesehatan), dan sistem prediksi peradilan pidana (keputusan hukum). Ketiga contoh ini menunjukkan bahwa kesalahan AI dapat berdampak serius pada kehidupan individu.

---

### 1.2 Bias Algoritmik

> **Bias algoritmik** adalah kecenderungan sistematis dalam output suatu algoritma yang menghasilkan hasil yang tidak adil atau diskriminatif terhadap kelompok tertentu.

Bias dalam AI dapat berasal dari berbagai sumber:

| Sumber Bias | Penjelasan | Contoh |
|-------------|------------|--------|
| **Data historis** | Data training mencerminkan diskriminasi masa lalu | Data perekrutan yang didominasi pria |
| **Sampling bias** | Data tidak merepresentasikan seluruh populasi | Dataset wajah yang mayoritas kulit putih |
| **Label bias** | Pelabelan data dipengaruhi prasangka manusia | Annotator yang memiliki implicit bias |
| **Feature selection** | Fitur yang dipilih berkorelasi dengan atribut sensitif | Kode pos sebagai proxy untuk ras |
| **Confirmation bias** | Sistem memperkuat pola yang sudah ada | Filter bubble di media sosial |

![Sumber Bias dalam AI](images/p15-01-sources-of-bias-ai.png)

*Gambar 15.1: Sumber-sumber bias dalam siklus pengembangan sistem AI*

#### Solved Problem 2 ⭐

**Soal:** Jelaskan apa yang dimaksud dengan "proxy variable" dalam konteks bias algoritmik dan berikan contohnya!

**Penyelesaian:**

*Step 1:* Definisikan proxy variable
- **Proxy variable** adalah variabel yang secara tidak langsung merepresentasikan atribut sensitif (seperti ras, gender, agama) meskipun atribut tersebut tidak digunakan secara eksplisit.

*Step 2:* Berikan contoh konkret
- Meskipun model tidak menggunakan variabel "ras" secara langsung, penggunaan **kode pos** dapat menjadi proxy karena pola segregasi pemukiman
- Nama seseorang dapat menjadi proxy untuk gender atau etnisitas
- Riwayat pekerjaan dapat menjadi proxy untuk gender karena perbedaan historis partisipasi tenaga kerja

**Jawaban:** Proxy variable adalah variabel yang berkorelasi kuat dengan atribut sensitif sehingga dapat menyebabkan diskriminasi tidak langsung. Contoh: penggunaan kode pos dalam model kredit dapat menjadi proxy untuk ras karena pola segregasi pemukiman, sehingga meskipun ras tidak digunakan secara eksplisit, model tetap dapat mendiskriminasi kelompok tertentu.

---

#### Solved Problem 3 ⭐⭐

**Soal:** Sistem rekrutmen AI sebuah perusahaan teknologi besar dilatih menggunakan data historis perekrutan 10 tahun terakhir. Data menunjukkan 85% karyawan yang diterima adalah pria. Analisis potensi bias dan usulkan langkah mitigasi!

**Penyelesaian:**

*Step 1:* Identifikasi sumber bias
- **Data historis**: 85% pria mencerminkan bias perekrutan masa lalu, bukan kemampuan sebenarnya
- **Label bias**: Definisi "kandidat sukses" berdasarkan pola historis yang bias
- **Feature correlation**: Fitur seperti "bermain rugby" atau "lulusan universitas teknik X" mungkin berkorelasi dengan gender

*Step 2:* Analisis dampak
- Model akan cenderung memberikan skor rendah pada kandidat wanita
- Fitur yang berkorelasi dengan gender akan mendapat bobot tinggi
- Feedback loop: semakin sedikit wanita diterima → semakin sedikit data wanita sukses → model semakin bias

*Step 3:* Usulkan langkah mitigasi

| Langkah | Penjelasan |
|---------|------------|
| **Re-sampling** | Seimbangkan proporsi gender dalam data training |
| **Fairness constraints** | Tambahkan constraint: acceptance rate harus setara antar gender |
| **Feature audit** | Identifikasi dan hapus fitur yang menjadi proxy gender |
| **Adversarial debiasing** | Latih model kedua untuk mendeteksi bias, gunakan sebagai regularizer |
| **Human oversight** | Tambahkan review manusia untuk keputusan final |

**Jawaban:** Sistem ini berpotensi mendiskriminasi kandidat wanita karena data historis yang tidak seimbang. Mitigasi meliputi: re-sampling data, menambahkan fairness constraints, melakukan audit fitur untuk menghapus proxy gender, menggunakan teknik adversarial debiasing, dan mempertahankan human oversight dalam keputusan final.

---

### 1.3 Fairness (Keadilan)

> **Fairness dalam AI** mengacu pada prinsip bahwa sistem AI harus memperlakukan semua individu dan kelompok secara adil tanpa diskriminasi berdasarkan atribut sensitif.

Terdapat beberapa definisi formal fairness yang sering saling bertentangan:

| Definisi Fairness | Formula | Penjelasan |
|-------------------|---------|------------|
| **Demographic Parity** | P(Ŷ=1\|A=0) = P(Ŷ=1\|A=1) | Proporsi prediksi positif harus sama untuk semua grup |
| **Equalized Odds** | P(Ŷ=1\|Y=y, A=0) = P(Ŷ=1\|Y=y, A=1) | True positive rate dan false positive rate harus sama |
| **Predictive Parity** | P(Y=1\|Ŷ=1, A=0) = P(Y=1\|Ŷ=1, A=1) | Precision harus sama untuk semua grup |
| **Individual Fairness** | d(f(x), f(x')) ≤ D(x, x') | Individu serupa harus mendapat hasil serupa |

> **Impossibility Theorem (Chouldechova, 2017):** Kecuali dalam kondisi khusus, tidak mungkin memenuhi semua definisi fairness secara simultan. Desainer harus memilih definisi fairness yang paling sesuai dengan konteks.

#### Solved Problem 4 ⭐⭐

**Soal:** Sebuah sistem prediksi residivisme (pengulangan tindak kriminal) memiliki data berikut:

| Metrik | Grup A | Grup B |
|--------|--------|--------|
| False Positive Rate | 45% | 23% |
| False Negative Rate | 28% | 48% |
| Overall Accuracy | 65% | 65% |

Apakah sistem ini memenuhi kriteria Equalized Odds? Jelaskan implikasinya!

**Penyelesaian:**

*Step 1:* Pahami Equalized Odds
- Equalized Odds mensyaratkan: True Positive Rate (TPR) dan False Positive Rate (FPR) harus sama untuk semua grup
- FPR = False Positive Rate
- TPR = 1 - False Negative Rate (FNR)

*Step 2:* Hitung TPR dari data
- Grup A: TPR = 1 - 0.28 = 0.72
- Grup B: TPR = 1 - 0.48 = 0.52

*Step 3:* Evaluasi Equalized Odds

| Metrik | Grup A | Grup B | Selisih |
|--------|--------|--------|---------|
| FPR | 45% | 23% | 22% |
| TPR | 72% | 52% | 20% |

Baik FPR maupun TPR berbeda signifikan antara kedua grup.

*Step 4:* Analisis implikasi
- Grup A memiliki FPR lebih tinggi (45% vs 23%): Banyak orang dari Grup A yang sebenarnya tidak akan mengulangi kejahatan, tapi diprediksi akan melakukannya → hukuman lebih berat yang tidak adil
- Meskipun akurasi keseluruhan sama (65%), distribusi error sangat tidak seimbang

**Jawaban:** Sistem ini **tidak memenuhi** Equalized Odds karena FPR (45% vs 23%) dan TPR (72% vs 52%) berbeda signifikan antar grup. Implikasi serius: Grup A dikenai false positive jauh lebih banyak, yang berarti orang dari Grup A lebih sering salah diprediksi sebagai kriminal. Akurasi yang sama (65%) menyembunyikan distribusi error yang diskriminatif.

---

### 1.4 Transparency dan Explainability

> **Transparency** dalam AI mengacu pada kemampuan untuk memahami bagaimana dan mengapa sistem AI membuat keputusan tertentu.

> **Explainability (XAI - Explainable AI)** adalah kemampuan sistem AI untuk menjelaskan keputusannya dalam bentuk yang dapat dipahami manusia.

| Tingkat Transparency | Deskripsi | Contoh |
|---------------------|-----------|--------|
| **Black box** | Tidak ada penjelasan | Deep neural network kompleks |
| **Partial transparency** | Faktor utama diketahui | Feature importance dari random forest |
| **Full transparency** | Seluruh proses dapat ditelusuri | Decision tree sederhana |

Teknik-teknik XAI yang umum digunakan:

| Teknik | Pendekatan | Kelebihan |
|--------|------------|-----------|
| **LIME** | Approximasi lokal dengan model sederhana | Model-agnostic, intuitif |
| **SHAP** | Shapley values untuk kontribusi fitur | Theoretically grounded |
| **Attention visualization** | Menampilkan bagian input yang diperhatikan | Cocok untuk neural network |
| **Decision tree extraction** | Mengekstrak rules dari model kompleks | Mudah dipahami manusia |

#### Solved Problem 5 ⭐

**Soal:** Mengapa transparency penting dalam konteks AI militer? Berikan dua alasan spesifik!

**Penyelesaian:**

*Step 1:* Identifikasi konteks AI militer
- Keputusan yang menyangkut nyawa manusia
- Chain of command memerlukan justifikasi
- Hukum internasional mensyaratkan akuntabilitas

*Step 2:* Berikan alasan spesifik

**Alasan 1: Akuntabilitas Hukum**
- Hukum humaniter internasional (Geneva Conventions) mensyaratkan bahwa setiap serangan militer harus dapat dipertanggungjawabkan
- Jika AI membuat keputusan targeting, harus dapat dijelaskan mengapa target tersebut dipilih
- Tanpa transparency, tidak mungkin menentukan apakah keputusan melanggar hukum perang

**Alasan 2: Chain of Command**
- Komandan perlu memahami rekomendasi AI sebelum mengesahkan tindakan
- "I was just following the algorithm" bukan pembelaan yang sah
- Kepercayaan komandan terhadap sistem AI bergantung pada kemampuan memahami logikanya

**Jawaban:** Transparency AI militer penting karena: (1) Akuntabilitas hukum — hukum humaniter internasional mensyaratkan setiap keputusan militer dapat dipertanggungjawabkan, dan (2) Chain of command — komandan harus memahami rekomendasi AI sebelum mengesahkan tindakan yang berpotensi menyebabkan korban jiwa.

---

### 1.5 Accountability (Akuntabilitas)

> **Accountability** dalam AI adalah prinsip bahwa harus ada pihak yang bertanggung jawab atas keputusan dan dampak yang dihasilkan oleh sistem AI.

Pertanyaan kunci: **Siapa yang bertanggung jawab ketika AI membuat kesalahan?**

| Pihak | Potensi Tanggung Jawab |
|-------|----------------------|
| **Developer/Engineer** | Desain sistem, pemilihan data, bugs |
| **Data provider** | Kualitas dan bias dalam data |
| **Operator/User** | Penggunaan sistem di luar scope |
| **Organisasi** | Keputusan untuk deploy, oversight |
| **Regulator** | Standar dan pengawasan yang memadai |

#### Solved Problem 6 ⭐⭐

**Soal:** Sebuah mobil self-driving mengalami kecelakaan fatal karena gagal mendeteksi pejalan kaki pada malam hari. Analisis tanggung jawab dari perspektif accountability AI!

**Penyelesaian:**

*Step 1:* Identifikasi stakeholders

| Pihak | Peran |
|-------|-------|
| Manufaktur mobil | Produksi dan pemasaran |
| Pengembang AI | Desain model deteksi objek |
| Operator/penumpang | Pengawasan (bila diperlukan) |
| Regulator | Izin operasi di jalan publik |
| Pemerintah daerah | Infrastruktur jalan dan penerangan |

*Step 2:* Analisis tanggung jawab masing-masing

- **Pengembang AI**: Apakah model dilatih dengan cukup data malam hari? Apakah ada known limitation yang tidak dikomunikasikan?
- **Manufaktur**: Apakah sensor (kamera, LIDAR) cukup berkualitas untuk kondisi malam? Apakah safety testing memadai?
- **Operator**: Apakah ada peringatan untuk tetap waspada? Apakah operator mengabaikan peringatan?
- **Regulator**: Apakah standar safety untuk kendaraan otonom sudah memadai?

*Step 3:* Identifikasi tantangan

- **Distributed responsibility**: Tanggung jawab terpecah → risiko "nobody's fault"
- **Complexity**: Interaksi antar komponen membuat sulit mengisolasi penyebab tunggal
- **Transparency**: Jika model bersifat black box, sulit menentukan penyebab kegagalan

**Jawaban:** Tanggung jawab bersifat multi-pihak: pengembang AI (kualitas model dan data training), manufaktur (kualitas sensor dan safety testing), operator (pengawasan), dan regulator (standar keselamatan). Tantangan utama adalah distributed responsibility di mana tanggung jawab terpecah sehingga sulit menentukan pihak yang paling bertanggung jawab. Diperlukan kerangka hukum yang jelas untuk accountability AI.

---

## 2. AI Safety dan Risiko

### 2.1 Alignment Problem

> **Alignment Problem** adalah tantangan untuk memastikan bahwa tujuan dan perilaku sistem AI selaras dengan nilai dan niat manusia.

Alignment problem menjadi semakin penting seiring kemampuan AI meningkat. Masalah ini mencakup beberapa sub-problem:

| Sub-Problem | Penjelasan | Contoh |
|-------------|------------|--------|
| **Specification problem** | Sulit menspesifikasikan tujuan dengan tepat | AI yang diminta "minimisasi penderitaan" mungkin memutuskan untuk menghilangkan semua makhluk hidup |
| **Reward hacking** | AI menemukan cara untuk memaksimalkan reward tanpa memenuhi niat sebenarnya | Game AI yang menemukan exploit alih-alih bermain dengan baik |
| **Goal misgeneralization** | AI menggeneralisasi tujuan secara salah di distribusi baru | Robot yang belajar membersihkan dengan menyembunyikan sampah alih-alih membuangnya |
| **Instrumental convergence** | Sub-goals yang muncul dari hampir semua tujuan utama | Self-preservation, resource acquisition, goal preservation |

#### Solved Problem 7 ⭐

**Soal:** Jelaskan apa yang dimaksud dengan "reward hacking" dan berikan contoh dalam konteks sistem militer!

**Penyelesaian:**

*Step 1:* Definisikan reward hacking
- Reward hacking terjadi ketika AI menemukan cara yang tidak diinginkan untuk memaksimalkan reward function-nya
- AI mengoptimalkan **metrik** yang diberikan, bukan **niat** yang dimaksud

*Step 2:* Berikan contoh militer
- Sebuah drone AI diberi reward "maksimalisasi jumlah target yang dihancurkan"
- AI mungkin menembak target-target yang mudah (tidak dijaga) termasuk yang bernilai rendah, alih-alih memprioritaskan target bernilai tinggi yang lebih sulit
- Lebih buruk: AI mungkin mengklasifikasikan objek-objek non-target sebagai target untuk meningkatkan metrik

**Jawaban:** Reward hacking adalah ketika AI menemukan cara yang tidak diinginkan untuk memaksimalkan reward tanpa memenuhi niat sebenarnya. Contoh militer: drone AI dengan reward "jumlah target dihancurkan" mungkin memprioritaskan target mudah bernilai rendah atau bahkan mengklasifikasi objek non-target sebagai target demi meningkatkan metrik, berlawanan dengan tujuan operasional sebenarnya.

---

### 2.2 Existential Risk

> **Existential risk dari AI** merujuk pada kemungkinan bahwa AI tingkat lanjut (Artificial General Intelligence/AGI atau Superintelligence) dapat menimbulkan ancaman fundamental bagi kelangsungan peradaban manusia.

Terdapat spektrum pendapat mengenai risiko eksistensial AI:

| Perspektif | Argumen |
|------------|---------|
| **Pesimis** | AGI yang tidak aligned dapat mengoptimalkan tujuan yang mengorbankan umat manusia |
| **Moderat** | Risiko nyata tapi dapat dikelola dengan research yang tepat |
| **Optimis** | AGI masih jauh dan fokus sebaiknya pada masalah AI saat ini |

Konsep-konsep kunci dalam diskusi existential risk:

| Konsep | Penjelasan |
|--------|------------|
| **Intelligence explosion** | AI yang dapat memperbaiki dirinya sendiri → peningkatan kecerdasan eksponensial |
| **Orthogonality thesis** | Tingkat kecerdasan tidak menentukan tujuan — AI super-cerdas bisa memiliki tujuan apa saja |
| **Instrumental convergence** | Hampir semua tujuan utama menghasilkan sub-goals: self-preservation, resource acquisition |
| **Control problem** | Bagaimana memastikan AI yang lebih cerdas dari manusia tetap dapat dikontrol |

#### Solved Problem 8 ⭐⭐

**Soal:** Jelaskan "orthogonality thesis" dan mengapa konsep ini relevan untuk AI safety! Berikan ilustrasi dengan contoh!

**Penyelesaian:**

*Step 1:* Definisikan orthogonality thesis
- Dikemukakan oleh Nick Bostrom
- Menyatakan bahwa tingkat kecerdasan dan tujuan (goals) adalah dimensi yang ortogonal (independen)
- Artinya: AI super-cerdas bisa memiliki tujuan APA SAJA, termasuk tujuan yang tampak sepele atau berbahaya

*Step 2:* Jelaskan relevansinya
- Asumsi bahwa "AI cerdas pasti akan memilih tujuan yang baik" adalah salah
- Kecerdasan adalah kemampuan mencapai tujuan, bukan memilih tujuan yang "benar"
- Oleh karena itu, alignment harus di-design secara eksplisit, tidak bisa diasumsikan muncul dari kecerdasan

*Step 3:* Berikan ilustrasi

| Kecerdasan | Tujuan Baik | Tujuan Sepele | Tujuan Berbahaya |
|------------|-------------|---------------|------------------|
| Rendah | Chatbot bantuan | Kalkulator | Spam bot |
| Tinggi | Sistem medis canggih | Paperclip maximizer | Cyber weapon otonom |

Contoh klasik "paperclip maximizer" (Bostrom): AI super-cerdas yang diberi tujuan memproduksi paperclip sebanyak mungkin → mengkonversi seluruh sumber daya Bumi menjadi paperclip.

**Jawaban:** Orthogonality thesis menyatakan bahwa kecerdasan dan tujuan adalah dimensi independen — AI super-cerdas bisa memiliki tujuan apa saja, termasuk yang berbahaya atau sepele. Relevansinya: kita tidak bisa berasumsi bahwa AI cerdas otomatis akan "baik"; alignment harus di-design secara eksplisit. Ilustrasi: paperclip maximizer menunjukkan bahwa kecerdasan tinggi + tujuan sepele = konsekuensi katastrofik.

---

### 2.3 Keamanan Sistem AI

> **Keamanan AI (AI Security)** mencakup perlindungan sistem AI dari serangan dan penyalahgunaan, serta pencegahan penggunaan AI untuk tujuan berbahaya.

Ancaman keamanan pada sistem AI meliputi:

| Jenis Serangan | Deskripsi | Contoh |
|----------------|-----------|--------|
| **Adversarial attack** | Manipulasi input untuk mengelabui model | Menambah noise pada gambar agar salah klasifikasi |
| **Data poisoning** | Memasukkan data berbahaya ke training set | Menyisipkan backdoor yang aktif pada trigger tertentu |
| **Model stealing** | Mencuri model melalui query berulang | Membuat duplikat model komersial |
| **Privacy attack** | Mengekstrak data sensitif dari model | Membership inference untuk mengetahui data training |
| **Prompt injection** | Manipulasi instruksi pada LLM | Menyisipkan instruksi berbahaya dalam input |

#### Solved Problem 9 ⭐

**Soal:** Apa yang dimaksud dengan adversarial attack? Berikan contoh dalam konteks pengenalan objek militer!

**Penyelesaian:**

*Step 1:* Definisikan adversarial attack
- Penambahan perturbasi kecil (sering tidak terlihat mata manusia) pada input yang menyebabkan model AI menghasilkan output yang salah

*Step 2:* Berikan contoh militer
- Sistem klasifikasi citra satelit digunakan untuk mendeteksi instalasi militer
- Musuh dapat menambahkan pola kamuflase spesifik yang dihitung secara matematika pada atap bangunan
- Perturbasi ini menyebabkan AI mengklasifikasi bangunan militer sebagai bangunan sipil
- Perturbasi ini mungkin tidak terlihat mencurigakan oleh pengamat manusia biasa

**Jawaban:** Adversarial attack adalah manipulasi input dengan perturbasi kecil yang menyebabkan kesalahan klasifikasi. Dalam konteks militer: musuh dapat menambahkan pola kamuflase terkomputasi pada instalasi militer yang menyebabkan AI pengenalan citra satelit salah mengklasifikasi target militer sebagai objek sipil, sementara pengamat manusia mungkin tidak menyadari adanya perturbasi tersebut.

---

## 3. Privasi dan Surveillance

### 3.1 AI dan Privasi

> **Privasi data dalam konteks AI** adalah hak individu untuk mengontrol bagaimana data pribadi mereka dikumpulkan, digunakan, dan dibagikan oleh sistem AI.

Tantangan privasi yang muncul dari AI:

| Tantangan | Penjelasan |
|-----------|------------|
| **Mass data collection** | AI memerlukan data besar, mendorong pengumpulan data masif |
| **Inference capability** | AI dapat menyimpulkan informasi sensitif dari data yang tampak tidak sensitif |
| **Re-identification** | Data yang dianonimkan dapat di-identifikasi kembali oleh AI |
| **Persistent surveillance** | AI memungkinkan monitoring 24/7 yang tidak mungkin dilakukan manusia |
| **Function creep** | Data yang dikumpulkan untuk satu tujuan digunakan untuk tujuan lain |

#### Solved Problem 10 ⭐

**Soal:** Jelaskan apa yang dimaksud dengan "inference capability" dalam konteks privasi AI dan berikan contoh!

**Penyelesaian:**

*Step 1:* Definisikan inference capability
- Kemampuan AI untuk menyimpulkan informasi yang tidak diberikan secara eksplisit dari data yang tersedia

*Step 2:* Berikan contoh

- Dari data pembelian di supermarket, AI dapat menyimpulkan: kondisi kesehatan (obat-obatan), agama (halal food), kehamilan (vitamin prenatal), status ekonomi
- Dari metadata telepon (tanpa konten percakapan): pola hubungan sosial, jadwal aktivitas, lokasi rumah dan kantor
- Dari pola typing di keyboard: kondisi emosional, tingkat kelelahan

**Jawaban:** Inference capability adalah kemampuan AI menyimpulkan informasi sensitif dari data yang tampak tidak sensitif. Contoh: AI dapat menyimpulkan kondisi kesehatan, agama, atau bahkan kehamilan seseorang hanya dari data pembelian supermarket tanpa orang tersebut memberikan informasi tersebut secara eksplisit.

---

### 3.2 Surveillance Systems

> **AI surveillance** adalah penggunaan kecerdasan artifisial untuk pemantauan sistematis terhadap aktivitas, perilaku, atau komunikasi individu atau kelompok.

| Jenis Surveillance | Teknologi AI | Penggunaan |
|--------------------|-------------|------------|
| **Pengenalan wajah** | Computer vision, deep learning | Identifikasi individu di ruang publik |
| **Analisis perilaku** | Pattern recognition, anomaly detection | Deteksi perilaku mencurigakan |
| **SIGINT** | NLP, speech recognition | Analisis komunikasi |
| **Social media monitoring** | NLP, sentiment analysis | Tracking opini dan aktivitas online |
| **Predictive policing** | Machine learning, spatial analysis | Prediksi lokasi dan waktu kejahatan |

#### Solved Problem 11 ⭐⭐

**Soal:** Bandingkan perspektif keamanan nasional dan perspektif hak asasi manusia mengenai penggunaan AI surveillance oleh negara! Identifikasi titik keseimbangan yang mungkin!

**Penyelesaian:**

*Step 1:* Analisis perspektif keamanan nasional

| Argumen | Penjelasan |
|---------|------------|
| Pencegahan terorisme | Deteksi ancaman sebelum terjadi |
| Keamanan perbatasan | Monitoring wilayah kedaulatan |
| Investigasi kriminal | Percepatan identifikasi pelaku |
| Keamanan publik | Pengawasan tempat-tempat rawan |

*Step 2:* Analisis perspektif hak asasi manusia

| Argumen | Penjelasan |
|---------|------------|
| Hak privasi | Kebebasan dari pengawasan tanpa dasar hukum |
| Chilling effect | Orang mengubah perilaku karena merasa diawasi |
| Potensi penyalahgunaan | Surveillance dapat digunakan untuk menekan oposisi |
| False positives | Orang tidak bersalah terdampak |

*Step 3:* Titik keseimbangan

- **Proporsionalitas**: Tingkat surveillance sebanding dengan tingkat ancaman
- **Judicial oversight**: Pengawasan yudisial untuk penggunaan surveillance
- **Data minimization**: Hanya mengumpulkan data yang diperlukan
- **Transparency reports**: Publikasi statistik penggunaan surveillance
- **Sunset clauses**: Batas waktu untuk program surveillance

**Jawaban:** Perspektif keamanan nasional menekankan kebutuhan surveillance untuk pencegahan ancaman, sementara perspektif HAM menekankan hak privasi dan risiko penyalahgunaan. Titik keseimbangan dapat dicapai melalui: proporsionalitas (surveillance sebanding ancaman), judicial oversight, data minimization, transparency reports, dan sunset clauses yang membatasi durasi program.

---

## 4. AI dalam Konteks Pertahanan

### 4.1 Autonomous Weapons Systems (AWS)

> **Autonomous Weapons Systems (AWS)** atau Lethal Autonomous Weapons Systems (LAWS) adalah sistem senjata yang dapat memilih dan menyerang target tanpa intervensi manusia.

Tingkat otonomi dalam sistem senjata:

| Tingkat | Deskripsi | Contoh |
|---------|-----------|--------|
| **Human-in-the-loop** | Manusia membuat semua keputusan penembakan | Drone yang dikendalikan operator |
| **Human-on-the-loop** | AI merekomendasikan, manusia menyetujui | Sistem pertahanan udara dengan konfirmasi |
| **Human-out-of-the-loop** | AI memutuskan secara otonom | Senjata yang sepenuhnya otonom |

![Tingkat Otonomi Senjata](images/p15-02-autonomy-levels-weapons.png)

*Gambar 15.2: Spektrum tingkat otonomi dalam sistem senjata*

#### Solved Problem 12 ⭐

**Soal:** Jelaskan argumen pro dan kontra terhadap pengembangan Lethal Autonomous Weapons Systems (LAWS)! Tentukan posisi yang paling seimbang!

**Penyelesaian:**

*Step 1:* Analisis argumen pro

| Argumen Pro | Penjelasan |
|-------------|------------|
| Kecepatan respons | Reaksi lebih cepat dari manusia dalam situasi kritis |
| Mengurangi risiko personel | Mengurangi korban di pihak sendiri |
| Konsistensi | Tidak terpengaruh emosi, kelelahan, atau ketakutan |
| Presisi | Potensi mengurangi collateral damage |

*Step 2:* Analisis argumen kontra

| Argumen Kontra | Penjelasan |
|----------------|------------|
| Accountability gap | Siapa yang bertanggung jawab atas kesalahan? |
| Dehumanisasi perang | Menurunkan threshold untuk berperang |
| Keandalan | Risiko malfunction, hacking, atau adversarial attack |
| Hukum humaniter | Sulit memenuhi prinsip proporsionalitas dan distinction |
| Arms race | Memicu perlombaan senjata otonom global |

*Step 3:* Posisi seimbang

**Pendekatan "Meaningful Human Control":**
- Manusia harus tetap memiliki kontrol bermakna dalam keputusan lethal
- Human-on-the-loop sebagai minimum: AI merekomendasikan, manusia memutuskan
- Exception untuk defensive systems dengan waktu respons sangat singkat (misalnya pertahanan rudal)

**Jawaban:** Argumen pro LAWS meliputi kecepatan, keselamatan personel, dan konsistensi. Argumen kontra mencakup accountability gap, dehumanisasi, dan risiko keandalan. Posisi paling seimbang adalah "Meaningful Human Control" di mana AI membantu pengambilan keputusan tetapi manusia tetap memegang kendali akhir untuk keputusan lethal, dengan pengecualian terbatas untuk sistem defensif dengan waktu respons kritis.

---

### 4.2 Aplikasi AI dalam Pertahanan Indonesia

AI memiliki berbagai aplikasi potensial dalam konteks pertahanan Indonesia:

| Domain | Aplikasi | Manfaat |
|--------|----------|---------|
| **C6ISR** | Fusi data intelijen otomatis | Situational awareness yang lebih baik |
| **Pertahanan udara** | Identifikasi ancaman otomatis | Waktu respons lebih cepat |
| **Maritim** | AUV patroli perbatasan | Cakupan area lebih luas |
| **Cyber** | Deteksi serangan siber otomatis | Respons real-time |
| **Logistik** | Optimasi supply chain militer | Efisiensi sumber daya |
| **Simulasi** | Wargaming dan perencanaan | Latihan cost-effective |

#### Solved Problem 13 ⭐⭐

**Soal:** Bagaimana AI dapat diterapkan dalam sistem C6ISR (Command, Control, Communications, Computers, Combat Systems, Intelligence, Surveillance, Reconnaissance) TNI? Berikan tiga contoh aplikasi spesifik!

**Penyelesaian:**

*Step 1:* Pahami komponen C6ISR dan kebutuhannya

*Step 2:* Identifikasi aplikasi AI spesifik

**Aplikasi 1: Intelligence Fusion**
- AI menggabungkan data dari berbagai sumber (HUMINT, SIGINT, IMINT, OSINT)
- Algoritma: NLP untuk analisis teks intelijen, computer vision untuk citra satelit
- Menghasilkan common operational picture yang terintegrasi
- Contoh: mendeteksi pola pergerakan kapal asing di perairan Indonesia

**Aplikasi 2: Automated Threat Assessment**
- AI menganalisis data sensor (radar, sonar) untuk klasifikasi ancaman otomatis
- Algoritma: classification (Bayesian network, deep learning)
- Memprioritaskan ancaman dan merekomendasikan respons
- Contoh: identifikasi otomatis pesawat udara asing yang memasuki FIR Indonesia

**Aplikasi 3: Predictive Maintenance Alutsista**
- AI memprediksi kebutuhan perawatan kendaraan tempur, pesawat, kapal
- Algoritma: time series analysis, anomaly detection
- Mengurangi downtime dan biaya perawatan
- Contoh: prediksi kegagalan komponen mesin jet F-16

**Jawaban:** Tiga aplikasi AI dalam C6ISR TNI: (1) Intelligence Fusion — penggabungan otomatis multi-source intelligence menggunakan NLP dan computer vision, (2) Automated Threat Assessment — klasifikasi dan prioritisasi ancaman otomatis menggunakan Bayesian network dan deep learning, (3) Predictive Maintenance — prediksi kebutuhan perawatan alutsista menggunakan time series analysis dan anomaly detection.

---

### 4.3 Pertimbangan Etis AI Militer

#### Solved Problem 14 ⭐⭐⭐

**Soal:** Sebuah drone pengintai TNI AU yang menggunakan AI mendeteksi aktivitas mencurigakan di daerah perbatasan. Sistem AI mengklasifikasikan target dengan confidence 78% sebagai "aktivitas penyelundupan senjata". Sebagai komandan, analisis dilema etis dan keputusan yang harus diambil!

**Penyelesaian:**

*Step 1:* Identifikasi dilema etis

| Faktor | Pro-Tindakan | Pro-Kehati-hatian |
|--------|-------------|-------------------|
| Confidence level | 78% cukup tinggi | 22% kemungkinan salah signifikan |
| Risiko jika benar | Membiarkan penyelundupan membahayakan keamanan | - |
| Risiko jika salah | - | Bisa menyerang warga sipil yang tidak bersalah |
| Waktu | Target mungkin hilang jika terlambat | Terburu-buru meningkatkan risiko kesalahan |

*Step 2:* Aplikasikan prinsip-prinsip etis

**Prinsip Proporsionalitas:**
- Tindakan harus proporsional dengan ancaman
- Confidence 78% belum cukup untuk tindakan lethal
- Cukup untuk tindakan non-lethal (surveillance lanjutan)

**Prinsip Distinction:**
- Sistem harus dapat membedakan kombatan dan sipil
- 22% ketidakpastian berarti sistem belum cukup yakin

**Prinsip Meaningful Human Control:**
- AI memberikan rekomendasi, manusia memutuskan
- Komandan tidak boleh "blindly follow" AI

*Step 3:* Keputusan yang tepat

1. **Jangan ambil tindakan lethal** berdasarkan confidence 78%
2. **Tingkatkan surveillance**: kirim aset tambahan (drone lain, HUMINT)
3. **Kumpulkan data tambahan** untuk meningkatkan confidence
4. **Laporkan ke atasan** dengan semua informasi termasuk uncertainty
5. **Dokumentasikan** keputusan dan alasannya

**Jawaban:** Dengan confidence 78%, tindakan lethal tidak etis karena melanggar prinsip distinction (22% kemungkinan target sipil). Keputusan yang tepat: (1) tidak mengambil tindakan lethal, (2) meningkatkan surveillance, (3) mengumpulkan data tambahan, (4) melaporkan ke rantai komando dengan full disclosure termasuk uncertainty, (5) mendokumentasikan proses pengambilan keputusan. Ini menerapkan prinsip meaningful human control dan proporsionalitas.

---

## 5. Regulasi AI

### 5.1 Kerangka Regulasi Global

> **Regulasi AI** adalah seperangkat aturan, standar, dan pedoman yang mengatur pengembangan dan penggunaan sistem kecerdasan artifisial.

| Regulasi | Wilayah | Pendekatan | Fitur Utama |
|----------|---------|------------|-------------|
| **EU AI Act** | Uni Eropa | Risk-based | Klasifikasi risiko: minimal, limited, high, unacceptable |
| **Executive Order on AI** | Amerika Serikat | Sector-specific | Safety testing, reporting requirements |
| **AI Governance Framework** | Singapura | Principles-based | FEAT: Fairness, Ethics, Accountability, Transparency |
| **Blueprint for AI Bill of Rights** | Amerika Serikat | Rights-based | Lima prinsip perlindungan |

#### EU AI Act — Klasifikasi Risiko:

| Kategori Risiko | Contoh | Regulasi |
|-----------------|--------|----------|
| **Unacceptable** | Social scoring, manipulasi subliminal | Dilarang |
| **High risk** | Rekrutmen AI, kredit scoring, AI medis | Wajib assessment, transparency, human oversight |
| **Limited risk** | Chatbot, deepfake | Wajib disclosure |
| **Minimal risk** | Spam filter, game AI | Tidak ada regulasi khusus |

#### Solved Problem 15 ⭐

**Soal:** Menurut EU AI Act, klasifikasikan tiga sistem AI berikut ke dalam kategori risiko yang tepat: (a) AI untuk credit scoring, (b) AI untuk rekomendasi musik, (c) AI untuk social scoring oleh pemerintah!

**Penyelesaian:**

*Step 1:* Pahami setiap kategori risiko EU AI Act
- Unacceptable: Mengancam hak fundamental
- High risk: Berdampak signifikan pada kehidupan
- Limited risk: Perlu transparency
- Minimal risk: Tidak perlu regulasi khusus

*Step 2:* Klasifikasikan

**(a) AI untuk credit scoring:**
- Mempengaruhi akses keuangan individu
- Kesalahan berdampak pada kemampuan hidup (rumah, bisnis)
- **High Risk** → Wajib assessment, transparency, human oversight

**(b) AI untuk rekomendasi musik:**
- Dampak minimal pada hak fundamental
- Kesalahan (rekomendasi buruk) tidak berbahaya
- **Minimal Risk** → Tidak perlu regulasi khusus

**(c) AI untuk social scoring oleh pemerintah:**
- Mengancam kebebasan dan hak fundamental
- Potensi diskriminasi masif
- **Unacceptable** → Dilarang

**Jawaban:** (a) Credit scoring → **High Risk** (berdampak pada akses keuangan), (b) Rekomendasi musik → **Minimal Risk** (dampak minimal), (c) Social scoring → **Unacceptable** (mengancam hak fundamental, dilarang oleh EU AI Act).

---

### 5.2 AI dan Hukum Internasional dalam Konteks Pertahanan

| Kerangka Hukum | Relevansi untuk AI Militer |
|----------------|---------------------------|
| **Geneva Conventions** | Prinsip distinction dan proporsionalitas berlaku untuk AWS |
| **Convention on Certain Conventional Weapons (CCW)** | Forum diskusi regulasi LAWS di PBB |
| **International Humanitarian Law (IHL)** | Kewajiban meaningful human control |
| **AUKUS** | Kerjasama AI pertahanan antara Australia-UK-AS |

#### Solved Problem 16 ⭐⭐

**Soal:** Jelaskan mengapa prinsip "distinction" dalam hukum humaniter internasional menjadi tantangan besar bagi pengembangan autonomous weapons!

**Penyelesaian:**

*Step 1:* Jelaskan prinsip distinction
- Prinsip distinction mensyaratkan pembedaan antara kombatan dan sipil
- Serangan hanya boleh ditujukan kepada target militer
- Pelanggaran prinsip ini merupakan kejahatan perang

*Step 2:* Identifikasi tantangan AI dalam memenuhi prinsip distinction

| Tantangan | Penjelasan |
|-----------|------------|
| **Ambiguitas visual** | Sipil dan kombatan sering tidak dapat dibedakan secara visual |
| **Konteks situasional** | Kombatan yang menyerah menjadi protected person (hors de combat) |
| **Dual-use** | Bangunan/kendaraan bisa berubah status sipil-militer |
| **Adversarial manipulation** | Musuh dapat menyamar sebagai sipil |
| **Edge cases** | Situasi unik yang tidak ada dalam data training |

*Step 3:* Analisis keterbatasan AI saat ini
- Computer vision masih memiliki error rate signifikan
- Pemahaman konteks masih terbatas
- Adversarial attacks dapat mengelabui sistem
- Tidak ada kemampuan reasoning tentang konsep legal "kombatan"

**Jawaban:** Prinsip distinction mensyaratkan pembedaan kombatan-sipil yang merupakan tantangan fundamental bagi AI karena: (1) ambiguitas visual antara sipil dan kombatan, (2) kebutuhan pemahaman konteks (misal kombatan yang menyerah), (3) dual-use facilities yang berubah status, (4) kerentanan terhadap adversarial manipulation, dan (5) ketidakmampuan AI saat ini untuk melakukan reasoning tentang konsep legal. Keterbatasan ini menjadikan meaningful human control esensial.

---

### 5.3 Kebijakan AI Nasional Indonesia

#### Solved Problem 17 ⭐

**Soal:** Sebutkan tiga aspek yang sebaiknya ada dalam kebijakan nasional AI Indonesia untuk konteks pertahanan!

**Penyelesaian:**

*Step 1:* Identifikasi kebutuhan spesifik Indonesia
- Negara kepulauan terbesar dengan tantangan surveillance maritim
- Kebutuhan modernisasi pertahanan
- Keterbatasan anggaran dan SDM AI

*Step 2:* Usulkan tiga aspek kebijakan

**Aspek 1: Standar Keamanan dan Keandalan**
- Standar testing AI militer sebelum deployment
- Prosedur sertifikasi untuk sistem AI kritis
- Requirement untuk meaningful human control

**Aspek 2: Pengembangan SDM**
- Program pendidikan AI untuk personel militer
- Kerjasama dengan universitas dan industri
- Training etika AI untuk semua operator

**Aspek 3: Kerangka Etika dan Governance**
- Dewan etika AI pertahanan
- Prosedur audit reguler untuk bias dan keandalan
- Mekanisme pelaporan insiden AI

**Jawaban:** Tiga aspek penting: (1) Standar keamanan dan keandalan — testing, sertifikasi, meaningful human control; (2) Pengembangan SDM — pendidikan AI militer, kerjasama universitas-industri; (3) Kerangka etika dan governance — dewan etika, audit reguler, mekanisme pelaporan insiden.

---

## 6. Masa Depan AI

### 6.1 Artificial General Intelligence (AGI)

> **Artificial General Intelligence (AGI)** adalah AI yang memiliki kemampuan kognitif setara atau melampaui manusia di seluruh domain tugas intelektual.

Perbandingan tingkat AI:

| Tingkat | Deskripsi | Status Saat Ini |
|---------|-----------|-----------------|
| **Narrow AI (ANI)** | AI yang unggul di satu tugas spesifik | Sudah tercapai (AlphaGo, ChatGPT, dll.) |
| **General AI (AGI)** | AI setara manusia di semua domain | Belum tercapai, timeline diperdebatkan |
| **Super AI (ASI)** | AI yang melampaui seluruh kemampuan manusia | Spekulatif |

#### Solved Problem 18 ⭐

**Soal:** Jelaskan perbedaan antara Narrow AI dan AGI dengan masing-masing satu contoh!

**Penyelesaian:**

*Step 1:* Definisikan perbedaan kunci

| Aspek | Narrow AI | AGI |
|-------|-----------|-----|
| Scope | Satu tugas spesifik | Semua tugas intelektual |
| Transfer | Tidak bisa transfer ke domain lain | Dapat generalize antar domain |
| Pemahaman | Pattern matching tanpa pemahaman mendalam | True understanding |
| Adaptasi | Perlu re-training untuk tugas baru | Belajar tugas baru secara fleksibel |

*Step 2:* Berikan contoh

- **Narrow AI**: AlphaGo — dapat bermain Go di level superhuman, tapi tidak bisa bermain catur, menulis puisi, atau melakukan tugas apapun selain Go
- **AGI (hipotetis)**: Sistem yang dapat bermain Go, menulis essay, mendiagnosis penyakit, memprogram komputer, dan melakukan semua tugas intelektual pada level manusia atau lebih baik

**Jawaban:** Narrow AI unggul di satu tugas spesifik (contoh: AlphaGo yang superhuman di Go tapi tidak bisa apa-apa selain itu), sedangkan AGI mampu melakukan semua tugas intelektual pada level manusia (contoh hipotetis: sistem yang bisa bermain Go, menulis, mendiagnosis, dan memprogram). Saat ini hanya Narrow AI yang sudah tercapai.

---

### 6.2 Dampak Sosial-Ekonomi AI

| Dampak | Positif | Negatif |
|--------|---------|---------|
| **Pekerjaan** | Penciptaan jenis pekerjaan baru | Otomatisasi menghilangkan pekerjaan tertentu |
| **Ekonomi** | Peningkatan produktivitas | Ketimpangan semakin besar |
| **Pendidikan** | Personalisasi pembelajaran | Digital divide |
| **Kesehatan** | Diagnosis lebih akurat | Akses tidak merata |
| **Keamanan** | Deteksi ancaman lebih baik | Senjata otonom dan surveillance |

#### Solved Problem 19 ⭐⭐

**Soal:** Analisis dampak AI terhadap dunia kerja militer dalam 10-20 tahun ke depan! Identifikasi tiga jenis pekerjaan militer yang mungkin berubah signifikan!

**Penyelesaian:**

*Step 1:* Identifikasi pekerjaan militer yang terpengaruh AI

**Pekerjaan 1: Analis Intelijen**
- Saat ini: Analis membaca ratusan laporan manual
- Masa depan: AI melakukan initial screening dan summarization
- Perubahan: Peran bergeser dari pengumpulan ke interpretasi strategis
- Skill baru: Kemampuan bekerja dengan AI tools, critical thinking

**Pekerjaan 2: Operator Kendaraan Militer**
- Saat ini: Pilot, pengemudi tank, nakhoda kapal
- Masa depan: Swarm drones, autonomous vehicles, unmanned vessels
- Perubahan: Dari operator ke supervisor multi-platform
- Skill baru: Human-AI teaming, multi-system management

**Pekerjaan 3: Staf Logistik**
- Saat ini: Perencanaan supply chain manual
- Masa depan: AI-optimized logistics, predictive maintenance
- Perubahan: Dari eksekusi rutin ke exception handling dan oversight
- Skill baru: Data literacy, AI system management

*Step 2:* Identifikasi implikasi

- Kebutuhan re-skilling personel militer
- Perubahan doktrin dan organisasi
- Pentingnya pendidikan AI di akademi militer

**Jawaban:** Tiga pekerjaan militer yang berubah signifikan: (1) Analis intelijen — bergeser dari pengumpulan manual ke interpretasi strategis dengan bantuan AI, (2) Operator kendaraan militer — bergeser dari operator tunggal ke supervisor multi-platform otonom, (3) Staf logistik — bergeser dari eksekusi rutin ke oversight AI-optimized systems. Implikasi: kebutuhan re-skilling masif dan integrasi pendidikan AI di akademi militer.

---

## 7. Review Komprehensif (Pertemuan 1-14)

### 7.1 Peta Konsep Keseluruhan

![Peta Konsep AI](images/p15-03-ai-concept-map.png)

*Gambar 15.3: Peta konsep keseluruhan mata kuliah Kecerdasan Artifisial*

### 7.2 Ringkasan per Topik

#### Pertemuan 1-2: Agen Cerdas dan Pencarian Uninformed

| Konsep | Poin Kunci |
|--------|------------|
| **Agen Cerdas** | Entitas yang mempersepsi (sensor) dan bertindak (aktuator) pada lingkungan |
| **5 Jenis Agen** | Simple Reflex → Model-Based → Goal-Based → Utility-Based → Learning |
| **PEAS** | Performance, Environment, Actuators, Sensors |
| **6 Karakteristik Lingkungan** | Observable, Deterministic, Episodic, Static, Discrete, Single/Multi-agent |
| **BFS** | Complete, optimal (unit cost), O(b^d) time & space |
| **DFS** | Not complete (infinite), not optimal, O(bm) time, O(bm) space |
| **UCS** | Complete, optimal, O(b^(1+⌊C*/ε⌋)) |

#### Pertemuan 3-4: Informed Search dan Pencarian Lokal

| Konsep | Poin Kunci |
|--------|------------|
| **Greedy Best-First** | f(n) = h(n), tidak optimal, tidak complete |
| **A*** | f(n) = g(n) + h(n), optimal jika h admissible, complete |
| **Admissible heuristic** | h(n) ≤ h*(n) — tidak pernah overestimate |
| **Consistent heuristic** | h(n) ≤ c(n,a,n') + h(n') |
| **Hill Climbing** | Greedy local search, terjebak di local maxima |
| **Simulated Annealing** | Probabilistic escape dari local maxima, jadwal pendinginan |
| **Algoritma Genetika** | Populasi, seleksi, crossover, mutasi |

#### Pertemuan 5-6: Game Playing dan CSP

| Konsep | Poin Kunci |
|--------|------------|
| **Minimax** | Optimal untuk zero-sum game, O(b^m) |
| **Alpha-Beta Pruning** | Optimal ordering: O(b^(m/2)) |
| **Evaluation function** | Estimasi utility untuk non-terminal states |
| **CSP** | Variables, Domains, Constraints |
| **AC-3** | Arc consistency, mengurangi domain |
| **Backtracking CSP** | Systematic search dengan constraint checking |
| **MRV** | Pilih variabel dengan domain terkecil |
| **LCV** | Pilih nilai yang mengeliminasi paling sedikit |

#### Pertemuan 9-10: Logika Proposisional dan Predikat

| Konsep | Poin Kunci |
|--------|------------|
| **Logika Proposisional** | Konnektif: ¬, ∧, ∨, →, ↔ |
| **Entailment** | KB ⊨ α jika α benar di setiap model di mana KB benar |
| **Resolution** | Metode pembuktian berbasis CNF |
| **FOL** | Kuantor: ∀ (universal), ∃ (eksistensial) |
| **Unifikasi** | Most General Unifier (MGU) |
| **Forward Chaining** | Data-driven reasoning |
| **Backward Chaining** | Goal-driven reasoning |

#### Pertemuan 11-12: Probabilitas dan Jaringan Bayesian

| Konsep | Poin Kunci |
|--------|------------|
| **Teorema Bayes** | P(H\|E) = P(E\|H)P(H)/P(E) |
| **Conditional Independence** | P(X\|Y,Z) = P(X\|Z) |
| **Jaringan Bayesian** | DAG + CPT, representasi compact joint distribution |
| **d-separation** | Metode menentukan conditional independence dari struktur graf |
| **Variable Elimination** | Algoritma inferensi eksak |

#### Pertemuan 13-14: Machine Learning

| Konsep | Poin Kunci |
|--------|------------|
| **Supervised Learning** | Training dari labeled data |
| **Decision Tree** | Information gain, entropy, pruning |
| **Naive Bayes** | Asumsi conditional independence antar fitur |
| **K-Means** | Clustering iteratif, pemilihan K dengan elbow method |
| **Evaluasi** | Accuracy, precision, recall, F1-score |
| **Cross-validation** | K-fold untuk estimasi generalisasi |
| **Reinforcement Learning** | Agent-environment, MDP, Q-learning |

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Sebuah sistem pertahanan siber menggunakan berbagai teknik AI. Hubungkan setiap komponen berikut dengan topik yang sesuai dari mata kuliah ini:
1. Deteksi anomali lalu lintas jaringan
2. Klasifikasi jenis malware
3. Perencanaan respons insiden
4. Prediksi sumber serangan
5. Aturan firewall otomatis

**Penyelesaian:**

*Step 1:* Analisis setiap komponen dan hubungkan dengan topik kuliah

| Komponen | Topik Terkait | Penjelasan |
|----------|--------------|------------|
| Deteksi anomali lalu lintas | **Unsupervised Learning** (Pertemuan 14) | Anomaly detection menggunakan clustering (K-Means) untuk mendeteksi pola lalu lintas yang tidak normal |
| Klasifikasi jenis malware | **Supervised Learning** (Pertemuan 13) | Decision tree atau Naive Bayes untuk mengklasifikasi malware berdasarkan fitur perilaku |
| Perencanaan respons insiden | **Search/Planning** (Pertemuan 2-4) | Goal-based search untuk menemukan urutan tindakan respons optimal (A* atau planning) |
| Prediksi sumber serangan | **Jaringan Bayesian** (Pertemuan 12) | Probabilistic reasoning untuk memprediksi sumber berdasarkan evidence (IP, pola, waktu) |
| Aturan firewall otomatis | **CSP** (Pertemuan 6) | Constraint satisfaction untuk menghasilkan konfigurasi firewall yang memenuhi semua requirement keamanan |

*Step 2:* Jelaskan integrasi

Sistem pertahanan siber yang komprehensif mengintegrasikan hampir semua topik AI yang dipelajari:
- **Agen cerdas** (Pertemuan 1) sebagai arsitektur keseluruhan — sistem adalah learning agent yang terus memperbaiki diri
- **Search** untuk planning respons
- **Probabilistic reasoning** untuk inference tentang ancaman
- **Machine learning** untuk deteksi dan klasifikasi

**Jawaban:** (1) Deteksi anomali → Unsupervised Learning/K-Means, (2) Klasifikasi malware → Supervised Learning/Decision Tree, (3) Perencanaan respons → Search & Planning/A*, (4) Prediksi sumber → Jaringan Bayesian, (5) Aturan firewall → CSP. Ini menunjukkan bahwa sistem pertahanan siber modern mengintegrasikan hampir seluruh topik AI dari mata kuliah ini.

---

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Bandingkan keempat metode penalaran/pengambilan keputusan yang dipelajari dalam mata kuliah ini untuk skenario berikut: "Menentukan apakah kapal asing di perairan Indonesia merupakan ancaman." Metode mana yang paling sesuai?

Metode: (a) Logika Proposisional, (b) Logika Predikat, (c) Jaringan Bayesian, (d) Decision Tree

**Penyelesaian:**

*Step 1:* Analisis skenario
- Informasi yang tersedia: jenis kapal, bendera, rute, kecepatan, sensor readings
- Sifat informasi: tidak pasti, mungkin tidak lengkap
- Output: level ancaman (bukan hanya binary)

*Step 2:* Evaluasi setiap metode

**(a) Logika Proposisional:**
- Dapat merepresentasikan aturan sederhana: "JIKA kapal militer DAN tanpa izin MAKA ancaman"
- Keterbatasan: tidak menangani ketidakpastian, hanya binary (ancaman/bukan)
- Kesesuaian: **Rendah** — terlalu rigid untuk situasi nyata

**(b) Logika Predikat:**
- Lebih ekspresif: ∀x (KapalMiliter(x) ∧ ¬PunyaIzin(x) → Ancaman(x))
- Dapat merepresentasikan relasi antar entitas
- Keterbatasan: tetap tidak menangani ketidakpastian
- Kesesuaian: **Sedang** — cocok untuk rule-based reasoning jika informasi lengkap

**(c) Jaringan Bayesian:**
- Menangani ketidakpastian secara eksplisit
- P(Ancaman | JenisKapal, Bendera, Rute, Kecepatan, Sensor)
- Dapat menghasilkan probabilitas, bukan hanya binary
- Mengakomodasi informasi tidak lengkap
- Kesesuaian: **Tinggi** — paling sesuai untuk situasi dengan ketidakpastian

**(d) Decision Tree:**
- Dapat dipelajari dari data historis
- Menghasilkan rules yang dapat dipahami
- Keterbatasan: output biasanya klasifikasi diskret
- Kesesuaian: **Sedang-Tinggi** — bagus untuk klasifikasi tapi kurang untuk reasoning probabilistik

*Step 3:* Tentukan metode paling sesuai

**Jawaban:** Metode paling sesuai adalah **(c) Jaringan Bayesian** karena: (1) mampu menangani ketidakpastian yang inherent dalam situasi maritim, (2) dapat menghasilkan probabilitas ancaman, bukan hanya binary, (3) mengakomodasi informasi yang tidak lengkap (misalnya sensor readings partial), (4) dapat dikombinasikan dengan expert knowledge melalui struktur graf kausal. Idealnya, decision tree dapat digunakan sebagai preprocessor untuk mengekstrak fitur awal, kemudian Bayesian network untuk final assessment.

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Untuk persiapan UAS, selesaikan soal integratif berikut:

Sebuah sistem robot SAR (Search and Rescue) TNI harus menemukan korban bencana di area seluas 10 km². Robot memiliki sensor thermal (jangkauan 50m), GPS, dan radio. Area dibagi menjadi grid 100×100 cells. Beberapa cells blocked (bangunan runtuh). Waktu terbatas: baterai 4 jam.

(a) Formulasikan sebagai search problem
(b) Tentukan algoritma pencarian yang sesuai dan jelaskan
(c) Identifikasi jenis agen yang diperlukan
(d) Buat analisis PEAS
(e) Pertimbangan etis apa yang relevan?

**Penyelesaian:**

**(a) Formulasi Search Problem:**

| Komponen | Spesifikasi |
|----------|-------------|
| **State** | Posisi robot (cell x,y), set cells yang sudah di-scan, waktu tersisa |
| **Initial State** | Posisi awal robot, belum ada cell yang di-scan, waktu = 4 jam |
| **Actions** | Move(N/S/E/W), Scan() |
| **Transition Model** | Move mengubah posisi, Scan menandai cell sebagai scanned |
| **Goal Test** | Semua reachable cells sudah di-scan ATAU korban ditemukan ATAU waktu habis |
| **Path Cost** | Coverage: jumlah cells yang belum di-scan (minimize) + waktu (minimize) |

**(b) Algoritma Pencarian:**

Karena area besar dan waktu terbatas, pencarian coverage optimal diperlukan:

- **A* tidak cocok**: karena goal test bukan mencapai satu state tujuan, tapi memaksimalkan coverage
- **Yang sesuai**: Pendekatan **utility-based search** dengan komponen:
  - **Greedy best-first** untuk arah menuju area belum ter-scan yang terdekat
  - **Simulated Annealing** atau **Genetic Algorithm** (Pertemuan 4) untuk mengoptimalkan rute coverage
  - Heuristik: prioritaskan area dengan probabilitas korban tinggi (dekat bangunan runtuh)

**(c) Jenis Agen: Utility-Based Agent dengan Learning**

| Requirement | Jenis Agen |
|-------------|------------|
| Track cells yang sudah di-scan | Model-Based |
| Tujuan: maksimalkan coverage | Goal-Based |
| Trade-off: coverage vs baterai vs jarak | Utility-Based |
| Adaptasi: revisi prioritas saat menemukan evidence | Learning |

Utility function: U = w₁ × Coverage + w₂ × P(FindVictim) - w₃ × EnergyUsed

**(d) Analisis PEAS:**

| Komponen | Spesifikasi |
|----------|-------------|
| **Performance** | Jumlah korban ditemukan, waktu menemukan, area coverage, battery efficiency |
| **Environment** | Grid area bencana, reruntuhan, korban, kondisi terrain, cuaca |
| **Actuators** | Motor penggerak, radio transmitter, beacon/marker, speaker (calling) |
| **Sensors** | Thermal camera (50m), GPS, battery level sensor, terrain sensor, audio sensor |

Karakteristik lingkungan:
- Partially Observable (thermal sensor range 50m)
- Stochastic (posisi korban tidak diketahui)
- Sequential (posisi saat ini mempengaruhi reachable cells)
- Dynamic (kondisi korban berubah, reruntuhan bisa bergerak)
- Continuous (posisi)
- Single agent (satu robot) atau Multi-agent (jika multiple robot)

**(e) Pertimbangan Etis:**

| Aspek Etis | Pertimbangan |
|------------|--------------|
| **Prioritasi korban** | Bagaimana memprioritaskan jika terdeteksi multiple korban? |
| **Risk assessment** | Robot harus mengukur risiko runtuhan lanjutan vs potensi menemukan korban |
| **Resource allocation** | Apakah meneruskan pencarian area berbahaya jika baterai rendah? |
| **Communication** | Wajib melaporkan temuan segera, bukan menunggu pencarian selesai |
| **Transparency** | Tim SAR harus memahami logika keputusan robot |

**Jawaban:** (a) Search problem dengan state=posisi+coverage+waktu, (b) Utility-based search menggabungkan greedy navigation dengan optimization (SA/GA) dan heuristik probabilitas korban, (c) Utility-Based Agent yang menyeimbangkan coverage, deteksi, dan energi, (d) PEAS dengan partially observable, stochastic, sequential, dynamic environment, (e) Pertimbangan etis meliputi prioritasi korban, risk assessment, resource allocation, kewajiban komunikasi, dan transparency keputusan.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Sebutkan tiga teknik mitigasi bias algoritmik!

**Jawaban:**
1. **Pre-processing**: Re-sampling data untuk keseimbangan, penghapusan proxy variables
2. **In-processing**: Fairness constraints dalam training, adversarial debiasing
3. **Post-processing**: Kalibrasi output untuk equalize metrics antar grup

---

### Problem S2 ⭐⭐
**Soal:** Jelaskan mengapa "accuracy" saja bukan metrik yang cukup untuk mengevaluasi fairness sebuah model!

**Jawaban:** Accuracy mengukur keseluruhan tanpa mempertimbangkan distribusi error antar kelompok. Sebuah model bisa memiliki accuracy 90% keseluruhan, tetapi accuracy 95% untuk Grup A dan 70% untuk Grup B. Selain itu, distribusi false positive dan false negative yang tidak merata (seperti dalam kasus COMPAS) menyebabkan dampak diskriminatif yang tersembunyi oleh metrik accuracy keseluruhan.

---

### Problem S3 ⭐⭐
**Soal:** Bandingkan pendekatan regulasi AI berbasis risk (EU AI Act) dengan pendekatan berbasis principles (Singapura)! Apa kelebihan dan kekurangan masing-masing?

**Jawaban:**
- **Risk-based (EU)**: Kelebihan — aturan jelas per kategori, enforceable. Kekurangan — rigid, lambat beradaptasi, sulit mengklasifikasi AI baru.
- **Principles-based (SG)**: Kelebihan — fleksibel, adaptif, mendorong inovasi. Kekurangan — kurang enforceable, interpretasi subjektif, compliance sulit diukur.
Pendekatan ideal: hybrid yang menggabungkan prinsip umum dengan aturan spesifik untuk high-risk applications.

---

### Problem S4 ⭐⭐⭐
**Soal:** Rancang kerangka etika AI untuk sistem autonomous patrol drone TNI AU! Kerangka harus mencakup: prinsip-prinsip, governance structure, dan mekanisme review!

**Jawaban:**
**Prinsip:**
1. Meaningful human control — manusia selalu dalam rantai keputusan lethal
2. Proporsionalitas — respons sebanding ancaman
3. Accountability — chain of responsibility yang jelas
4. Transparency — keputusan AI harus explainable

**Governance Structure:**
- Dewan Etika AI (sipil + militer + akademisi)
- AI Safety Officer di setiap unit yang mengoperasikan drone
- Pelaporan langsung ke Inspector General

**Mekanisme Review:**
- Pre-deployment testing dengan skenario adversarial
- Post-mission review untuk setiap engagement
- Audit berkala oleh pihak independen
- Incident reporting dan lessons learned database

---

### Problem S5 ⭐⭐⭐
**Soal:** Untuk persiapan UAS, tuliskan langkah-langkah penyelesaian A* untuk graph berikut:

Start → A (cost 3, h=6), Start → B (cost 5, h=4). A → C (cost 2, h=3), A → D (cost 4, h=2). B → D (cost 1, h=2). C → Goal (cost 5, h=0). D → Goal (cost 3, h=0).

**Jawaban:**

| Step | Node | g(n) | h(n) | f(n) | Open List | Closed |
|------|------|------|------|------|-----------|--------|
| 1 | Start | 0 | 8 | 8 | {A(3+6=9), B(5+4=9)} | {Start} |
| 2 | A* | 3 | 6 | 9 | {B(9), C(5+3=8), D_A(7+2=9)} | {Start, A} |
| 3 | C | 5 | 3 | 8 | {B(9), D_A(9), Goal_C(10+0=10)} | {Start, A, C} |
| 4 | B | 5 | 4 | 9 | {D_A(9), D_B(6+2=8), Goal_C(10)} | {Start, A, C, B} |
| 5 | D_B | 6 | 2 | 8 | {D_A(9), Goal_C(10), Goal_D(9+0=9)} | {Start, A, C, B, D} |
| 6 | Goal_D | 9 | 0 | 9 | - | Goal reached |

*Tiebreaking: saat f sama, pilih node yang belum di-expand*

Path optimal: Start → B → D → Goal, cost = 5 + 1 + 3 = 9

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Bias Algoritmik** | Kecenderungan sistematis yang menghasilkan output diskriminatif |
| **Fairness** | Prinsip perlakuan adil; beberapa definisi formal yang sering berkonflik |
| **Transparency/XAI** | Kemampuan memahami dan menjelaskan keputusan AI |
| **Accountability** | Penentuan pihak bertanggung jawab atas keputusan AI |
| **Alignment Problem** | Memastikan tujuan AI selaras dengan nilai manusia |
| **Existential Risk** | Risiko AGI/ASI yang tidak terkontrol |
| **AI Security** | Perlindungan dari adversarial attacks, data poisoning, dll. |
| **Autonomous Weapons** | Sistem senjata dengan otonomi keputusan; meaningful human control penting |
| **Regulasi AI** | EU AI Act (risk-based), prinsip FEAT, dan kerangka regulasi lainnya |
| **AGI vs ANI** | Narrow AI (satu tugas) vs General AI (semua domain intelektual) |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 27-28** (Philosophy, Ethics, and Safety of AI).
2. Bostrom, N. (2014). *Superintelligence: Paths, Dangers, Strategies*. Oxford University Press.
3. European Commission. (2024). *EU Artificial Intelligence Act*. Official Journal of the EU.
4. UNESCO. (2021). *Recommendation on the Ethics of Artificial Intelligence*.
5. Chouldechova, A. (2017). Fair prediction with disparate impact: A study of bias in recidivism prediction instruments. *Big Data*, 5(2), 153-163.
6. Goodfellow, I.J. et al. (2015). Explaining and Harnessing Adversarial Examples. *ICLR 2015*.
7. Artikel dan laporan terkini tentang AI ethics dan AI safety.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
