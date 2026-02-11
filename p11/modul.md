# Modul 11: Penalaran dengan Ketidakpastian - Probabilitas

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 11  
**Topik:** Penalaran dengan Ketidakpastian - Probabilitas  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan sumber-sumber ketidakpastian dalam sistem AI
2. Mengidentifikasi keterbatasan logika dalam menangani ketidakpastian
3. Menerapkan aturan dasar probabilitas termasuk probabilitas bersyarat dan aturan produk
4. Menghitung probabilitas posterior menggunakan Teorema Bayes
5. Melakukan normalisasi dalam perhitungan probabilistik
6. Membedakan independensi dan independensi bersyarat
7. Menerapkan Naive Bayes sebagai model probabilistik untuk klasifikasi

---

## 1. Sumber Ketidakpastian dalam AI

### 1.1 Mengapa Ketidakpastian Penting?

Dalam pertemuan-pertemuan sebelumnya (Pertemuan 9-10), kita mempelajari representasi pengetahuan menggunakan logika proposisional dan logika predikat. Logika bekerja dengan baik ketika pengetahuan bersifat pasti dan lengkap. Namun, di dunia nyata, agen AI sering menghadapi **ketidakpastian**.

> **Ketidakpastian (Uncertainty)** dalam AI adalah kondisi di mana agen tidak memiliki informasi lengkap atau pasti tentang state lingkungan, efek dari tindakan, atau hubungan sebab-akibat dalam domainnya.

Pertimbangkan skenario berikut: Sebuah sistem radar pertahanan udara mendeteksi sinyal pada layar. Apakah sinyal tersebut pesawat musuh, pesawat sipil, burung, atau noise? Sistem tidak dapat menjawab dengan kepastian absolut menggunakan logika biner (benar/salah).

### 1.2 Dua Sumber Utama Ketidakpastian

Russell dan Norvig mengidentifikasi dua sumber utama ketidakpastian:

| Sumber | Deskripsi | Contoh |
|--------|-----------|--------|
| **Laziness (Kemalasan)** | Terlalu sulit atau mahal untuk mendaftar semua aturan/pengecualian | Aturan "jika demam maka flu" mengabaikan puluhan penyakit lain |
| **Ignorance (Ketidaktahuan)** | Informasi yang diperlukan tidak tersedia | Hasil tes medis belum keluar, data radar tidak lengkap |

Selain itu, ketidakpastian juga muncul dari:
- **Sensor noise**: Data yang diterima tidak akurat
- **Non-determinism**: Aksi yang sama bisa menghasilkan efek berbeda
- **Adversarial actions**: Musuh yang sengaja menyembunyikan informasi

#### Solved Problem 1 ⭐

**Soal:** Identifikasi sumber ketidakpastian pada sistem deteksi intrusi siber (Intrusion Detection System/IDS) yang dioperasikan BSSN!

**Penyelesaian:**

*Step 1:* Identifikasi ketidakpastian dari laziness
- IDS tidak dapat mendaftar semua pola serangan yang mungkin
- Aturan deteksi selalu incomplete karena serangan baru (zero-day)

*Step 2:* Identifikasi ketidakpastian dari ignorance
- Traffic yang dienkripsi tidak dapat diinspeksi
- Niat sebenarnya dari sebuah paket data tidak diketahui
- Konteks pengirim (friend or foe) sering tidak jelas

*Step 3:* Identifikasi sumber lain
- **Sensor noise**: Network packet loss atau corruption
- **Non-determinism**: Malware polymorphic yang mengubah signature
- **Adversarial**: Penyerang sengaja menyamarkan traffic

**Jawaban:** IDS menghadapi ketidakpastian dari: (1) laziness — tidak mungkin mendaftar semua pola serangan, (2) ignorance — traffic terenkripsi dan konteks pengirim tidak diketahui, (3) sensor noise — packet loss, (4) adversarial — penyerang menyamarkan aktivitas. Karena itu, IDS modern menggunakan pendekatan probabilistik untuk menilai tingkat ancaman.

---

### 1.3 Keterbatasan Logika untuk Ketidakpastian

Logika proposisional dan predikat (Pertemuan 9-10) memiliki keterbatasan dalam menangani ketidakpastian:

| Keterbatasan | Penjelasan |
|-------------|------------|
| **Biner** | Logika hanya mengenal TRUE atau FALSE, tidak ada "mungkin" |
| **Monotonic** | Menambah informasi baru tidak pernah membatalkan kesimpulan lama |
| **Closed-world assumption** | Apa yang tidak diketahui dianggap salah |
| **Qualification problem** | Tidak mungkin mendaftar semua prasyarat untuk sebuah aturan |

**Contoh Qualification Problem:**

Dalam logika: "Jika ada sinyal radar DAN kecepatan > Mach 1 DAN altitude > 10.000 ft MAKA pesawat tempur musuh"

Aturan ini mengabaikan banyak pengecualian: bisa jadi pesawat uji coba, pesawat sipil supersonik, drone, dll. Menambah semua pengecualian menjadi tidak praktis.

> **Solusi:** Daripada menggunakan logika biner, kita menggunakan **derajat kepercayaan (degree of belief)** yang direpresentasikan sebagai **probabilitas**.

#### Solved Problem 2 ⭐

**Soal:** Mengapa pendekatan logika murni tidak cukup untuk sistem diagnosis kerusakan pesawat tempur?

**Penyelesaian:**

*Step 1:* Identifikasi masalah dengan pendekatan logika

Aturan logika: "IF engine_temperature_high AND oil_pressure_low THEN engine_failure"

*Step 2:* Analisis keterbatasan
- **Ketidakpastian sensor**: Sensor suhu mungkin tidak akurat
- **Multiple causes**: Suhu tinggi bisa disebabkan banyak hal (cuaca, beban, sensor error)
- **Qualification problem**: Banyak kondisi lain yang relevan (altitude, kecepatan, umur mesin)
- **Partial information**: Tidak semua sensor tersedia atau berfungsi

*Step 3:* Jelaskan kebutuhan probabilistik
- Sistem perlu mengatakan: "Probabilitas engine failure = 0.85" daripada binary TRUE/FALSE
- Memungkinkan pilot mengambil keputusan berdasarkan tingkat risiko

**Jawaban:** Logika murni tidak cukup karena: (1) sensor memiliki noise sehingga input tidak pasti, (2) gejala yang sama bisa disebabkan banyak hal sehingga tidak bisa ditentukan pasti, (3) tidak mungkin mendaftar semua kondisi yang relevan. Pendekatan probabilistik memberikan derajat kepercayaan yang lebih informatif untuk pengambilan keputusan.

---

## 2. Dasar-Dasar Probabilitas

### 2.1 Konsep Dasar

Materi ini merupakan review dan pendalaman dari mata kuliah **Statistika dan Probabilitas (Semester 3)**, difokuskan pada penerapannya dalam AI.

> **Probabilitas** adalah ukuran numerik dari derajat kepercayaan terhadap suatu proposisi, dengan nilai antara 0 (pasti salah) dan 1 (pasti benar).

**Notasi dan Terminologi:**

| Simbol | Makna | Contoh |
|--------|-------|--------|
| $P(A)$ | Probabilitas event A | $P(\text{Hujan}) = 0.3$ |
| $P(\neg A)$ | Probabilitas bukan A | $P(\neg\text{Hujan}) = 0.7$ |
| $P(A, B)$ | Joint probability A dan B | $P(\text{Hujan}, \text{Macet})$ |
| $P(A \mid B)$ | Probabilitas A given B | $P(\text{Macet} \mid \text{Hujan})$ |

### 2.2 Aksioma Probabilitas (Kolmogorov)

