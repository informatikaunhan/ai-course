# Latihan Pertemuan 11: Penalaran dengan Ketidakpastian - Probabilitas

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 11  
**Topik:** Penalaran dengan Ketidakpastian - Probabilitas  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Petunjuk Pengerjaan

1. Kerjakan semua soal secara mandiri
2. Waktu pengerjaan: 120 menit
3. Untuk soal pilihan ganda, pilih satu jawaban yang paling tepat
4. Untuk soal uraian, jawab dengan lengkap dan sistematis
5. Studi kasus memerlukan analisis mendalam dan penerapan konsep
6. Gunakan kalkulator untuk perhitungan probabilitas

---

## Bagian A: Soal Pilihan Ganda (20 Soal)

### Soal 1
Menurut Russell dan Norvig, dua sumber utama ketidakpastian dalam sistem AI adalah:

A. Hardware failure dan software bug  
B. Laziness dan ignorance  
C. Overfitting dan underfitting  
D. Bias dan variance  
E. Noise dan interference

---

### Soal 2
Keterbatasan logika proposisional berikut yang PALING berkaitan dengan ketidakpastian adalah:

A. Logika tidak mendukung variabel  
B. Logika hanya mengenal nilai TRUE atau FALSE  
C. Logika tidak mendukung fungsi  
D. Logika tidak dapat merepresentasikan kuantor  
E. Logika tidak mendukung rekursi

---

### Soal 3
Manakah yang merupakan aksioma Kolmogorov yang BENAR?

A. $0 \leq P(A) \leq \infty$  
B. $P(\Omega) = 0$  
C. $P(A \cup B) = P(A) + P(B)$ untuk A dan B yang saling lepas  
D. $P(A) + P(\neg A) = 0$  
E. $P(\emptyset) = 1$

---

### Soal 4
Jika $P(A) = 0.6$ dan $P(B) = 0.3$, serta A dan B saling lepas (mutually exclusive), maka $P(A \cup B)$ adalah:

A. 0.18  
B. 0.72  
C. 0.90  
D. 0.30  
E. 0.60

---

### Soal 5
Probabilitas bersyarat $P(A \mid B)$ didefinisikan sebagai:

A. $P(A) \times P(B)$  
B. $P(A) + P(B)$  
C. $P(A, B) / P(B)$  
D. $P(A, B) / P(A)$  
E. $P(A) / P(B)$

---

### Soal 6
Dalam Teorema Bayes $P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)}$, komponen $P(E \mid H)$ disebut:

A. Prior  
B. Posterior  
C. Evidence  
D. Likelihood  
E. Marginal

---

### Soal 7
Jika prior probability sebuah penyakit adalah 2%, tes memiliki true positive rate 90% dan false positive rate 8%, berapa probabilitas seseorang benar-benar sakit jika tes positif?

A. 90.0%  
B. 18.7%  
C. 2.0%  
D. 8.0%  
E. 50.0%

---

### Soal 8
Base rate fallacy terjadi ketika seseorang:

A. Tidak memahami aturan produk  
B. Mengabaikan prior probability dan terlalu fokus pada likelihood  
C. Mengalikan dua probabilitas yang tidak independen  
D. Menggunakan hukum total probability secara salah  
E. Tidak melakukan normalisasi

---

### Soal 9
Dalam Bayesian updating, posterior dari observasi pertama menjadi:

A. Likelihood untuk observasi kedua  
B. Evidence untuk observasi kedua  
C. Prior untuk observasi kedua  
D. Marginal probability  
E. Joint probability

---

### Soal 10
Normalisasi dalam inferensi probabilistik berfungsi untuk:

A. Mengubah distribusi menjadi normal/Gaussian  
B. Menghilangkan outlier  
C. Memastikan semua probabilitas berjumlah 1  
D. Mengurangi dimensi data  
E. Mengubah skala variabel

---

### Soal 11
Dua event A dan B dikatakan independen jika:

A. $P(A \cup B) = P(A) + P(B)$  
B. $P(A, B) = P(A) \cdot P(B)$  
C. $P(A \mid B) = P(B)$  
D. $P(A) + P(B) = 1$  
E. $P(A, B) = 0$

---

### Soal 12
Sensor A memiliki detection probability 0.80 dan sensor B memiliki detection probability 0.75. Jika kedua sensor independen, probabilitas KEDUANYA gagal mendeteksi target adalah:

A. 0.05  
B. 0.95  
C. 0.60  
D. 0.20  
E. 0.40

---

### Soal 13
Naive Bayes classifier mengasumsikan bahwa:

A. Semua fitur memiliki distribusi Gaussian  
B. Semua kelas memiliki probabilitas prior yang sama  
C. Semua fitur independen satu sama lain diberikan kelas  
D. Jumlah fitur harus genap  
E. Data training harus seimbang

---

### Soal 14
Laplace smoothing (additive smoothing) digunakan dalam Naive Bayes untuk mengatasi masalah:

A. Overfitting  
B. Missing values  
C. Zero probability pada fitur yang belum muncul  
D. High dimensionality  
E. Class imbalance

---

### Soal 15
Dengan Laplace smoothing ($\alpha = 1$), jika sebuah kata muncul 0 kali di kelas Spam dari 50 dokumen spam, dan vocabulary size = 100, maka estimasi probabilitasnya adalah:

A. 0  
B. 1/100  
C. 1/50  
D. 1/150  
E. 1/200

---

### Soal 16
Hukum Probabilitas Total menyatakan bahwa:

A. $P(E) = P(E \mid H) + P(E \mid \neg H)$  
B. $P(E) = P(E \mid H) \cdot P(H) + P(E \mid \neg H) \cdot P(\neg H)$  
C. $P(E) = P(H) + P(\neg H)$  
D. $P(E) = P(E, H) - P(E, \neg H)$  
E. $P(E) = 1 - P(\neg E)$

---

### Soal 17
Manakah pernyataan yang BENAR tentang perbedaan independensi dan independensi bersyarat?

A. Independensi selalu menyiratkan independensi bersyarat  
B. Independensi bersyarat selalu menyiratkan independensi  
C. Keduanya adalah konsep yang identik  
D. Kedua konsep tidak saling menyiratkan  
E. Independensi bersyarat hanya berlaku untuk event kontinu

---

### Soal 18
Dalam konteks pertahanan, manakah skenario yang PALING tepat menggambarkan conditional independence?

A. Cuaca di Jakarta dan cuaca di Surabaya  
B. Dua sensor radar yang mendeteksi target yang sama secara terpisah, di mana noise masing-masing sensor bersifat independen  
C. Jumlah peluru dan jumlah senapan di gudang senjata  
D. Waktu keberangkatan kapal dan waktu kedatangan kapal  
E. Tinggi badan dan berat badan tentara

---

### Soal 19
Jika $P(A) = 0.4$, $P(B \mid A) = 0.5$, dan $P(B \mid \neg A) = 0.2$, berapakah $P(B)$?

A. 0.20  
B. 0.32  
C. 0.50  
D. 0.70  
E. 0.12

---

### Soal 20
Keuntungan utama pendekatan probabilistik dibandingkan logika murni untuk penalaran dalam AI adalah:

A. Lebih cepat secara komputasional  
B. Tidak memerlukan data training  
C. Dapat merepresentasikan dan mengelola ketidakpastian secara kuantitatif  
D. Tidak memerlukan prior knowledge  
E. Selalu menghasilkan jawaban yang pasti benar

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara laziness dan ignorance sebagai sumber ketidakpastian! Berikan satu contoh masing-masing dari domain pertahanan!

---

### Soal 2 ⭐
Sebutkan empat keterbatasan logika proposisional dalam menangani ketidakpastian dan jelaskan secara singkat masing-masing!

---

### Soal 3 ⭐
Jelaskan perbedaan antara prior probability, likelihood, dan posterior probability dalam konteks Teorema Bayes! Berikan satu contoh yang mengilustrasikan ketiga komponen tersebut!

---

### Soal 4 ⭐
Sebuah pos jaga memiliki dua lampu peringatan: Lampu A menyala dengan probabilitas 0.15 dan Lampu B menyala dengan probabilitas 0.10. Jika kedua lampu independen, hitung: (a) probabilitas keduanya menyala, (b) probabilitas setidaknya satu lampu menyala!

---

### Soal 5 ⭐⭐
Sebuah gudang amunisi dijaga oleh sensor panas. Data historis menunjukkan:
- Probabilitas kebakaran sesungguhnya: P(Kebakaran) = 0.005
- Sensor mendeteksi jika memang ada kebakaran: P(Alarm | Kebakaran) = 0.98
- Sensor memberi alarm palsu: P(Alarm | ¬Kebakaran) = 0.04

Hitung probabilitas kebakaran sesungguhnya jika alarm berbunyi! Jelaskan setiap langkah!

---

### Soal 6 ⭐⭐
Jelaskan apa yang dimaksud dengan base rate fallacy! Mengapa fenomena ini berbahaya dalam konteks sistem peringatan dini militer? Berikan contoh numerik sederhana!

---

### Soal 7 ⭐⭐
Melanjutkan Soal 5, jika alarm berbunyi dua kali berturut-turut (deteksi independen), hitung probabilitas kebakaran sesungguhnya setelah alarm kedua! Gunakan Bayesian updating!

---

### Soal 8 ⭐⭐
Dua intel lapangan memberikan laporan independen tentang keberadaan kamp musuh:
- Intel A melaporkan "ada kamp" (akurasi: 80%)
- Intel B melaporkan "tidak ada kamp" (akurasi: 85%)
- Prior probability keberadaan kamp: 0.25

Hitung posterior probability keberadaan kamp setelah menerima kedua laporan!

---

### Soal 9 ⭐⭐
Jelaskan perbedaan antara independence dan conditional independence! Berikan contoh di mana dua variabel yang TIDAK independen menjadi conditionally independent given variabel ketiga!

---

### Soal 10 ⭐⭐
Tiga kapal memasuki wilayah perairan Indonesia dengan prior probability sebagai berikut: kapal dagang (70%), kapal penangkap ikan (20%), kapal mencurigakan (10%). Sistem sensor mendeteksi pola pergerakan tertentu dengan likelihood:
- P(pola | dagang) = 0.10
- P(pola | ikan) = 0.30
- P(pola | mencurigakan) = 0.80

Gunakan normalisasi untuk menghitung posterior probability masing-masing hipotesis!

---

### Soal 11 ⭐⭐
Jelaskan mengapa Naive Bayes disebut "naive"! Berikan contoh di mana asumsi independensi bersyarat sangat dilanggar, dan jelaskan mengapa Naive Bayes sering tetap bekerja dengan baik meskipun asumsi ini dilanggar!

---

### Soal 12 ⭐⭐⭐
Sebuah sistem klasifikasi email militer menggunakan Naive Bayes dengan data training berikut:

| Kata | Muncul di "Rahasia" (20 email) | Muncul di "Biasa" (80 email) |
|------|:-----:|:-----:|
| "operasi" | 15 | 10 |
| "koordinat" | 12 | 3 |
| "cuaca" | 4 | 25 |

Sebuah email baru mengandung kata "operasi" dan "koordinat" tetapi tidak "cuaca". Klasifikasikan email tersebut menggunakan Naive Bayes dengan Laplace smoothing ($\alpha = 1$)! Tunjukkan semua langkah!

---

### Soal 13 ⭐⭐⭐
Sebuah stasiun radar memiliki tiga mode operasi: Mode A (jarak jauh, akurasi rendah), Mode B (jarak menengah, akurasi sedang), Mode C (jarak dekat, akurasi tinggi). Buatkan expected utility analysis untuk memilih mode terbaik jika:

| Mode | P(Deteksi) | P(False Alarm) | Biaya Operasi | Cakupan Area |
|------|:-----:|:-----:|:-----:|:-----:|
| A | 0.60 | 0.15 | Rendah (10) | Luas (90) |
| B | 0.80 | 0.08 | Sedang (30) | Sedang (60) |
| C | 0.95 | 0.02 | Tinggi (60) | Sempit (30) |

Definisikan utility function yang mempertimbangkan keempat faktor, tentukan bobot yang wajar, dan pilih mode terbaik!

---

### Soal 14 ⭐⭐⭐
Buktikan bahwa untuk dua evidence $E_1$ dan $E_2$ yang conditionally independent given $H$, berlaku:

$$P(H \mid E_1, E_2) = \frac{P(E_1 \mid H) \cdot P(E_2 \mid H) \cdot P(H)}{P(E_1, E_2)}$$

Mulai dari definisi probabilitas bersyarat dan tunjukkan setiap langkah derivasi!

---

### Soal 15 ⭐⭐⭐
Sebuah sistem pendeteksi torpedo memiliki dua sensor sonar independen. Sensor 1 memiliki true positive rate 0.85 dan false positive rate 0.06. Sensor 2 memiliki true positive rate 0.90 dan false positive rate 0.04. Prior probability torpedo = 0.03.

(a) Hitung posterior probability torpedo jika hanya Sensor 1 memberikan alarm  
(b) Hitung posterior probability torpedo jika kedua sensor memberikan alarm  
(c) Hitung posterior probability torpedo jika Sensor 1 alarm tetapi Sensor 2 tidak  
(d) Bandingkan ketiga skenario dan jelaskan implikasinya untuk pengambilan keputusan!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Deteksi Ancaman Maritim Multi-Sensor

**Latar Belakang:**

TNI Angkatan Laut mengoperasikan Pusat Komando dan Pengendalian Maritim yang memonitor lalu lintas kapal di Selat Malaka. Sistem menggunakan tiga sumber informasi untuk mengklasifikasikan kapal yang memasuki zona pengawasan:

1. **Radar pantai**: Mendeteksi ukuran dan kecepatan kapal
2. **AIS (Automatic Identification System)**: Menerima sinyal identifikasi dari kapal
3. **Citra satelit**: Memberikan informasi visual tentang jenis kapal

Terdapat empat kategori kapal:
- **Kapal Dagang** (prior = 0.60): Kapal kargo, tanker, container ship
- **Kapal Ikan** (prior = 0.25): Kapal penangkap ikan lokal dan asing
- **Kapal Patroli Asing** (prior = 0.10): Kapal angkatan laut negara lain
- **Kapal Mencurigakan** (prior = 0.05): Kapal penyelundup, illegal fishing berskala besar

Data likelihood dari masing-masing sensor:

**Sensor 1 — Radar (Pola kecepatan tinggi terdeteksi):**

| Hipotesis | P(kecepatan tinggi | H) |
|-----------|:-----:|
| Kapal Dagang | 0.10 |
| Kapal Ikan | 0.05 |
| Kapal Patroli Asing | 0.70 |
| Kapal Mencurigakan | 0.60 |

**Sensor 2 — AIS (Sinyal AIS TIDAK diterima):**

| Hipotesis | P(tanpa AIS | H) |
|-----------|:-----:|
| Kapal Dagang | 0.05 |
| Kapal Ikan | 0.40 |
| Kapal Patroli Asing | 0.30 |
| Kapal Mencurigakan | 0.85 |

**Sensor 3 — Satelit (Pola visual mencurigakan):**

| Hipotesis | P(visual mencurigakan | H) |
|-----------|:-----:|
| Kapal Dagang | 0.03 |
| Kapal Ikan | 0.08 |
| Kapal Patroli Asing | 0.25 |
| Kapal Mencurigakan | 0.90 |

**Asumsi:** Ketiga sensor bersifat conditionally independent given kategori kapal.

**Pertanyaan:**

**1a.** Hitung posterior probability setiap kategori kapal jika hanya Sensor 1 (radar) mendeteksi pola kecepatan tinggi! Gunakan normalisasi. (15 poin)

**1b.** Sebuah kapal terdeteksi dengan kecepatan tinggi (Sensor 1) DAN tanpa sinyal AIS (Sensor 2). Hitung posterior probability setiap kategori menggunakan kedua bukti secara simultan! (20 poin)

**1c.** Kapal yang sama kemudian dianalisis citra satelitnya dan menunjukkan pola visual mencurigakan (Sensor 3). Perbarui posterior dari hasil 1b menggunakan Bayesian updating! (15 poin)