Tiga aksioma dasar probabilitas:

1. **Non-negativity**: $P(A) \geq 0$ untuk semua event A
2. **Normalization**: $P(\Omega) = 1$ (probabilitas seluruh sample space = 1)
3. **Additivity**: Jika A dan B mutually exclusive, maka $P(A \cup B) = P(A) + P(B)$

Dari aksioma ini, diturunkan:
- $P(\neg A) = 1 - P(A)$
- $0 \leq P(A) \leq 1$

### 2.3 Prior Probability (Probabilitas Prior)

> **Prior Probability** adalah probabilitas yang ditetapkan sebelum ada bukti (evidence) baru. Disebut juga **unconditional probability**.

Contoh:
- $P(\text{Pesawat asing melintas perbatasan}) = 0.02$ (berdasarkan data historis)
- $P(\text{Sensor radar mendeteksi objek}) = 0.15$

#### Solved Problem 3 ⭐

**Soal:** Data historis menunjukkan bahwa dari 10.000 penerbangan yang melintas wilayah udara Indonesia, 200 adalah pesawat yang tidak teridentifikasi. Berapa probabilitas prior bahwa penerbangan berikutnya adalah tidak teridentifikasi?

**Penyelesaian:**

*Step 1:* Identifikasi data
- Total penerbangan: 10.000
- Pesawat tidak teridentifikasi: 200

*Step 2:* Hitung probabilitas prior

$$P(\text{Tidak Teridentifikasi}) = \frac{200}{10.000} = 0.02$$

**Jawaban:** $P(\text{Tidak Teridentifikasi}) = 0.02$ atau 2%.

---

### 2.4 Joint Probability (Probabilitas Gabungan)

> **Joint Probability** $P(A, B)$ adalah probabilitas bahwa event A dan event B terjadi bersamaan.

**Contoh — Joint Probability Table:**

Survei pada 1000 misi drone TNI AU:

| | Misi Sukses | Misi Gagal | **Total** |
|---|:---:|:---:|:---:|
| Cuaca Baik | 600 | 50 | 650 |
| Cuaca Buruk | 200 | 150 | 350 |
| **Total** | 800 | 200 | **1000** |

Dari tabel ini:
- $P(\text{Cuaca Baik}, \text{Sukses}) = 600/1000 = 0.60$
- $P(\text{Cuaca Buruk}, \text{Gagal}) = 150/1000 = 0.15$

**Marginal Probability** diperoleh dengan menjumlahkan baris/kolom:
- $P(\text{Sukses}) = 800/1000 = 0.80$
- $P(\text{Cuaca Baik}) = 650/1000 = 0.65$

#### Solved Problem 4 ⭐

**Soal:** Dari tabel di atas, hitung: (a) $P(\text{Cuaca Baik}, \text{Gagal})$, (b) $P(\text{Cuaca Buruk})$, (c) $P(\text{Gagal})$.

**Penyelesaian:**

*Step 1:* Hitung joint probability

(a) $P(\text{Cuaca Baik}, \text{Gagal}) = \frac{50}{1000} = 0.05$

*Step 2:* Hitung marginal probabilities

(b) $P(\text{Cuaca Buruk}) = \frac{350}{1000} = 0.35$

(c) $P(\text{Gagal}) = \frac{200}{1000} = 0.20$

**Jawaban:** (a) 0.05, (b) 0.35, (c) 0.20.

---

### 2.5 Conditional Probability (Probabilitas Bersyarat)

> **Probabilitas Bersyarat** $P(A \mid B)$ adalah probabilitas terjadinya event A, diketahui bahwa event B telah terjadi.

$$P(A \mid B) = \frac{P(A, B)}{P(B)}, \quad P(B) > 0$$

Rumus ini juga dapat ditulis ulang sebagai **Aturan Produk (Product Rule)**:

$$P(A, B) = P(A \mid B) \cdot P(B)$$

atau equivalen:

$$P(A, B) = P(B \mid A) \cdot P(A)$$

![Probabilitas Bersyarat](images/p11-01-conditional-probability-venn.png)

*Gambar 11.1: Visualisasi probabilitas bersyarat dengan diagram Venn*

#### Solved Problem 5 ⭐

**Soal:** Menggunakan tabel misi drone di atas, hitung probabilitas misi sukses jika cuaca baik!

**Penyelesaian:**

*Step 1:* Identifikasi apa yang dicari
- $P(\text{Sukses} \mid \text{Cuaca Baik})$

*Step 2:* Terapkan rumus probabilitas bersyarat

$$P(\text{Sukses} \mid \text{Cuaca Baik}) = \frac{P(\text{Sukses}, \text{Cuaca Baik})}{P(\text{Cuaca Baik})}$$

*Step 3:* Substitusi nilai

$$P(\text{Sukses} \mid \text{Cuaca Baik}) = \frac{0.60}{0.65} = 0.923$$

**Jawaban:** $P(\text{Sukses} \mid \text{Cuaca Baik}) = 0.923$ atau 92.3%. Misi drone memiliki tingkat keberhasilan sangat tinggi saat cuaca baik.

#### Solved Problem 6 ⭐⭐

**Soal:** Dari data yang sama, hitung $P(\text{Sukses} \mid \text{Cuaca Buruk})$ dan bandingkan dengan $P(\text{Sukses} \mid \text{Cuaca Baik})$. Apa implikasinya untuk perencanaan operasi?

**Penyelesaian:**

*Step 1:* Hitung $P(\text{Sukses} \mid \text{Cuaca Buruk})$

$$P(\text{Sukses} \mid \text{Cuaca Buruk}) = \frac{P(\text{Sukses}, \text{Cuaca Buruk})}{P(\text{Cuaca Buruk})} = \frac{0.20}{0.35} = 0.571$$

*Step 2:* Bandingkan

| Kondisi | P(Sukses) |
|---------|-----------|
| Cuaca Baik | 92.3% |
| Cuaca Buruk | 57.1% |
| Tanpa informasi cuaca | 80.0% |

*Step 3:* Analisis implikasi
- Cuaca buruk menurunkan keberhasilan dari 92.3% menjadi 57.1%
- Informasi cuaca sangat penting untuk perencanaan operasi
- Menunda misi saat cuaca buruk bisa meningkatkan success rate signifikan

**Jawaban:** $P(\text{Sukses} \mid \text{Cuaca Buruk}) = 0.571$ (57.1%), jauh lebih rendah dari 92.3% saat cuaca baik. Implikasi: informasi cuaca merupakan faktor kritis dalam perencanaan operasi drone, dan penundaan misi saat cuaca buruk adalah keputusan rasional untuk memaksimalkan success rate.

---

## 3. Teorema Bayes

### 3.1 Formulasi Teorema Bayes

> **Teorema Bayes** memungkinkan kita memperbarui kepercayaan (belief) terhadap suatu hipotesis berdasarkan bukti (evidence) baru.

$$P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)}$$

dimana:

| Komponen | Nama | Makna |
|----------|------|-------|
| $P(H \mid E)$ | **Posterior** | Probabilitas hipotesis setelah melihat evidence |
| $P(E \mid H)$ | **Likelihood** | Probabilitas evidence jika hipotesis benar |
| $P(H)$ | **Prior** | Probabilitas awal hipotesis sebelum evidence |
| $P(E)$ | **Evidence** | Probabilitas total dari evidence (normalizer) |

![Teorema Bayes](images/p11-02-bayes-theorem-components.png)

*Gambar 11.2: Komponen Teorema Bayes dan alur pembaruan kepercayaan*

### 3.2 Derivasi Teorema Bayes

Teorema Bayes diturunkan dari aturan produk:

*Step 1:* Dari aturan produk, kita tahu:
$$P(H, E) = P(H \mid E) \cdot P(E)$$

*Step 2:* Juga:
$$P(H, E) = P(E \mid H) \cdot P(H)$$

*Step 3:* Karena kedua ruas sama:
$$P(H \mid E) \cdot P(E) = P(E \mid H) \cdot P(H)$$

*Step 4:* Bagi kedua ruas dengan $P(E)$:
$$P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)}$$

#### Solved Problem 7 ⭐

**Soal:** Sebuah radar memiliki karakteristik berikut: jika ada pesawat musuh, radar mendeteksinya dengan probabilitas 0.95 (true positive rate). Jika tidak ada pesawat musuh, radar memberikan alarm palsu dengan probabilitas 0.03 (false positive rate). Data historis menunjukkan probabilitas adanya pesawat musuh di suatu waktu adalah 0.01. Jika radar memberikan alarm, berapa probabilitas benar-benar ada pesawat musuh?

**Penyelesaian:**

*Step 1:* Identifikasi komponen
- $H$ = ada pesawat musuh
- $E$ = radar memberikan alarm
- $P(H) = 0.01$ (prior)
- $P(E \mid H) = 0.95$ (likelihood — true positive)
- $P(E \mid \neg H) = 0.03$ (false positive rate)

*Step 2:* Hitung $P(E)$ menggunakan Total Probability

$$P(E) = P(E \mid H) \cdot P(H) + P(E \mid \neg H) \cdot P(\neg H)$$
$$P(E) = 0.95 \times 0.01 + 0.03 \times 0.99$$
$$P(E) = 0.0095 + 0.0297 = 0.0392$$

*Step 3:* Terapkan Teorema Bayes

$$P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)} = \frac{0.95 \times 0.01}{0.0392} = \frac{0.0095}{0.0392} = 0.2423$$

**Jawaban:** $P(H \mid E) = 0.2423$ atau sekitar 24.2%. Meskipun radar memiliki true positive rate tinggi (95%), probabilitas pesawat musuh benar ada hanya 24.2% saat alarm berbunyi. Ini karena prior yang sangat rendah (1%) — sebagian besar alarm kemungkinan false positive.

#### Solved Problem 8 ⭐⭐

**Soal:** Melanjutkan Solved Problem 7, jika radar memberikan alarm dua kali berturut-turut (kedua deteksi independen), berapa probabilitas bahwa benar ada pesawat musuh?

**Penyelesaian:**

*Step 1:* Gunakan hasil pertama sebagai prior baru
- Setelah alarm pertama: $P(H \mid E_1) = 0.2423$

*Step 2:* Terapkan Bayes untuk alarm kedua
- Prior baru: $P(H) = 0.2423$
- $P(E_2 \mid H) = 0.95$
- $P(E_2 \mid \neg H) = 0.03$

*Step 3:* Hitung $P(E_2)$ dengan prior baru

$$P(E_2) = 0.95 \times 0.2423 + 0.03 \times 0.7577$$
$$P(E_2) = 0.2302 + 0.0227 = 0.2529$$

*Step 4:* Terapkan Bayes

$$P(H \mid E_1, E_2) = \frac{0.95 \times 0.2423}{0.2529} = \frac{0.2302}{0.2529} = 0.9102$$

**Jawaban:** $P(H \mid E_1, E_2) = 0.9102$ atau 91.0%. Dua alarm berturut-turut meningkatkan kepercayaan secara dramatis dari 24.2% menjadi 91.0%. Ini menunjukkan kekuatan Bayesian updating — setiap bukti baru memperbarui kepercayaan kita.

---

### 3.3 Total Probability (Hukum Probabilitas Total)

> **Hukum Probabilitas Total** digunakan untuk menghitung $P(E)$ (penyebut Teorema Bayes):

$$P(E) = \sum_{i} P(E \mid H_i) \cdot P(H_i)$$

dimana $H_1, H_2, ..., H_n$ adalah partisi yang saling lepas dan lengkap dari ruang sampel.

Untuk kasus biner (hanya dua hipotesis):

$$P(E) = P(E \mid H) \cdot P(H) + P(E \mid \neg H) \cdot P(\neg H)$$

#### Solved Problem 9 ⭐⭐

**Soal:** Dalam operasi intelijen, ada tiga kemungkinan sumber sinyal yang terdeteksi oleh sistem SIGINT: (1) Komunikasi militer musuh ($H_1$, prior 0.10), (2) Komunikasi sipil ($H_2$, prior 0.70), (3) Noise/interferensi ($H_3$, prior 0.20). Jika sinyal terenkripsi, probabilitas enkripsi untuk masing-masing sumber: $P(\text{Enkripsi} \mid H_1) = 0.90$, $P(\text{Enkripsi} \mid H_2) = 0.10$, $P(\text{Enkripsi} \mid H_3) = 0.01$. Sinyal yang tertangkap terenkripsi. Hitung probabilitas posterior untuk setiap hipotesis!

**Penyelesaian:**

*Step 1:* Hitung $P(\text{Enkripsi})$ menggunakan total probability

$$P(E) = P(E \mid H_1) \cdot P(H_1) + P(E \mid H_2) \cdot P(H_2) + P(E \mid H_3) \cdot P(H_3)$$
$$P(E) = 0.90 \times 0.10 + 0.10 \times 0.70 + 0.01 \times 0.20$$
$$P(E) = 0.09 + 0.07 + 0.002 = 0.162$$

*Step 2:* Hitung posterior untuk setiap hipotesis

$$P(H_1 \mid E) = \frac{0.90 \times 0.10}{0.162} = \frac{0.09}{0.162} = 0.5556$$

$$P(H_2 \mid E) = \frac{0.10 \times 0.70}{0.162} = \frac{0.07}{0.162} = 0.4321$$

$$P(H_3 \mid E) = \frac{0.01 \times 0.20}{0.162} = \frac{0.002}{0.162} = 0.0123$$

*Step 3:* Verifikasi (harus berjumlah 1)

$$0.5556 + 0.4321 + 0.0123 = 1.0000 \checkmark$$

**Jawaban:**

| Hipotesis | Prior | Posterior | Perubahan |
|-----------|-------|-----------|-----------|
| Komunikasi militer ($H_1$) | 0.10 | **0.556** | ↑ Naik signifikan |
| Komunikasi sipil ($H_2$) | 0.70 | 0.432 | ↓ Turun |
| Noise ($H_3$) | 0.20 | 0.012 | ↓ Turun drastis |

Bukti enkripsi meningkatkan probabilitas komunikasi militer dari 10% menjadi 55.6%, sementara noise hampir tereleminasi.

---

### 3.4 Normalisasi

> **Normalisasi** adalah teknik untuk menghitung probabilitas posterior tanpa perlu menghitung $P(E)$ secara eksplisit.

Perhatikan bahwa dalam Teorema Bayes, $P(E)$ hanya berfungsi sebagai **konstanta normalisasi** agar semua posterior berjumlah 1.

Proses normalisasi:
1. Hitung **numerator** untuk setiap hipotesis: $P(E \mid H_i) \cdot P(H_i)$
2. Jumlahkan semua numerator untuk mendapatkan $P(E)$
3. Bagi setiap numerator dengan jumlah total

Notasi ringkas:

$$P(H \mid E) = \alpha \cdot P(E \mid H) \cdot P(H)$$

dimana $\alpha = 1/P(E)$ adalah **konstanta normalisasi**.

#### Solved Problem 10 ⭐