**1d.** Bandingkan bagaimana posterior berubah dari prior → setelah 1 sensor → setelah 2 sensor → setelah 3 sensor untuk kategori "Kapal Mencurigakan". Apa insight yang dapat diambil tentang sensor fusion? (10 poin)

**1e.** Jika komandan harus memutuskan apakah akan mengirim kapal patroli untuk intercept (biaya tinggi, waktu terbatas), pada level posterior berapa untuk "Kapal Mencurigakan" keputusan intercept sebaiknya diambil? Rancang threshold decision rule yang mempertimbangkan trade-off antara false positive (membuang resource) dan false negative (melewatkan ancaman nyata)! (10 poin)

---

### Studi Kasus 2: Sistem Klasifikasi Sinyal SIGINT untuk Keamanan Nasional

**Latar Belakang:**

Badan Intelijen Sinyal (unit SIGINT) memantau spektrum frekuensi radio di wilayah perbatasan. Sistem harus mengklasifikasikan sinyal yang terdeteksi ke dalam kategori untuk menentukan prioritas tindakan.

**Kategori Sinyal:**
- **Komunikasi Militer Asing** ($H_1$, prior = 0.08): Sinyal enkripsi tingkat tinggi dari kekuatan militer asing
- **Komunikasi Sipil** ($H_2$, prior = 0.65): Radio sipil, telepon satelit, komunikasi komersial
- **Navigasi/Cuaca** ($H_3$, prior = 0.15): Sinyal navigasi, data meteorologi, beacon
- **Sinyal Mencurigakan** ($H_4$, prior = 0.07): Pola tidak teridentifikasi, potensi spionase
- **Noise/Interferensi** ($H_5$, prior = 0.05): Noise atmosferik, interferensi peralatan

**Fitur yang Diamati:**

Sistem mengekstrak tiga fitur dari setiap sinyal:
- $F_1$: Pola enkripsi terdeteksi (ya/tidak)
- $F_2$: Frekuensi berada di band militer (ya/tidak)
- $F_3$: Sinyal bersifat burst (pendek, terjadwal) vs kontinu

**Data Training (200 sinyal yang sudah diverifikasi):**

| Fitur | $H_1$ (16 sinyal) | $H_2$ (130 sinyal) | $H_3$ (30 sinyal) | $H_4$ (14 sinyal) | $H_5$ (10 sinyal) |
|-------|:-----:|:-----:|:-----:|:-----:|:-----:|
| $F_1$ = ya | 14 | 5 | 0 | 10 | 0 |
| $F_2$ = ya | 15 | 8 | 3 | 9 | 1 |
| $F_3$ = burst | 12 | 15 | 2 | 11 | 2 |

**Pertanyaan:**

**2a.** Hitung semua conditional probability $P(F_i \mid H_j)$ yang diperlukan menggunakan Laplace smoothing ($\alpha = 1$)! Sajikan dalam tabel terorganisir. (15 poin)

**2b.** Sebuah sinyal baru terdeteksi dengan fitur: enkripsi terdeteksi ($F_1$ = ya), di band militer ($F_2$ = ya), bersifat burst ($F_3$ = burst). Klasifikasikan sinyal ini menggunakan Naive Bayes! Tunjukkan semua langkah perhitungan dan tentukan kategori paling probable! (20 poin)

**2c.** Sinyal kedua terdeteksi dengan fitur: tidak ada enkripsi ($F_1$ = tidak), di band militer ($F_2$ = ya), kontinu ($F_3$ = tidak burst). Klasifikasikan sinyal ini! (15 poin)

**2d.** Analis intelijen merasa bahwa fitur $F_1$ (enkripsi) dan $F_2$ (band militer) sangat berkorelasi untuk sinyal militer asing — sinyal militer yang terenkripsi hampir selalu berada di band militer. Jelaskan bagaimana pelanggaran asumsi Naive Bayes ini mempengaruhi hasil klasifikasi! Apakah overestimate atau underestimate probabilitas $H_1$? (10 poin)

**2e.** Rancang sistem prioritas response berdasarkan posterior probability! Definisikan empat level prioritas (KRITIS, TINGGI, SEDANG, RENDAH) dengan threshold probability dan tindakan yang sesuai untuk masing-masing level. Pertimbangkan bahwa kesalahan mengabaikan sinyal militer asing ($H_1$) atau sinyal mencurigakan ($H_4$) jauh lebih berbahaya daripada false alarm! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **B** | Russell dan Norvig mengidentifikasi laziness (terlalu sulit mendaftar semua aturan) dan ignorance (informasi tidak tersedia) sebagai dua sumber utama ketidakpastian |
| 2 | **B** | Logika proposisional bersifat biner (TRUE/FALSE) tanpa nilai antara, sehingga tidak dapat merepresentasikan derajat kepercayaan |
| 3 | **C** | Aksioma ketiga Kolmogorov: untuk event yang saling lepas (mutually exclusive), $P(A \cup B) = P(A) + P(B)$ |
| 4 | **C** | Untuk event saling lepas: $P(A \cup B) = P(A) + P(B) = 0.6 + 0.3 = 0.9$ |
| 5 | **C** | Definisi probabilitas bersyarat: $P(A \mid B) = P(A, B) / P(B)$ |
| 6 | **D** | $P(E \mid H)$ adalah likelihood, yaitu probabilitas bukti muncul jika hipotesis benar |
| 7 | **B** | $P(H \mid E) = \frac{0.90 \times 0.02}{0.90 \times 0.02 + 0.08 \times 0.98} = \frac{0.018}{0.018 + 0.0784} = \frac{0.018}{0.0964} = 0.1867$ atau 18.7% |
| 8 | **B** | Base rate fallacy terjadi ketika seseorang mengabaikan prior probability (base rate) dan terlalu fokus pada likelihood/hit rate |
| 9 | **C** | Dalam Bayesian updating, posterior dari observasi sebelumnya menjadi prior untuk observasi berikutnya |
| 10 | **C** | Normalisasi memastikan distribusi posterior berjumlah 1, sehingga merupakan distribusi probabilitas yang valid |
| 11 | **B** | Dua event independen jika dan hanya jika $P(A, B) = P(A) \cdot P(B)$ |
| 12 | **A** | $P(\text{keduanya gagal}) = P(\neg A) \cdot P(\neg B) = (1-0.80)(1-0.75) = 0.20 \times 0.25 = 0.05$ |
| 13 | **C** | Asumsi utama Naive Bayes: semua fitur conditionally independent given kelas |
| 14 | **C** | Laplace smoothing menambahkan pseudocount untuk menghindari probabilitas nol pada fitur yang belum muncul di training data |
| 15 | **D** | Dengan Laplace: $\frac{0 + 1}{50 + 100} = \frac{1}{150}$ |
| 16 | **B** | Hukum probabilitas total: $P(E) = P(E \mid H) \cdot P(H) + P(E \mid \neg H) \cdot P(\neg H)$ |
| 17 | **D** | Independensi dan independensi bersyarat adalah konsep yang berbeda dan tidak saling menyiratkan |
| 18 | **B** | Dua sensor radar mendeteksi target yang sama secara terpisah; noise mereka independen given keberadaan target (conditional independence) |
| 19 | **B** | $P(B) = P(B \mid A) \cdot P(A) + P(B \mid \neg A) \cdot P(\neg A) = 0.5 \times 0.4 + 0.2 \times 0.6 = 0.20 + 0.12 = 0.32$ |
| 20 | **C** | Keuntungan utama probabilitas: dapat merepresentasikan derajat kepercayaan secara kuantitatif (bukan hanya benar/salah) |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Laziness (Kemalasan):**
- Definisi: Terlalu sulit, mahal, atau tidak praktis untuk mendaftarkan semua aturan, pengecualian, dan kondisi
- Contoh pertahanan: Aturan identifikasi friend-or-foe (IFF) tidak dapat mendaftar semua kemungkinan pola terbang, formasi, dan sinyal dari seluruh jenis pesawat militer dan sipil di dunia

**Ignorance (Ketidaktahuan):**
- Definisi: Informasi yang diperlukan memang tidak tersedia atau belum diketahui
- Contoh pertahanan: Kemampuan sebenarnya dari sistem pertahanan udara musuh tidak diketahui karena merupakan informasi rahasia — agen AI tidak dapat mengetahui probabilitas intercept yang sebenarnya