**Soal:** Menggunakan normalisasi, hitung probabilitas sebuah email adalah spam, diketahui email mengandung kata "gratis". Data: $P(\text{Spam}) = 0.4$, $P(\text{Ham}) = 0.6$, $P(\text{"gratis"} \mid \text{Spam}) = 0.8$, $P(\text{"gratis"} \mid \text{Ham}) = 0.1$.

**Penyelesaian:**

*Step 1:* Hitung numerator (unnormalized posterior)
- Spam: $P(\text{"gratis"} \mid \text{Spam}) \times P(\text{Spam}) = 0.8 \times 0.4 = 0.32$
- Ham: $P(\text{"gratis"} \mid \text{Ham}) \times P(\text{Ham}) = 0.1 \times 0.6 = 0.06$

*Step 2:* Jumlahkan untuk normalisasi
- Total = $0.32 + 0.06 = 0.38$

*Step 3:* Normalisasi
- $P(\text{Spam} \mid \text{"gratis"}) = 0.32 / 0.38 = 0.842$
- $P(\text{Ham} \mid \text{"gratis"}) = 0.06 / 0.38 = 0.158$

*Step 4:* Verifikasi: $0.842 + 0.158 = 1.0$ ✓

**Jawaban:** $P(\text{Spam} \mid \text{"gratis"}) = 0.842$ atau 84.2%. Email yang mengandung kata "gratis" memiliki probabilitas tinggi untuk menjadi spam.

---

## 4. Independensi dan Independensi Bersyarat

### 4.1 Independensi (Independence)

> Dua event A dan B **independen** jika dan hanya jika: $P(A, B) = P(A) \cdot P(B)$

Equivalen dengan: $P(A \mid B) = P(A)$ — artinya mengetahui B tidak mengubah probabilitas A.

**Contoh independen:** Hasil lemparan dadu pertama dan kedua.

**Contoh tidak independen:** Cuaca dan keberhasilan misi drone.

**Mengapa independensi penting?**

Tanpa independensi, full joint distribution memerlukan penyimpanan eksponensial:
- Untuk $n$ variabel boolean: perlu $2^n - 1$ parameter
- Contoh: 10 variabel boolean → 1.023 parameter
- Contoh: 30 variabel boolean → lebih dari 1 miliar parameter

Dengan asumsi independensi: hanya perlu $n$ parameter!

#### Solved Problem 11 ⭐

**Soal:** Apakah event "Sensor A mendeteksi objek" dan "Sensor B mendeteksi objek" independen jika kedua sensor mengawasi area yang sama? Jelaskan!

**Penyelesaian:**

*Step 1:* Analisis kondisi

Kedua sensor mengawasi area yang sama, artinya jika ada objek, kemungkinan besar kedua sensor mendeteksinya.

*Step 2:* Uji independensi

Jika ada objek di area:
- $P(A \text{ deteksi} \mid \text{objek ada}) = 0.95$
- $P(B \text{ deteksi} \mid \text{objek ada}) = 0.90$
- $P(A \text{ deteksi}, B \text{ deteksi} \mid \text{objek ada}) \approx 0.855$

Jika independen, seharusnya: $0.95 \times 0.90 = 0.855$

Tampaknya independen? **Tidak selalu!** Faktor lingkungan (kabut, jamming) mempengaruhi kedua sensor bersamaan, sehingga:
- Saat ada kabut tebal: kedua sensor sama-sama performanya turun
- Ini membuat deteksi keduanya **berkorelasi**

**Jawaban:** Kedua sensor **tidak sepenuhnya independen** karena faktor lingkungan yang sama (cuaca, jamming, obstacles) mempengaruhi kedua sensor bersamaan. Namun, **given kondisi lingkungan tertentu**, deteksi kedua sensor mungkin mendekati independen — ini adalah konsep **conditional independence**.

---

### 4.2 Independensi Bersyarat (Conditional Independence)

> Dua event A dan B **conditionally independent** given C jika: $P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$

Atau equivalen: $P(A \mid B, C) = P(A \mid C)$

Artinya: jika kita sudah mengetahui C, mengetahui B tidak memberikan informasi tambahan tentang A.

**Contoh klasik:**

| Variabel | Deskripsi |
|----------|-----------|
| $C$ (Cause) | Cuaca buruk |
| $A$ (Effect 1) | Traffic macet |
| $B$ (Effect 2) | Penerbangan delay |

- $A$ dan $B$ **tidak independen** (keduanya cenderung terjadi bersamaan)
- $A$ dan $B$ **conditionally independent given $C$**: Jika kita tahu cuaca buruk, mengetahui traffic macet tidak menambah informasi tentang penerbangan delay

![Independensi Bersyarat](images/p11-03-conditional-independence.png)

*Gambar 11.3: Visualisasi independensi bersyarat — effect yang sama-sama disebabkan cause yang sama*

**Mengapa conditional independence sangat penting?**

Conditional independence memungkinkan dekomposisi joint probability yang lebih efisien:

$$P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$$

Ini mengurangi jumlah parameter yang perlu disimpan secara drastis. Konsep ini menjadi fondasi **Jaringan Bayesian** yang akan dibahas pada **Pertemuan 12**.

#### Solved Problem 12 ⭐⭐

**Soal:** Pada sistem pertahanan udara, dua radar ($R_1$ dan $R_2$) mendeteksi ancaman secara independen given jenis ancaman. Jika ancaman adalah pesawat tempur ($H$), $P(R_1 = \text{positif} \mid H) = 0.90$ dan $P(R_2 = \text{positif} \mid H) = 0.85$. Jika bukan ancaman ($\neg H$), $P(R_1 = \text{positif} \mid \neg H) = 0.05$ dan $P(R_2 = \text{positif} \mid \neg H) = 0.08$. Prior $P(H) = 0.02$. Hitung probabilitas ancaman jika kedua radar positif!

**Penyelesaian:**

*Step 1:* Karena $R_1$ dan $R_2$ conditionally independent given $H$:

$$P(R_1^+, R_2^+ \mid H) = P(R_1^+ \mid H) \cdot P(R_2^+ \mid H) = 0.90 \times 0.85 = 0.765$$

$$P(R_1^+, R_2^+ \mid \neg H) = P(R_1^+ \mid \neg H) \cdot P(R_2^+ \mid \neg H) = 0.05 \times 0.08 = 0.004$$

*Step 2:* Terapkan Bayes

Numerator:
- $H$: $0.765 \times 0.02 = 0.0153$
- $\neg H$: $0.004 \times 0.98 = 0.00392$

*Step 3:* Normalisasi

Total = $0.0153 + 0.00392 = 0.01922$

$$P(H \mid R_1^+, R_2^+) = \frac{0.0153}{0.01922} = 0.7961$$

**Jawaban:** $P(H \mid R_1^+, R_2^+) = 0.796$ atau 79.6%. Dengan dua radar independen memberikan sinyal positif, probabilitas ancaman naik dari 2% menjadi hampir 80%. Ini menunjukkan nilai dari **sensor fusion** — menggabungkan data dari multiple sensor meningkatkan kepercayaan secara signifikan.

#### Solved Problem 13 ⭐⭐

**Soal:** Buktikan bahwa jika $A$ dan $B$ independen, maka $A$ dan $\neg B$ juga independen!

**Penyelesaian:**

*Step 1:* Diketahui $A \perp B$, artinya $P(A, B) = P(A) \cdot P(B)$

*Step 2:* Kita tahu bahwa $P(A) = P(A, B) + P(A, \neg B)$

*Step 3:* Sehingga:
$$P(A, \neg B) = P(A) - P(A, B)$$
$$P(A, \neg B) = P(A) - P(A) \cdot P(B) \quad \text{(karena independen)}$$
$$P(A, \neg B) = P(A) \cdot (1 - P(B))$$
$$P(A, \neg B) = P(A) \cdot P(\neg B)$$

*Step 4:* Ini memenuhi definisi independensi

**Jawaban:** Terbukti. Jika $P(A, B) = P(A) \cdot P(B)$, maka $P(A, \neg B) = P(A) \cdot P(\neg B)$, sehingga $A$ dan $\neg B$ juga independen. ∎

---

## 5. Naive Bayes Classifier

### 5.1 Konsep Naive Bayes

> **Naive Bayes Classifier** adalah model probabilistik yang menggunakan Teorema Bayes dengan asumsi **conditional independence** antar fitur (features) given kelas (class).

Untuk klasifikasi dengan kelas $C$ dan fitur $x_1, x_2, ..., x_n$:

$$P(C \mid x_1, x_2, ..., x_n) = \frac{P(C) \cdot \prod_{i=1}^{n} P(x_i \mid C)}{P(x_1, x_2, ..., x_n)}$$

Karena penyebut sama untuk semua kelas:

$$P(C \mid x_1, ..., x_n) \propto P(C) \cdot \prod_{i=1}^{n} P(x_i \mid C)$$

Prediksi: pilih kelas dengan probabilitas posterior tertinggi:

$$\hat{C} = \arg\max_C P(C) \cdot \prod_{i=1}^{n} P(x_i \mid C)$$

![Naive Bayes Classifier](images/p11-04-naive-bayes-structure.png)

*Gambar 11.4: Struktur Naive Bayes — kelas sebagai parent, fitur sebagai children yang conditionally independent*

### 5.2 Mengapa "Naive"?

Asumsi conditional independence antar fitur disebut "naive" karena **sering tidak benar** di dunia nyata. Namun, meskipun asumsi ini dilanggar, Naive Bayes sering memberikan hasil klasifikasi yang **cukup baik** dalam praktik.

| Kelebihan | Kekurangan |
|-----------|------------|
| Sederhana dan cepat | Asumsi independensi sering tidak realistis |
| Bekerja baik dengan data sedikit | Tidak memodelkan korelasi antar fitur |
| Mudah diinterpretasi | Estimasi probabilitas bisa buruk |
| Robust terhadap fitur irrelevant | Sensitif terhadap fitur yang sangat berkorelasi |

### 5.3 Contoh Aplikasi: Spam Filter

Salah satu aplikasi paling sukses Naive Bayes adalah **spam filtering**.

- Kelas: $C \in \{\text{Spam}, \text{Ham}\}$
- Fitur: kehadiran kata-kata tertentu dalam email ($x_i = 1$ jika kata $i$ ada, $x_i = 0$ jika tidak)

#### Solved Problem 14 ⭐⭐

**Soal:** Buat spam classifier menggunakan Naive Bayes dengan data training berikut:

| Email | "diskon" | "gratis" | "rapat" | "laporan" | Kelas |
|-------|:---:|:---:|:---:|:---:|-------|
| 1 | 1 | 1 | 0 | 0 | Spam |
| 2 | 1 | 0 | 0 | 0 | Spam |
| 3 | 0 | 1 | 0 | 1 | Spam |
| 4 | 0 | 0 | 1 | 1 | Ham |
| 5 | 0 | 0 | 1 | 0 | Ham |
| 6 | 1 | 0 | 1 | 1 | Ham |

Klasifikasikan email baru dengan fitur: "diskon"=1, "gratis"=0, "rapat"=1, "laporan"=0.

**Penyelesaian:**

*Step 1:* Hitung prior
- $P(\text{Spam}) = 3/6 = 0.5$
- $P(\text{Ham}) = 3/6 = 0.5$

*Step 2:* Hitung likelihood untuk setiap fitur given kelas

**P(fitur | Spam):**

| Fitur | P(fitur=1 \| Spam) | P(fitur=0 \| Spam) |
|-------|:---:|:---:|
| "diskon" | 2/3 | 1/3 |
| "gratis" | 2/3 | 1/3 |
| "rapat" | 0/3 = 0 | 3/3 |
| "laporan" | 1/3 | 2/3 |

**P(fitur | Ham):**

| Fitur | P(fitur=1 \| Ham) | P(fitur=0 \| Ham) |
|-------|:---:|:---:|
| "diskon" | 1/3 | 2/3 |
| "gratis" | 0/3 = 0 | 3/3 |
| "rapat" | 3/3 | 0/3 = 0 |
| "laporan" | 2/3 | 1/3 |

> ⚠️ **Masalah zero probability!** $P(\text{"rapat"} = 1 \mid \text{Spam}) = 0$ dan $P(\text{"gratis"} = 1 \mid \text{Ham}) = 0$. Ini akan membuat seluruh produk menjadi 0. Solusi: **Laplace Smoothing** (lihat Solved Problem 15).

*Step 3:* Untuk saat ini, gunakan Laplace smoothing $(k=1)$:

$P_{smooth}(x_i = 1 \mid C) = \frac{count(x_i=1, C) + 1}{count(C) + 2}$

**Smoothed P(fitur | Spam):**

| Fitur | P(fitur=1 \| Spam) |
|-------|:---:|
| "diskon" | (2+1)/(3+2) = 3/5 |
| "gratis" | (2+1)/(3+2) = 3/5 |
| "rapat" | (0+1)/(3+2) = 1/5 |
| "laporan" | (1+1)/(3+2) = 2/5 |

**Smoothed P(fitur | Ham):**

| Fitur | P(fitur=1 \| Ham) |
|-------|:---:|
| "diskon" | (1+1)/(3+2) = 2/5 |
| "gratis" | (0+1)/(3+2) = 1/5 |
| "rapat" | (3+1)/(3+2) = 4/5 |
| "laporan" | (2+1)/(3+2) = 3/5 |

*Step 4:* Hitung untuk email baru: "diskon"=1, "gratis"=0, "rapat"=1, "laporan"=0

**Spam:**
$$P(\text{Spam}) \times P(\text{diskon}=1 \mid S) \times P(\text{gratis}=0 \mid S) \times P(\text{rapat}=1 \mid S) \times P(\text{laporan}=0 \mid S)$$
$$= 0.5 \times \frac{3}{5} \times \frac{2}{5} \times \frac{1}{5} \times \frac{3}{5} = 0.5 \times 0.6 \times 0.4 \times 0.2 \times 0.6 = 0.0144$$

**Ham:**
$$P(\text{Ham}) \times P(\text{diskon}=1 \mid H) \times P(\text{gratis}=0 \mid H) \times P(\text{rapat}=1 \mid H) \times P(\text{laporan}=0 \mid H)$$
$$= 0.5 \times \frac{2}{5} \times \frac{4}{5} \times \frac{4}{5} \times \frac{2}{5} = 0.5 \times 0.4 \times 0.8 \times 0.8 \times 0.4 = 0.0512$$

*Step 5:* Normalisasi

Total = $0.0144 + 0.0512 = 0.0656$
- $P(\text{Spam} \mid \text{email}) = 0.0144 / 0.0656 = 0.220$
- $P(\text{Ham} \mid \text{email}) = 0.0512 / 0.0656 = 0.780$

**Jawaban:** Email diklasifikasikan sebagai **Ham** (bukan spam) dengan probabilitas 78.0%. Kehadiran kata "rapat" yang sangat berkorelasi dengan Ham menjadi faktor dominan meskipun ada kata "diskon".

#### Solved Problem 15 ⭐

**Soal:** Jelaskan apa itu Laplace Smoothing dan mengapa diperlukan dalam Naive Bayes!

**Penyelesaian:**

*Step 1:* Identifikasi masalah