**Perbedaan utama:** Laziness adalah masalah representasi (informasi ada tapi terlalu banyak untuk dimasukkan), sedangkan ignorance adalah masalah fundamental (informasi memang tidak ada).

---

#### Jawaban Soal 2 ⭐

Empat keterbatasan logika proposisional dalam menangani ketidakpastian:

1. **Biner (Binary):** Logika hanya mengenal TRUE atau FALSE, tidak ada nilai "mungkin" atau "kemungkinan besar". Contoh: Tidak bisa menyatakan "kemungkinan 70% ini pesawat musuh"

2. **Monotonic:** Menambah informasi baru tidak pernah membatalkan kesimpulan lama. Dalam dunia nyata, bukti baru bisa mengubah atau membatalkan kesimpulan sebelumnya

3. **Closed-World Assumption:** Apa yang tidak diketahui dianggap salah. Contoh: Jika tidak ada data tentang kapal selam, logika menyimpulkan tidak ada kapal selam

4. **Qualification Problem:** Tidak mungkin mendaftarkan semua prasyarat untuk sebuah aturan. Contoh: Aturan "jika sinyal radar maka ada pesawat" memiliki banyak pengecualian (burung, cuaca, jamming)

---

#### Jawaban Soal 3 ⭐

**Prior Probability $P(H)$:**
- Probabilitas hipotesis sebelum mengamati bukti baru
- Mencerminkan pengetahuan awal atau data historis
- Contoh: P(Serangan) = 0.02 berdasarkan frekuensi historis serangan

**Likelihood $P(E \mid H)$:**
- Probabilitas bukti muncul jika hipotesis benar
- Mengukur seberapa cocok bukti dengan hipotesis
- Contoh: P(Alarm | Serangan) = 0.95 — jika memang ada serangan, alarm berbunyi 95% kali

**Posterior Probability $P(H \mid E)$:**
- Probabilitas hipotesis setelah mengamati bukti
- Hasil akhir dari Teorema Bayes
- Contoh: P(Serangan | Alarm) = ? — inilah yang ingin kita hitung

**Hubungan:** Prior adalah "kepercayaan awal", likelihood mengukur "kekuatan bukti", dan posterior adalah "kepercayaan yang diperbarui setelah melihat bukti".

---

#### Jawaban Soal 4 ⭐

**Diketahui:**
- P(A) = 0.15, P(B) = 0.10
- A dan B independen

**(a) Probabilitas keduanya menyala:**

$$P(A \cap B) = P(A) \times P(B) = 0.15 \times 0.10 = 0.015$$

Probabilitas keduanya menyala: **1.5%**

**(b) Probabilitas setidaknya satu menyala:**

$$P(A \cup B) = P(A) + P(B) - P(A \cap B) = 0.15 + 0.10 - 0.015 = 0.235$$

Probabilitas setidaknya satu menyala: **23.5%**

*Cara alternatif:* $P(\text{setidaknya satu}) = 1 - P(\text{tidak ada}) = 1 - (1-0.15)(1-0.10) = 1 - 0.85 \times 0.90 = 1 - 0.765 = 0.235$

---

#### Jawaban Soal 5 ⭐⭐

**Diketahui:**
- P(Kebakaran) = 0.005
- P(Alarm | Kebakaran) = 0.98
- P(Alarm | ¬Kebakaran) = 0.04

**Step 1: Hitung P(Alarm) menggunakan Total Probability**

$$P(\text{Alarm}) = P(\text{Alarm} \mid \text{Kebakaran}) \times P(\text{Kebakaran}) + P(\text{Alarm} \mid \neg\text{Kebakaran}) \times P(\neg\text{Kebakaran})$$
$$= 0.98 \times 0.005 + 0.04 \times 0.995$$
$$= 0.0049 + 0.0398 = 0.0447$$

**Step 2: Terapkan Teorema Bayes**

$$P(\text{Kebakaran} \mid \text{Alarm}) = \frac{P(\text{Alarm} \mid \text{Kebakaran}) \times P(\text{Kebakaran})}{P(\text{Alarm})}$$
$$= \frac{0.98 \times 0.005}{0.0447} = \frac{0.0049}{0.0447} = 0.1096$$

**Jawaban:** Probabilitas kebakaran sesungguhnya jika alarm berbunyi adalah **10.96%** (sekitar 11%).

**Interpretasi:** Meskipun sensor memiliki true positive rate tinggi (98%), karena prior kebakaran sangat rendah (0.5%), sebagian besar alarm adalah false alarm. Ini adalah contoh klasik base rate effect.

---

#### Jawaban Soal 6 ⭐⭐

**Base Rate Fallacy:**
Kesalahan penalaran di mana seseorang mengabaikan probabilitas dasar (prior/base rate) dan terlalu fokus pada likelihood atau hit rate dari suatu bukti.

**Mengapa berbahaya dalam konteks militer:**
Dalam sistem peringatan dini, jika operator hanya fokus pada "sensor detection rate 95%" tanpa mempertimbangkan bahwa serangan sebenarnya sangat jarang terjadi (misalnya prior 0.1%), maka:
- Operator mungkin memperlakukan setiap alarm sebagai ancaman nyata
- Padahal sebagian besar alarm adalah false alarm
- Hal ini menyebabkan alert fatigue (kelelahan merespons alarm)
- Atau sebaliknya, overreaction yang membuang sumber daya

**Contoh numerik:**
- Prior serangan: P(Serangan) = 0.001 (1 dari 1000 hari)
- Detection rate: P(Alarm | Serangan) = 0.95
- False alarm rate: P(Alarm | ¬Serangan) = 0.05

$$P(\text{Serangan} \mid \text{Alarm}) = \frac{0.95 \times 0.001}{0.95 \times 0.001 + 0.05 \times 0.999} = \frac{0.00095}{0.00095 + 0.04995} = \frac{0.00095}{0.05090} = 0.0187$$

Meskipun sensor 95% akurat, hanya **1.87%** dari alarm yang benar-benar menunjukkan serangan! Operator yang mengabaikan base rate dan berasumsi 95% alarm adalah nyata akan membuat kesalahan fatal.

---

#### Jawaban Soal 7 ⭐⭐

**Bayesian Updating — Alarm Kedua:**

**Step 1: Hasil dari Soal 5 menjadi prior baru**
- Prior baru: P(Kebakaran) = 0.1096 (hasil alarm pertama)
- P(¬Kebakaran) = 1 - 0.1096 = 0.8904

**Step 2: Hitung P(Alarm₂) dengan prior baru**

$$P(\text{Alarm}_2) = P(\text{Alarm} \mid \text{Keb}) \times P(\text{Keb}) + P(\text{Alarm} \mid \neg\text{Keb}) \times P(\neg\text{Keb})$$
$$= 0.98 \times 0.1096 + 0.04 \times 0.8904$$
$$= 0.1074 + 0.0356 = 0.1430$$

**Step 3: Terapkan Bayes**

$$P(\text{Kebakaran} \mid \text{Alarm}_1, \text{Alarm}_2) = \frac{0.98 \times 0.1096}{0.1430} = \frac{0.1074}{0.1430} = 0.7510$$

**Jawaban:** Setelah alarm kedua, probabilitas kebakaran meningkat dari **10.96%** menjadi **75.10%**.

**Insight:** Bayesian updating menunjukkan bahwa bukti berulang secara dramatis mengubah posterior — dari 0.5% (prior awal) → 10.96% (setelah alarm 1) → 75.10% (setelah alarm 2).

---

#### Jawaban Soal 8 ⭐⭐

**Diketahui:**
- P(Kamp) = 0.25, P(¬Kamp) = 0.75
- Intel A: "ada kamp" dengan akurasi 80% → P(A=ada | Kamp) = 0.80, P(A=ada | ¬Kamp) = 0.20
- Intel B: "tidak ada kamp" dengan akurasi 85% → P(B=tidak | ¬Kamp) = 0.85, P(B=tidak | Kamp) = 0.15

**Step 1: Hitung likelihood gabungan (kedua laporan independen)**