Tanpa smoothing, jika sebuah fitur tidak pernah muncul untuk suatu kelas di training data, $P(x_i \mid C) = 0$. Karena Naive Bayes mengalikan semua likelihood, **satu zero akan membuat seluruh produk menjadi nol**.

*Step 2:* Definisi Laplace Smoothing

> **Laplace Smoothing** (additive smoothing) menambahkan pseudocount $k$ (biasanya $k=1$) ke setiap kemungkinan:

$$P_{smooth}(x_i = v \mid C) = \frac{count(x_i = v, C) + k}{count(C) + k \cdot |V|}$$

dimana $|V|$ = jumlah nilai yang mungkin untuk fitur $x_i$ (untuk binary: $|V| = 2$).

*Step 3:* Contoh
- Tanpa smoothing: $P(\text{"rapat"} = 1 \mid \text{Spam}) = 0/3 = 0$ → seluruh produk = 0
- Dengan smoothing ($k=1$): $P(\text{"rapat"} = 1 \mid \text{Spam}) = (0+1)/(3+2) = 1/5 = 0.2$

**Jawaban:** Laplace Smoothing menambahkan pseudocount ke setiap fitur-kelas untuk menghindari probabilitas nol. Ini diperlukan karena satu probabilitas nol dalam Naive Bayes akan mengeliminasi seluruh kelas, meskipun bukti lain mendukung kelas tersebut.

---

### 5.4 Aplikasi Naive Bayes dalam Konteks Pertahanan

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Sebuah sistem klasifikasi target radar harus mengklasifikasikan objek sebagai "Pesawat Tempur" ($C_1$), "Pesawat Sipil" ($C_2$), atau "Drone" ($C_3$). Fitur-fitur yang digunakan: kecepatan ($x_1$: rendah/tinggi), altitude ($x_2$: rendah/tinggi), dan radar cross-section ($x_3$: kecil/besar). Data training:

| Prior | $P(C_i)$ |
|-------|-----------|
| Pesawat Tempur | 0.15 |
| Pesawat Sipil | 0.70 |
| Drone | 0.15 |

| Likelihood | P(tinggi \| $C_1$) | P(tinggi \| $C_2$) | P(tinggi \| $C_3$) |
|------------|:---:|:---:|:---:|
| Kecepatan ($x_1$) | 0.90 | 0.80 | 0.10 |
| Altitude ($x_2$) | 0.70 | 0.85 | 0.20 |
| RCS ($x_3$ = besar) | 0.60 | 0.90 | 0.05 |

Objek terdeteksi dengan: kecepatan tinggi, altitude rendah, RCS kecil. Klasifikasikan!

**Penyelesaian:**

*Step 1:* Tentukan fitur objek
- $x_1$ = tinggi, $x_2$ = rendah, $x_3$ = kecil

*Step 2:* Hitung likelihood complement (untuk "rendah" dan "kecil")
- $P(x_2 = \text{rendah} \mid C_i) = 1 - P(x_2 = \text{tinggi} \mid C_i)$
- $P(x_3 = \text{kecil} \mid C_i) = 1 - P(x_3 = \text{besar} \mid C_i)$

*Step 3:* Hitung posterior unnormalized untuk setiap kelas

**Pesawat Tempur ($C_1$):**
$$P(C_1) \times P(x_1=\text{tinggi} \mid C_1) \times P(x_2=\text{rendah} \mid C_1) \times P(x_3=\text{kecil} \mid C_1)$$
$$= 0.15 \times 0.90 \times 0.30 \times 0.40 = 0.0162$$

**Pesawat Sipil ($C_2$):**
$$= 0.70 \times 0.80 \times 0.15 \times 0.10 = 0.0084$$

**Drone ($C_3$):**
$$= 0.15 \times 0.10 \times 0.80 \times 0.95 = 0.0114$$

*Step 4:* Normalisasi

Total = $0.0162 + 0.0084 + 0.0114 = 0.0360$

| Kelas | Unnormalized | **Posterior** |
|-------|:---:|:---:|
| Pesawat Tempur | 0.0162 | **0.450** |
| Pesawat Sipil | 0.0084 | 0.233 |
| Drone | 0.0114 | 0.317 |

*Step 5:* Verifikasi: $0.450 + 0.233 + 0.317 = 1.000$ ✓

**Jawaban:** Objek diklasifikasikan sebagai **Pesawat Tempur** dengan probabilitas posterior 45.0%. Meskipun pesawat sipil memiliki prior tertinggi (70%), kombinasi kecepatan tinggi + altitude rendah + RCS kecil lebih konsisten dengan profil pesawat tempur. Namun, probabilitasnya tidak sangat tinggi, menunjukkan ketidakpastian yang signifikan — sistem perlu meminta konfirmasi atau data tambahan.

---

## 6. Penerapan dalam Konteks AI

### 6.1 Alur Inferensi Probabilistik dalam AI

![Alur Inferensi Probabilistik](images/p11-05-probabilistic-inference-flow.png)

*Gambar 11.5: Alur inferensi probabilistik dalam sistem AI*

### 6.2 Koneksi dengan Topik Lain

| Topik Terkait | Koneksi dengan Probabilitas |
|---------------|----------------------------|
| **Jaringan Bayesian** (Pertemuan 12) | Menggunakan conditional independence untuk representasi compact |
| **Machine Learning** (Pertemuan 13-14) | Naive Bayes sebagai classifier, probabilitas untuk evaluasi model |
| **Pencarian dengan Ketidakpastian** (Pertemuan 4) | Simulated annealing menggunakan probabilitas |
| **Utility-Based Agent** (Pertemuan 1) | Expected utility = $\sum P(outcome) \times U(outcome)$ |

#### Solved Problem 17 ⭐⭐

**Soal:** Sebuah utility-based agent untuk drone militer harus memutuskan antara dua aksi: Patroli ($a_1$) atau Kembali ke Base ($a_2$). Probabilitas cuaca memburuk adalah 0.3. Utility table:

| | Cuaca Baik (0.7) | Cuaca Buruk (0.3) |
|---|:---:|:---:|
| Patroli ($a_1$) | 80 | -20 |
| Kembali ($a_2$) | 30 | 50 |

Tentukan aksi rasional menggunakan expected utility!

**Penyelesaian:**

*Step 1:* Hitung expected utility untuk setiap aksi

$$EU(a_1) = P(\text{Baik}) \times U(a_1, \text{Baik}) + P(\text{Buruk}) \times U(a_1, \text{Buruk})$$
$$EU(a_1) = 0.7 \times 80 + 0.3 \times (-20) = 56 - 6 = 50$$

$$EU(a_2) = 0.7 \times 30 + 0.3 \times 50 = 21 + 15 = 36$$

*Step 2:* Bandingkan

| Aksi | Expected Utility |
|------|:---:|
| Patroli ($a_1$) | **50** |
| Kembali ($a_2$) | 36 |

**Jawaban:** Aksi rasional adalah **Patroli** ($a_1$) dengan expected utility 50. Meskipun ada risiko cuaca buruk, expected utility patroli masih lebih tinggi.

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Melanjutkan soal sebelumnya, jika sebelum memutuskan, drone menerima laporan cuaca yang mengatakan "kemungkinan cuaca akan buruk". Laporan cuaca memiliki akurasi: $P(\text{laporan buruk} \mid \text{cuaca buruk}) = 0.80$ dan $P(\text{laporan buruk} \mid \text{cuaca baik}) = 0.15$. Perbarui probabilitas cuaca dan tentukan ulang aksi rasional!

**Penyelesaian:**

*Step 1:* Update probabilitas cuaca menggunakan Bayes

Prior: $P(\text{Buruk}) = 0.3$, $P(\text{Baik}) = 0.7$