$$P(A\text{=ada}, B\text{=tidak} \mid \text{Kamp}) = P(A\text{=ada} \mid \text{Kamp}) \times P(B\text{=tidak} \mid \text{Kamp})$$
$$= 0.80 \times 0.15 = 0.12$$

$$P(A\text{=ada}, B\text{=tidak} \mid \neg\text{Kamp}) = P(A\text{=ada} \mid \neg\text{Kamp}) \times P(B\text{=tidak} \mid \neg\text{Kamp})$$
$$= 0.20 \times 0.85 = 0.17$$

**Step 2: Hitung unnormalized posterior**

$$P(\text{Kamp}) \times P(\text{bukti} \mid \text{Kamp}) = 0.25 \times 0.12 = 0.030$$
$$P(\neg\text{Kamp}) \times P(\text{bukti} \mid \neg\text{Kamp}) = 0.75 \times 0.17 = 0.1275$$

**Step 3: Normalisasi**

$$\alpha = 0.030 + 0.1275 = 0.1575$$

$$P(\text{Kamp} \mid \text{bukti}) = \frac{0.030}{0.1575} = 0.1905$$

**Jawaban:** Posterior probability keberadaan kamp: **19.05%**

Posterior turun dari prior 25% menjadi 19.05% karena laporan negatif dari Intel B (yang akurasinya lebih tinggi, 85%) lebih kuat pengaruhnya daripada laporan positif dari Intel A (akurasi 80%).

---

#### Jawaban Soal 9 ⭐⭐

**Independence:**
- Dua event A dan B independen jika: $P(A, B) = P(A) \cdot P(B)$
- Mengetahui A tidak memberikan informasi tentang B
- Contoh: Hasil lemparan dadu pertama dan kedua

**Conditional Independence:**
- A dan B conditionally independent given C jika: $P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$
- Given C, mengetahui A tidak memberikan informasi tambahan tentang B
- Notasi: $A \perp B \mid C$

**Contoh variabel yang TIDAK independen tetapi conditionally independent:**

Misalkan:
- $A$ = Hasil tes darah pasien
- $B$ = Hasil X-ray pasien
- $C$ = Penyakit pasien (misalnya pneumonia)

$A$ dan $B$ TIDAK independen: Jika tes darah abnormal, kemungkinan X-ray juga abnormal (keduanya dipengaruhi penyakit).

$A$ dan $B$ conditionally independent GIVEN $C$: Jika kita sudah tahu pasien memiliki pneumonia, hasil tes darah tidak memberikan informasi tambahan tentang X-ray. Masing-masing hanya bergantung pada penyakit, bukan satu sama lain.

---

#### Jawaban Soal 10 ⭐⭐

**Diketahui:**
- P(Dagang) = 0.70, P(Ikan) = 0.20, P(Mencurigakan) = 0.10
- Likelihood: P(pola | Dagang) = 0.10, P(pola | Ikan) = 0.30, P(pola | Mencurigakan) = 0.80

**Step 1: Hitung unnormalized posterior**

$$P'(\text{Dagang}) = P(\text{pola} \mid \text{Dagang}) \times P(\text{Dagang}) = 0.10 \times 0.70 = 0.070$$
$$P'(\text{Ikan}) = P(\text{pola} \mid \text{Ikan}) \times P(\text{Ikan}) = 0.30 \times 0.20 = 0.060$$
$$P'(\text{Mencurigakan}) = P(\text{pola} \mid \text{Mencurigakan}) \times P(\text{Mencurigakan}) = 0.80 \times 0.10 = 0.080$$

**Step 2: Hitung konstanta normalisasi**

$$\alpha = 0.070 + 0.060 + 0.080 = 0.210$$

**Step 3: Normalisasi**

$$P(\text{Dagang} \mid \text{pola}) = \frac{0.070}{0.210} = 0.3333 \text{ (33.3%)}$$
$$P(\text{Ikan} \mid \text{pola}) = \frac{0.060}{0.210} = 0.2857 \text{ (28.6%)}$$
$$P(\text{Mencurigakan} \mid \text{pola}) = \frac{0.080}{0.210} = 0.3810 \text{ (38.1%)}$$

**Verifikasi:** 0.3333 + 0.2857 + 0.3810 = 1.0 ✓

**Jawaban:** Setelah mengamati pola pergerakan, kapal mencurigakan menjadi hipotesis paling probable (38.1%), meningkat signifikan dari prior 10%. Kapal dagang turun dari 70% ke 33.3%.

---

#### Jawaban Soal 11 ⭐⭐

**Mengapa disebut "Naive":**
Naive Bayes mengasumsikan bahwa semua fitur conditionally independent given kelas. Artinya, mengetahui nilai satu fitur tidak memberikan informasi tentang fitur lain jika kelas sudah diketahui. Asumsi ini hampir selalu dilanggar di dunia nyata, sehingga disebut "naive" (naif/sederhana).

**Contoh pelanggaran asumsi:**
Dalam deteksi spam email, fitur "gratis" dan "diskon" sangat berkorelasi — email yang mengandung "gratis" sangat mungkin juga mengandung "diskon". Naive Bayes menganggap keduanya independen dan menghitung:

$$P(\text{Spam} \mid \text{"gratis"}, \text{"diskon"}) \propto P(\text{"gratis"} \mid \text{Spam}) \times P(\text{"diskon"} \mid \text{Spam}) \times P(\text{Spam})$$

Ini meng-overcount bukti spam karena menghitung kedua kata sebagai bukti independen, padahal keduanya muncul bersama.

**Mengapa tetap bekerja baik:**
1. **Klasifikasi hanya butuh ranking:** Yang penting bukan probabilitas yang tepat, tetapi kelas mana yang probabilitasnya paling tinggi. Meskipun estimasi probabilitas salah, ranking sering tetap benar.
2. **Overestimate dan underestimate saling cancel out:** Error pada satu fitur sering dikompensasi oleh error pada fitur lain.
3. **Decision boundary masih baik:** Meskipun probabilitas absolut salah, batas keputusan sering masih mendekati optimal.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Diketahui:**
- P(Rahasia) = 20/100 = 0.20, P(Biasa) = 80/100 = 0.80
- Email baru: "operasi" = ya, "koordinat" = ya, "cuaca" = tidak
- Laplace smoothing α = 1, vocabulary size k = 2 (ya/tidak per fitur)

**Step 1: Hitung P(fitur | kelas) dengan Laplace smoothing**

Untuk kelas Rahasia (20 email), $k = 2$:

$$P(\text{"operasi"=ya} \mid \text{Rahasia}) = \frac{15 + 1}{20 + 2} = \frac{16}{22} = 0.7273$$
$$P(\text{"koordinat"=ya} \mid \text{Rahasia}) = \frac{12 + 1}{20 + 2} = \frac{13}{22} = 0.5909$$
$$P(\text{"cuaca"=tidak} \mid \text{Rahasia}) = \frac{(20-4) + 1}{20 + 2} = \frac{17}{22} = 0.7727$$

Untuk kelas Biasa (80 email):

$$P(\text{"operasi"=ya} \mid \text{Biasa}) = \frac{10 + 1}{80 + 2} = \frac{11}{82} = 0.1341$$
$$P(\text{"koordinat"=ya} \mid \text{Biasa}) = \frac{3 + 1}{80 + 2} = \frac{4}{82} = 0.0488$$
$$P(\text{"cuaca"=tidak} \mid \text{Biasa}) = \frac{(80-25) + 1}{80 + 2} = \frac{56}{82} = 0.6829$$

**Step 2: Hitung skor Naive Bayes (unnormalized)**

$$\text{Score(Rahasia)} = P(\text{Rahasia}) \times \prod P(f_i \mid \text{Rahasia})$$
$$= 0.20 \times 0.7273 \times 0.5909 \times 0.7727$$
$$= 0.20 \times 0.3322 = 0.06644$$

$$\text{Score(Biasa)} = P(\text{Biasa}) \times \prod P(f_i \mid \text{Biasa})$$
$$= 0.80 \times 0.1341 \times 0.0488 \times 0.6829$$
$$= 0.80 \times 0.004468 = 0.003574$$

**Step 3: Normalisasi**

$$\alpha = 0.06644 + 0.003574 = 0.07001$$