$$P(\text{Buruk} \mid \text{laporan buruk}) = \frac{P(\text{laporan buruk} \mid \text{Buruk}) \times P(\text{Buruk})}{P(\text{laporan buruk})}$$

$$P(\text{laporan buruk}) = 0.80 \times 0.3 + 0.15 \times 0.7 = 0.24 + 0.105 = 0.345$$

$$P(\text{Buruk} \mid \text{laporan buruk}) = \frac{0.24}{0.345} = 0.6957$$

$$P(\text{Baik} \mid \text{laporan buruk}) = 1 - 0.6957 = 0.3043$$

*Step 2:* Hitung ulang expected utility dengan probabilitas baru

$$EU(a_1) = 0.3043 \times 80 + 0.6957 \times (-20) = 24.34 - 13.91 = 10.43$$

$$EU(a_2) = 0.3043 \times 30 + 0.6957 \times 50 = 9.13 + 34.79 = 43.92$$

*Step 3:* Bandingkan

| Aksi | EU (sebelum laporan) | EU (setelah laporan) |
|------|:---:|:---:|
| Patroli ($a_1$) | 50 | 10.43 |
| Kembali ($a_2$) | 36 | **43.92** |

**Jawaban:** Setelah menerima laporan cuaca buruk, aksi rasional berubah menjadi **Kembali ke Base** ($a_2$) dengan EU = 43.92. Laporan cuaca mengubah probabilitas cuaca buruk dari 30% menjadi ~70%, yang secara dramatis mengubah keputusan optimal. Ini menunjukkan pentingnya **Bayesian updating** dalam pengambilan keputusan agen cerdas.

---

### 6.3 Diagnosis sebagai Inferensi Probabilistik

#### Solved Problem 19 ⭐⭐

**Soal:** Sistem diagnosis kerusakan kapal perang mendeteksi dua gejala: suhu mesin tinggi ($s_1$) dan getaran abnormal ($s_2$). Tiga kemungkinan penyebab: bearing rusak ($H_1$, prior 0.30), sistem pendingin bermasalah ($H_2$, prior 0.50), overload ($H_3$, prior 0.20). Likelihood:

| | P($s_1$ \| $H_i$) | P($s_2$ \| $H_i$) |
|---|:---:|:---:|
| Bearing rusak ($H_1$) | 0.7 | 0.9 |
| Pendingin ($H_2$) | 0.9 | 0.3 |
| Overload ($H_3$) | 0.6 | 0.5 |

Asumsikan gejala conditionally independent given penyebab. Hitung posterior!

**Penyelesaian:**

*Step 1:* Hitung gabungan likelihood (asumsi conditional independence)

$$P(s_1, s_2 \mid H_1) = 0.7 \times 0.9 = 0.63$$
$$P(s_1, s_2 \mid H_2) = 0.9 \times 0.3 = 0.27$$
$$P(s_1, s_2 \mid H_3) = 0.6 \times 0.5 = 0.30$$

*Step 2:* Hitung unnormalized posterior

$$H_1: 0.63 \times 0.30 = 0.189$$
$$H_2: 0.27 \times 0.50 = 0.135$$
$$H_3: 0.30 \times 0.20 = 0.060$$

*Step 3:* Normalisasi

Total = $0.189 + 0.135 + 0.060 = 0.384$

| Penyebab | Prior | Posterior |
|----------|:---:|:---:|
| Bearing rusak ($H_1$) | 0.30 | **0.492** |
| Pendingin ($H_2$) | 0.50 | 0.352 |
| Overload ($H_3$) | 0.20 | 0.156 |

**Jawaban:** Penyebab paling mungkin adalah **bearing rusak** dengan posterior 49.2%. Meskipun sistem pendingin memiliki prior tertinggi (50%), kombinasi kedua gejala — khususnya getaran abnormal yang sangat berkorelasi dengan bearing rusak — menggeser diagnosis ke bearing rusak.

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Dalam skenario Solved Problem 19, teknisi melakukan pemeriksaan tambahan dan menemukan gejala baru: suara berdecit ($s_3$). Diketahui $P(s_3 \mid H_1) = 0.95$, $P(s_3 \mid H_2) = 0.10$, $P(s_3 \mid H_3) = 0.20$. Perbarui diagnosis menggunakan posterior sebelumnya sebagai prior baru!

**Penyelesaian:**

*Step 1:* Gunakan posterior sebelumnya sebagai prior baru

| $H_i$ | Prior Baru (=Posterior sebelumnya) |
|--------|:---:|
| $H_1$ | 0.492 |
| $H_2$ | 0.352 |
| $H_3$ | 0.156 |

*Step 2:* Hitung unnormalized posterior

$$H_1: P(s_3 \mid H_1) \times P(H_1) = 0.95 \times 0.492 = 0.4674$$
$$H_2: P(s_3 \mid H_2) \times P(H_2) = 0.10 \times 0.352 = 0.0352$$
$$H_3: P(s_3 \mid H_3) \times P(H_3) = 0.20 \times 0.156 = 0.0312$$

*Step 3:* Normalisasi

Total = $0.4674 + 0.0352 + 0.0312 = 0.5338$

| Penyebab | Prior (sebelum $s_3$) | **Posterior (setelah $s_3$)** |
|----------|:---:|:---:|
| Bearing rusak ($H_1$) | 0.492 | **0.876** |
| Pendingin ($H_2$) | 0.352 | 0.066 |
| Overload ($H_3$) | 0.156 | 0.058 |

**Jawaban:** Setelah bukti suara berdecit, probabilitas bearing rusak meningkat dari 49.2% menjadi **87.6%**. Gejala suara berdecit sangat diskriminatif — hampir eksklusif pada bearing rusak — sehingga secara drastis meningkatkan kepercayaan terhadap $H_1$. Sistem diagnosis sekarang cukup yakin untuk merekomendasikan penggantian bearing.

---

## 7. Koneksi dengan Pertemuan Selanjutnya

### 7.1 Menuju Jaringan Bayesian (Pertemuan 12)

Pada pertemuan ini, kita menghitung probabilitas menggunakan Teorema Bayes secara langsung. Namun, untuk domain yang kompleks dengan banyak variabel, pendekatan ini menjadi tidak praktis karena:

1. **Full joint distribution** terlalu besar ($2^n$ entries untuk $n$ variabel boolean)
2. Perlu cara **representasi compact** yang memanfaatkan conditional independence

> **Jaringan Bayesian** (akan dibahas pada **Pertemuan 12**) adalah representasi grafis yang menangkap hubungan conditional independence antar variabel, memungkinkan inferensi efisien pada domain yang kompleks.

#### Solved Problem 21 ⭐⭐

**Soal:** Sebuah domain memiliki 5 variabel boolean. (a) Berapa parameter yang diperlukan untuk full joint distribution? (b) Jika kita menggunakan Naive Bayes dengan 1 variabel kelas dan 4 variabel fitur, berapa parameter yang diperlukan?

**Penyelesaian:**

*Step 1:* Hitung full joint distribution

Untuk 5 variabel boolean:
- Total kemungkinan kombinasi: $2^5 = 32$
- Parameter yang diperlukan: $32 - 1 = 31$ (dikurangi 1 karena constraint normalisasi)

*Step 2:* Hitung Naive Bayes parameters

Naive Bayes dengan 1 kelas (binary) dan 4 fitur (binary):
- Prior kelas: 1 parameter ($P(C)$; $P(\neg C) = 1 - P(C)$)
- Likelihood per fitur per kelas: $4 \times 2 = 8$ parameter
- Total: $1 + 8 = 9$ parameter

*Step 3:* Bandingkan