$$P(\text{Rahasia} \mid \text{email}) = \frac{0.06644}{0.07001} = 0.9490 \text{ (94.9%)}$$
$$P(\text{Biasa} \mid \text{email}) = \frac{0.003574}{0.07001} = 0.0510 \text{ (5.1%)}$$

**Jawaban:** Email diklasifikasikan sebagai **"Rahasia"** dengan posterior probability **94.9%**. Keberadaan kata "operasi" dan terutama "koordinat" (yang jarang muncul di email biasa) menjadi indikator kuat bahwa email bersifat rahasia.

---

#### Jawaban Soal 13 ⭐⭐⭐

**Definisikan Utility Function:**

$$U(\text{Mode}) = w_1 \cdot \text{Detection} - w_2 \cdot \text{FalseAlarm} - w_3 \cdot \text{Biaya}_{norm} + w_4 \cdot \text{Cakupan}_{norm}$$

**Normalisasi (skala 0-1):**
- Biaya: A=10/60=0.167, B=30/60=0.500, C=60/60=1.000
- Cakupan: A=90/90=1.000, B=60/90=0.667, C=30/90=0.333

**Bobot yang wajar** (konteks pertahanan, deteksi prioritas utama):
- $w_1 = 0.40$ (deteksi — paling penting)
- $w_2 = 0.20$ (false alarm — gangguan operasional)
- $w_3 = 0.15$ (biaya operasi)
- $w_4 = 0.25$ (cakupan area)

**Perhitungan:**

**Mode A:**
$$U(A) = 0.40(0.60) - 0.20(0.15) - 0.15(0.167) + 0.25(1.000)$$
$$= 0.240 - 0.030 - 0.025 + 0.250 = 0.435$$

**Mode B:**
$$U(B) = 0.40(0.80) - 0.20(0.08) - 0.15(0.500) + 0.25(0.667)$$
$$= 0.320 - 0.016 - 0.075 + 0.167 = 0.396$$

**Mode C:**
$$U(C) = 0.40(0.95) - 0.20(0.02) - 0.15(1.000) + 0.25(0.333)$$
$$= 0.380 - 0.004 - 0.150 + 0.083 = 0.309$$

**Jawaban:** 

| Mode | Utility |
|------|---------|
| **A** | **0.435** ← Terbaik |
| B | 0.396 |
| C | 0.309 |

Mode A optimal karena cakupan area luasnya sangat berharga untuk pengawasan umum. Namun, jika situasi berubah (misalnya ancaman sudah terkonfirmasi di area tertentu), bobot deteksi harus dinaikkan dan Mode C menjadi lebih optimal.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Derivasi:**

**Step 1:** Mulai dari definisi probabilitas bersyarat:

$$P(H \mid E_1, E_2) = \frac{P(E_1, E_2, H)}{P(E_1, E_2)}$$

**Step 2:** Ekspansi numerator menggunakan chain rule:

$$P(E_1, E_2, H) = P(E_1, E_2 \mid H) \cdot P(H)$$

**Step 3:** Terapkan conditional independence — karena $E_1 \perp E_2 \mid H$:

$$P(E_1, E_2 \mid H) = P(E_1 \mid H) \cdot P(E_2 \mid H)$$

**Step 4:** Substitusi kembali:

$$P(E_1, E_2, H) = P(E_1 \mid H) \cdot P(E_2 \mid H) \cdot P(H)$$

**Step 5:** Masukkan ke rumus Bayes:

$$\boxed{P(H \mid E_1, E_2) = \frac{P(E_1 \mid H) \cdot P(E_2 \mid H) \cdot P(H)}{P(E_1, E_2)}}$$

**QED** ∎

**Catatan:** $P(E_1, E_2)$ di penyebut dapat dihitung menggunakan total probability:
$$P(E_1, E_2) = P(E_1 \mid H) P(E_2 \mid H) P(H) + P(E_1 \mid \neg H) P(E_2 \mid \neg H) P(\neg H)$$

(juga menggunakan conditional independence given $\neg H$)

---

#### Jawaban Soal 15 ⭐⭐⭐

**Diketahui:**
- Sensor 1: TPR₁ = 0.85, FPR₁ = 0.06
- Sensor 2: TPR₂ = 0.90, FPR₂ = 0.04
- Prior: P(Torpedo) = 0.03, P(¬Torpedo) = 0.97

**(a) Hanya Sensor 1 alarm:**

$$P(\text{Torpedo} \mid S_1) = \frac{P(S_1 \mid T) \cdot P(T)}{P(S_1 \mid T) \cdot P(T) + P(S_1 \mid \neg T) \cdot P(\neg T)}$$
$$= \frac{0.85 \times 0.03}{0.85 \times 0.03 + 0.06 \times 0.97} = \frac{0.0255}{0.0255 + 0.0582} = \frac{0.0255}{0.0837} = 0.3046$$

**Posterior setelah Sensor 1 saja: 30.46%**

**(b) Kedua sensor alarm (independen given hipotesis):**

$$P(S_1, S_2 \mid T) = 0.85 \times 0.90 = 0.765$$
$$P(S_1, S_2 \mid \neg T) = 0.06 \times 0.04 = 0.0024$$

$$P(\text{Torpedo} \mid S_1, S_2) = \frac{0.765 \times 0.03}{0.765 \times 0.03 + 0.0024 \times 0.97}$$
$$= \frac{0.02295}{0.02295 + 0.002328} = \frac{0.02295}{0.025278} = 0.9079$$

**Posterior setelah kedua sensor: 90.79%**

**(c) Sensor 1 alarm, Sensor 2 TIDAK alarm:**

$$P(S_1, \neg S_2 \mid T) = 0.85 \times (1-0.90) = 0.85 \times 0.10 = 0.085$$
$$P(S_1, \neg S_2 \mid \neg T) = 0.06 \times (1-0.04) = 0.06 \times 0.96 = 0.0576$$

$$P(\text{Torpedo} \mid S_1, \neg S_2) = \frac{0.085 \times 0.03}{0.085 \times 0.03 + 0.0576 \times 0.97}$$
$$= \frac{0.00255}{0.00255 + 0.05587} = \frac{0.00255}{0.05842} = 0.04364$$

**Posterior jika sensor berbeda pendapat: 4.36%**

**(d) Perbandingan dan Implikasi:**

| Skenario | Posterior |
|----------|----------|
| Prior (tanpa sensor) | 3.00% |
| Sensor 1 saja alarm | 30.46% |
| Kedua sensor alarm | **90.79%** |
| Sensor 1 alarm, Sensor 2 tidak | 4.36% |

**Implikasi pengambilan keputusan:**
1. **Kedua sensor sepakat alarm** → Probabilitas sangat tinggi (90.8%), tindakan evasif harus segera diambil
2. **Hanya satu sensor alarm** → Probabilitas moderat (30.5%), lakukan verifikasi tambahan sebelum tindakan agresif
3. **Sensor berbeda pendapat** → Probabilitas rendah (4.4%), mendekati prior, sensor yang tidak alarm "menetralisir" yang alarm
4. **Sensor fusion sangat powerful:** Dua sensor independen yang sepakat memberikan kepastian jauh lebih tinggi daripada satu sensor saja. Ini menjustifikasi investasi dalam redundansi sensor.

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Deteksi Ancaman Maritim Multi-Sensor

**1a. Posterior setelah Sensor 1 saja (kecepatan tinggi) — 15 poin**

**Step 1: Hitung unnormalized posterior**

| Hipotesis | Prior | Likelihood | Unnormalized |
|-----------|-------|-----------|-------------|
| Dagang | 0.60 | 0.10 | 0.060 |
| Ikan | 0.25 | 0.05 | 0.0125 |
| Patroli Asing | 0.10 | 0.70 | 0.070 |
| Mencurigakan | 0.05 | 0.60 | 0.030 |

**Step 2: Normalisasi**

$$\alpha = 0.060 + 0.0125 + 0.070 + 0.030 = 0.1725$$

| Hipotesis | Posterior |
|-----------|----------|
| Dagang | 0.060 / 0.1725 = **0.3478 (34.8%)** |
| Ikan | 0.0125 / 0.1725 = **0.0725 (7.2%)** |
| Patroli Asing | 0.070 / 0.1725 = **0.4058 (40.6%)** |
| Mencurigakan | 0.030 / 0.1725 = **0.1739 (17.4%)** |

**Verifikasi:** 0.3478 + 0.0725 + 0.4058 + 0.1739 = 1.000 ✓

Setelah radar mendeteksi kecepatan tinggi, Kapal Patroli Asing menjadi hipotesis paling probable (40.6%), naik dari prior 10%.

---

**1b. Posterior setelah Sensor 1 + Sensor 2 (kecepatan tinggi + tanpa AIS) — 20 poin**

Karena sensor conditionally independent, kita dapat menggabungkan likelihood:

**Step 1: Hitung combined likelihood**

| Hipotesis | L₁ (kecepatan) | L₂ (tanpa AIS) | Combined |
|-----------|:---:|:---:|:---:|
| Dagang | 0.10 | 0.05 | 0.005 |
| Ikan | 0.05 | 0.40 | 0.020 |
| Patroli Asing | 0.70 | 0.30 | 0.210 |
| Mencurigakan | 0.60 | 0.85 | 0.510 |

**Step 2: Hitung unnormalized posterior**

| Hipotesis | Prior | Combined L | Unnormalized |
|-----------|-------|-----------|-------------|
| Dagang | 0.60 | 0.005 | 0.00300 |
| Ikan | 0.25 | 0.020 | 0.00500 |
| Patroli Asing | 0.10 | 0.210 | 0.02100 |
| Mencurigakan | 0.05 | 0.510 | 0.02550 |

**Step 3: Normalisasi**

$$\alpha = 0.00300 + 0.00500 + 0.02100 + 0.02550 = 0.05450$$

| Hipotesis | Posterior |
|-----------|----------|
| Dagang | 0.00300 / 0.05450 = **0.0550 (5.5%)** |
| Ikan | 0.00500 / 0.05450 = **0.0917 (9.2%)** |
| Patroli Asing | 0.02100 / 0.05450 = **0.3853 (38.5%)** |
| Mencurigakan | 0.02550 / 0.05450 = **0.4679 (46.8%)** |

Dengan dua sensor, "Kapal Mencurigakan" menjadi paling probable (46.8%), digerakkan terutama oleh fakta bahwa kapal tidak mengirim sinyal AIS.

---

**1c. Bayesian updating dengan Sensor 3 (visual mencurigakan) — 15 poin**

Gunakan posterior dari 1b sebagai prior baru:

**Step 1: Hitung unnormalized posterior**

| Hipotesis | Prior baru (dari 1b) | L₃ (visual) | Unnormalized |
|-----------|:---:|:---:|:---:|
| Dagang | 0.0550 | 0.03 | 0.001650 |
| Ikan | 0.0917 | 0.08 | 0.007336 |
| Patroli Asing | 0.3853 | 0.25 | 0.096325 |
| Mencurigakan | 0.4679 | 0.90 | 0.421110 |

**Step 2: Normalisasi**

$$\alpha = 0.001650 + 0.007336 + 0.096325 + 0.421110 = 0.526421$$

| Hipotesis | Posterior |
|-----------|----------|
| Dagang | 0.001650 / 0.526421 = **0.0031 (0.3%)** |
| Ikan | 0.007336 / 0.526421 = **0.0139 (1.4%)** |
| Patroli Asing | 0.096325 / 0.526421 = **0.1830 (18.3%)** |
| Mencurigakan | 0.421110 / 0.526421 = **0.7999 (80.0%)** |

Setelah tiga sensor, "Kapal Mencurigakan" memiliki posterior ~80.0%.

---

**1d. Evolusi posterior "Kapal Mencurigakan" — 10 poin**

| Tahap | Posterior Mencurigakan |
|-------|:-----:|
| Prior (tanpa data) | 5.0% |
| Setelah Sensor 1 (radar) | 17.4% |
| Setelah Sensor 1 + 2 (radar + AIS) | 46.8% |
| Setelah Sensor 1 + 2 + 3 (radar + AIS + satelit) | 80.0% |

**Insight tentang sensor fusion:**
1. **Bukti kumulatif sangat kuat:** Setiap sensor menambah kepastian secara signifikan — dari 5% hingga 80%
2. **Sensor yang berbeda lebih berharga daripada sensor yang sama:** Radar mengukur kecepatan, AIS mengukur kepatuhan identifikasi, satelit mengukur visual — masing-masing memberikan informasi orthogonal
3. **Tidak ada satu sensor yang cukup:** Sensor 1 saja hanya menaikkan posterior ke 17.4% — jauh dari threshold keputusan
4. **Diminishing returns:** Peningkatan dari sensor 1 ke 2 (+29.4pp) lebih besar dari sensor 2 ke 3 (+33.2pp) secara relatif, tetapi sensor 3 tetap memberikan konfirmasi penting
5. **Bayesian framework alami untuk multi-sensor:** Kerangka ini secara natural mengintegrasikan berbagai sumber informasi tanpa perlu aturan ad hoc

---

**1e. Threshold Decision Rule — 10 poin**

**Rancangan threshold decision rule:**

| Level | Posterior "Mencurigakan" | Tindakan |
|-------|:-----:|----------|
| **NORMAL** | < 15% | Monitoring rutin, catat dalam log |
| **WASPADA** | 15% — 40% | Tingkatkan monitoring, aktifkan semua sensor, siapkan kapal patroli |
| **SIAGA** | 40% — 70% | Kirim kapal patroli untuk visual contact, laporkan ke komando |
| **KRITIS** | > 70% | Intercept langsung, deployment aset militer, eskalasi ke komando tinggi |

**Justifikasi asymmetric threshold:**
- Threshold intercept (40%) sengaja dibuat LEBIH RENDAH dari 50% karena biaya false negative (melewatkan kapal penyelundup) jauh lebih tinggi daripada biaya false positive (mengirim patroli sia-sia)
- Dalam konteks keamanan nasional, "better safe than sorry" — 40% kemungkinan ancaman sudah memerlukan investigasi aktif
- Cost-benefit: Biaya satu kali pengiriman patroli jauh lebih kecil daripada kerugian jika penyelundupan berhasil

---

#### Studi Kasus 2: Sistem Klasifikasi Sinyal SIGINT

**2a. Tabel Conditional Probability dengan Laplace Smoothing — 15 poin**

Laplace smoothing: $P(F_i = \text{ya} \mid H_j) = \frac{\text{count} + 1}{n_j + 2}$

(+2 di penyebut karena fitur biner: ya/tidak, sehingga $k = 2$)

| Fitur | $H_1$ (n=16) | $H_2$ (n=130) | $H_3$ (n=30) | $H_4$ (n=14) | $H_5$ (n=10) |
|-------|:---:|:---:|:---:|:---:|:---:|
| P($F_1$=ya) | 15/18 = 0.8333 | 6/132 = 0.0455 | 1/32 = 0.0313 | 11/16 = 0.6875 | 1/12 = 0.0833 |
| P($F_1$=tidak) | 3/18 = 0.1667 | 126/132 = 0.9545 | 31/32 = 0.9688 | 5/16 = 0.3125 | 11/12 = 0.9167 |
| P($F_2$=ya) | 16/18 = 0.8889 | 9/132 = 0.0682 | 4/32 = 0.1250 | 10/16 = 0.6250 | 2/12 = 0.1667 |
| P($F_2$=tidak) | 2/18 = 0.1111 | 123/132 = 0.9318 | 28/32 = 0.8750 | 6/16 = 0.3750 | 10/12 = 0.8333 |
| P($F_3$=burst) | 13/18 = 0.7222 | 16/132 = 0.1212 | 3/32 = 0.0938 | 12/16 = 0.7500 | 3/12 = 0.2500 |
| P($F_3$=kontinu) | 5/18 = 0.2778 | 116/132 = 0.8788 | 29/32 = 0.9063 | 4/16 = 0.2500 | 9/12 = 0.7500 |

---

**2b. Klasifikasi sinyal: $F_1$=ya, $F_2$=ya, $F_3$=burst — 20 poin**

**Step 1: Hitung skor (prior × likelihood) untuk setiap kelas**