| Representasi | Parameter |
|-------------|:---------:|
| Full Joint Distribution | 31 |
| Naive Bayes | 9 |
| **Penghematan** | **71%** |

**Jawaban:** (a) 31 parameter, (b) 9 parameter. Naive Bayes menghemat 71% parameter berkat asumsi conditional independence. Untuk 20 variabel, penghematan menjadi lebih dramatis: $2^{20} - 1 \approx 1$ juta vs $1 + 2 \times 19 = 39$ parameter.

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Sebuah sistem surveillance maritim memantau 3 variabel: Kapal Asing Terdeteksi ($K$), Aktivitas Komunikasi Meningkat ($A$), dan Cuaca Buruk ($C$). Diberikan full joint distribution:

| K | A | C | P(K, A, C) |
|:---:|:---:|:---:|:---:|
| T | T | T | 0.01 |
| T | T | F | 0.04 |
| T | F | T | 0.02 |
| T | F | F | 0.03 |
| F | T | T | 0.05 |
| F | T | F | 0.15 |
| F | F | T | 0.20 |
| F | F | F | 0.50 |

Hitung: (a) $P(K)$, (b) $P(A \mid K)$, (c) $P(K \mid A, \neg C)$, (d) Apakah $A$ dan $C$ independen?

**Penyelesaian:**

*Step 1:* (a) $P(K)$ — marginalisasi terhadap A dan C

$$P(K) = P(K,T,T) + P(K,T,F) + P(K,F,T) + P(K,F,F)$$
$$P(K) = 0.01 + 0.04 + 0.02 + 0.03 = 0.10$$

*Step 2:* (b) $P(A \mid K)$

$$P(A, K) = P(K,T,T) + P(K,T,F) = 0.01 + 0.04 = 0.05$$

$$P(A \mid K) = \frac{P(A, K)}{P(K)} = \frac{0.05}{0.10} = 0.50$$

*Step 3:* (c) $P(K \mid A, \neg C)$

$$P(K, A, \neg C) = 0.04$$
$$P(A, \neg C) = P(K, A, \neg C) + P(\neg K, A, \neg C) = 0.04 + 0.15 = 0.19$$

$$P(K \mid A, \neg C) = \frac{0.04}{0.19} = 0.2105$$

*Step 4:* (d) Cek independensi $A$ dan $C$

$$P(A) = 0.01 + 0.04 + 0.05 + 0.15 = 0.25$$
$$P(C) = 0.01 + 0.02 + 0.05 + 0.20 = 0.28$$
$$P(A) \times P(C) = 0.25 \times 0.28 = 0.070$$

$$P(A, C) = 0.01 + 0.05 = 0.06$$

Karena $P(A, C) = 0.06 \neq 0.070 = P(A) \times P(C)$:

**Jawaban:**
(a) $P(K) = 0.10$ (10%)
(b) $P(A \mid K) = 0.50$ (50%) — aktivitas komunikasi meningkat 2× lipat saat ada kapal asing
(c) $P(K \mid A, \neg C) = 0.211$ (21.1%) — cuaca baik + komunikasi meningkat → 21% kemungkinan kapal asing
(d) $A$ dan $C$ **tidak independen** karena $P(A, C) = 0.06 \neq 0.070 = P(A) \cdot P(C)$

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Sebuah tes keamanan siber memiliki true positive rate 90% dan false positive rate 5%. Jika probabilitas serangan siber pada hari tertentu adalah 1%, berapa probabilitas serangan benar terjadi jika alarm berbunyi?

**Jawaban:** Menggunakan Bayes: $P(H \mid E) = \frac{0.90 \times 0.01}{0.90 \times 0.01 + 0.05 \times 0.99} = \frac{0.009}{0.009 + 0.0495} = \frac{0.009}{0.0585} = 0.154$ atau 15.4%.

---

### Problem S2 ⭐
**Soal:** Jika $P(A) = 0.4$ dan $P(B) = 0.3$, serta $A$ dan $B$ independen, hitung $P(A \cup B)$.

**Jawaban:** $P(A \cup B) = P(A) + P(B) - P(A,B) = 0.4 + 0.3 - (0.4 \times 0.3) = 0.7 - 0.12 = 0.58$

---

### Problem S3 ⭐⭐
**Soal:** Dua intel lapangan memberikan penilaian independen tentang ancaman: Intel A mengatakan "bahaya" (akurasi 85%), Intel B mengatakan "aman" (akurasi 90%). Prior ancaman = 0.20. Hitung posterior ancaman!

**Jawaban:** $P(\text{bahaya}_A, \text{aman}_B \mid H) = 0.85 \times 0.10 = 0.085$; $P(\text{bahaya}_A, \text{aman}_B \mid \neg H) = 0.15 \times 0.90 = 0.135$. Posterior: $\frac{0.085 \times 0.20}{0.085 \times 0.20 + 0.135 \times 0.80} = \frac{0.017}{0.017 + 0.108} = 0.136$ atau 13.6%. Ancaman turun dari 20% menjadi 13.6%.

---

### Problem S4 ⭐⭐
**Soal:** Jelaskan mengapa Naive Bayes disebut "naive" dan berikan contoh di mana asumsi independensi sangat dilanggar!

**Jawaban:** Disebut "naive" karena mengasumsikan semua fitur independen given kelas, yang jarang benar. Contoh pelanggaran: dalam deteksi spam, kata "gratis" dan "diskon" sangat berkorelasi (keduanya sering muncul bersama di email spam). Menganggap keduanya independen meng-overcount bukti spam. Namun, meskipun asumsi dilanggar, Naive Bayes sering tetap memberikan klasifikasi yang benar.

---

### Problem S5 ⭐⭐⭐
**Soal:** Buktikan bahwa Bayesian updating bersifat order-independent: $P(H \mid E_1, E_2) = P(H \mid E_2, E_1)$ jika $E_1$ dan $E_2$ conditionally independent given $H$.

**Jawaban:** 
$$P(H \mid E_1, E_2) = \frac{P(E_1, E_2 \mid H) P(H)}{P(E_1, E_2)} = \frac{P(E_1 \mid H) P(E_2 \mid H) P(H)}{P(E_1, E_2)}$$

Karena perkalian bersifat komutatif: $P(E_1 \mid H) P(E_2 \mid H) = P(E_2 \mid H) P(E_1 \mid H)$

Sehingga hasilnya sama terlepas dari urutan evidence. ∎

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Ketidakpastian** | Muncul dari laziness, ignorance, sensor noise, dan non-determinism |
| **Probabilitas** | Ukuran numerik derajat kepercayaan (0 sampai 1) |
| **Prior** | Probabilitas awal sebelum bukti baru |
| **Posterior** | Probabilitas setelah bukti baru (hasil Teorema Bayes) |
| **Teorema Bayes** | $P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)}$ |
| **Total Probability** | $P(E) = \sum_i P(E \mid H_i) \cdot P(H_i)$ |
| **Normalisasi** | Teknik menghitung posterior tanpa P(E) eksplisit |
| **Independensi** | $P(A, B) = P(A) \cdot P(B)$ |
| **Conditional Independence** | $P(A, B \mid C) = P(A \mid C) \cdot P(B \mid C)$ |
| **Naive Bayes** | Classifier berbasis Bayes dengan asumsi conditional independence |
| **Laplace Smoothing** | Menambah pseudocount untuk menghindari zero probability |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 12-13**.
2. Bishop, C.M. (2006). *Pattern Recognition and Machine Learning*. Springer. **Chapter 1-2**.
3. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press.
4. Mitchell, T. (1997). *Machine Learning*. McGraw-Hill. **Chapter 6**.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