$$\text{Score}(H_1) = P(H_1) \times P(F_1\text{=ya} \mid H_1) \times P(F_2\text{=ya} \mid H_1) \times P(F_3\text{=burst} \mid H_1)$$
$$= 0.08 \times 0.8333 \times 0.8889 \times 0.7222 = 0.08 \times 0.5350 = 0.04280$$

$$\text{Score}(H_2) = 0.65 \times 0.0455 \times 0.0682 \times 0.1212 = 0.65 \times 0.000244 = 0.000159$$

$$\text{Score}(H_3) = 0.15 \times 0.0313 \times 0.1250 \times 0.0938 = 0.15 \times 0.000367 = 0.0000550$$

$$\text{Score}(H_4) = 0.07 \times 0.6875 \times 0.6250 \times 0.7500 = 0.07 \times 0.3223 = 0.02256$$

$$\text{Score}(H_5) = 0.05 \times 0.0833 \times 0.1667 \times 0.2500 = 0.05 \times 0.003472 = 0.000174$$

**Step 2: Normalisasi**

$$\alpha = 0.04280 + 0.000159 + 0.0000550 + 0.02256 + 0.000174 = 0.06575$$

| Hipotesis | Posterior |
|-----------|----------|
| $H_1$ Militer Asing | 0.04280 / 0.06575 = **0.6510 (65.1%)** |
| $H_2$ Sipil | 0.000159 / 0.06575 = **0.0024 (0.2%)** |
| $H_3$ Navigasi | 0.0000550 / 0.06575 = **0.0008 (0.1%)** |
| $H_4$ Mencurigakan | 0.02256 / 0.06575 = **0.3432 (34.3%)** |
| $H_5$ Noise | 0.000174 / 0.06575 = **0.0026 (0.3%)** |

**Klasifikasi:** Sinyal diklasifikasikan sebagai **Komunikasi Militer Asing ($H_1$)** dengan posterior **65.1%**. $H_4$ (Mencurigakan) juga cukup tinggi (34.3%).

---

**2c. Klasifikasi sinyal kedua: $F_1$=tidak, $F_2$=ya, $F_3$=kontinu — 15 poin**

$$\text{Score}(H_1) = 0.08 \times 0.1667 \times 0.8889 \times 0.2778 = 0.08 \times 0.04115 = 0.003292$$

$$\text{Score}(H_2) = 0.65 \times 0.9545 \times 0.0682 \times 0.8788 = 0.65 \times 0.03717 = 0.02416$$

$$\text{Score}(H_3) = 0.15 \times 0.9688 \times 0.1250 \times 0.9063 = 0.15 \times 0.10971 = 0.01646$$

$$\text{Score}(H_4) = 0.07 \times 0.3125 \times 0.6250 \times 0.2500 = 0.07 \times 0.04883 = 0.003418$$

$$\text{Score}(H_5) = 0.05 \times 0.9167 \times 0.1667 \times 0.7500 = 0.05 \times 0.11459 = 0.005730$$

$$\alpha = 0.003292 + 0.02416 + 0.01646 + 0.003418 + 0.005730 = 0.05306$$

| Hipotesis | Posterior |
|-----------|----------|
| $H_1$ Militer Asing | 0.003292 / 0.05306 = **0.0621 (6.2%)** |
| $H_2$ Sipil | 0.02416 / 0.05306 = **0.4553 (45.5%)** |
| $H_3$ Navigasi | 0.01646 / 0.05306 = **0.3103 (31.0%)** |
| $H_4$ Mencurigakan | 0.003418 / 0.05306 = **0.0644 (6.4%)** |
| $H_5$ Noise | 0.005730 / 0.05306 = **0.1080 (10.8%)** |

**Klasifikasi:** Sinyal kedua diklasifikasikan sebagai **Komunikasi Sipil ($H_2$)** dengan posterior **45.5%**. Tidak ada enkripsi dan sifat kontinu menjadi indikator kuat sinyal sipil. $H_3$ (Navigasi) juga cukup tinggi (31.0%) karena sinyal navigasi juga umumnya tidak terenkripsi dan kontinu.

---

**2d. Pengaruh pelanggaran asumsi independensi — 10 poin**

**Analisis korelasi $F_1$ dan $F_2$:**
Untuk sinyal militer asing, $P(F_1\text{=ya} \mid H_1) = 0.83$ dan $P(F_2\text{=ya} \mid H_1) = 0.89$. Dalam kenyataan, kedua fitur ini sangat berkorelasi: sinyal militer yang terenkripsi ($F_1$) hampir pasti berada di band militer ($F_2$).

**Dampak pada klasifikasi:**
Naive Bayes menghitung:
$$P(F_1\text{=ya}, F_2\text{=ya} \mid H_1) = P(F_1\text{=ya} \mid H_1) \times P(F_2\text{=ya} \mid H_1) = 0.83 \times 0.89 = 0.74$$

Tetapi probabilitas sesungguhnya mungkin mendekati:
$$P(F_1\text{=ya}, F_2\text{=ya} \mid H_1) \approx 0.83$$ (karena enkripsi militer selalu di band militer)

**Dampak: OVERESTIMATE** probabilitas $H_1$

Naive Bayes menghitung seolah-olah kedua fitur memberikan bukti independen, padahal sebenarnya $F_2$ redundan jika $F_1$ sudah diketahui. Ini meng-double count bukti dan membuat posterior $H_1$ lebih tinggi dari seharusnya.

**Namun demikian**, dalam kasus ini overestimate $H_1$ tidak terlalu merugikan karena:
- Ranking klasifikasi (urutan kelas) kemungkinan tetap benar
- Untuk keamanan nasional, lebih baik overestimate ancaman militer daripada underestimate

---

**2e. Sistem prioritas response — 10 poin**

**Framework Prioritas Asymmetric:**

| Level | Kondisi | Tindakan |
|-------|---------|----------|
| **KRITIS** | $P(H_1) > 40\%$ ATAU $P(H_4) > 50\%$ | Eskalasi segera ke komandan intelijen. Aktivasi full monitoring. Laporkan ke Mabes. Rekam dan analisis mendalam sinyal. |
| **TINGGI** | $P(H_1) \in [15\%, 40\%]$ ATAU $P(H_4) \in [25\%, 50\%]$ ATAU $P(H_1) + P(H_4) > 40\%$ | Analis senior ditugaskan. Monitoring intensif. Cross-reference dengan sumber intelijen lain. Siapkan laporan. |
| **SEDANG** | $P(H_1) \in [5\%, 15\%]$ ATAU $P(H_4) \in [10\%, 25\%]$ | Analis melakukan verifikasi tambahan. Kumpulkan fitur tambahan jika memungkinkan. Log untuk analisis pola. |
| **RENDAH** | $P(H_2) > 60\%$ ATAU $P(H_3) > 60\%$ ATAU $P(H_5) > 60\%$ | Pencatatan rutin. Tidak perlu eskalasi. Review berkala. |

**Justifikasi threshold asimetris:**
1. **$H_1$ (Militer Asing) threshold lebih rendah (40%):** Melewatkan sinyal militer asing bisa menyebabkan kegagalan intelijen yang katastrofik. Lebih baik false alarm daripada miss
2. **$H_4$ (Mencurigakan) threshold moderat (50%):** Sinyal mencurigakan perlu investigasi tetapi risikonya sedikit lebih rendah dari sinyal militer terkonfirmasi
3. **Kombinasi $H_1 + H_4$:** Jika total probabilitas ancaman tinggi meskipun masing-masing di bawah threshold individual, tetap eskalasi
4. **$H_2$, $H_3$, $H_5$ hanya butuh dominasi kuat (>60%):** Baru dianggap rendah jika bukti non-ancaman sangat kuat

**Penerapan pada hasil 2b:**
Sinyal pertama: $P(H_1) = 65.1\%$ → Level **KRITIS** → Eskalasi segera

**Penerapan pada hasil 2c:**
Sinyal kedua: $P(H_1) = 6.2\%$, $P(H_4) = 6.4\%$ → Level **SEDANG** → Verifikasi tambahan

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
- Studi Kasus 1: 70 poin
- Studi Kasus 2: 70 poin
- Total: 140 poin

### Total Keseluruhan: 305 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
