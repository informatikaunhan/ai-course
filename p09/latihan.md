# Latihan Pertemuan 09: Representasi Pengetahuan — Logika Proposisional

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 09  
**Topik:** Representasi Pengetahuan — Logika Proposisional  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Petunjuk Pengerjaan

1. Kerjakan semua soal secara mandiri
2. Waktu pengerjaan: 120 menit
3. Untuk soal pilihan ganda, pilih satu jawaban yang paling tepat
4. Untuk soal uraian, jawab dengan lengkap dan sistematis
5. Studi kasus memerlukan analisis mendalam dan penerapan konsep

---

## Bagian A: Soal Pilihan Ganda (20 Soal)

### Soal 1
Manakah yang merupakan proposisi valid dalam logika proposisional?

A. "Berapa jumlah pasukan?"  
B. "Kirim drone ke sektor 7!"  
C. "Radar mendeteksi objek di koordinat Alpha"  
D. "x + 5 = 10"  
E. "Semoga misi berhasil"

---

### Soal 2
Dalam knowledge-based agent, operasi yang digunakan untuk menambahkan fakta baru ke Knowledge Base adalah:

A. ASK  
B. QUERY  
C. TELL  
D. INSERT  
E. ASSERT

---

### Soal 3
Implikasi P ⇒ Q bernilai False jika dan hanya jika:

A. P = False dan Q = False  
B. P = False dan Q = True  
C. P = True dan Q = True  
D. P = True dan Q = False  
E. P = False, terlepas dari nilai Q

---

### Soal 4
Berapa jumlah model (interpretasi) yang mungkin jika terdapat 4 simbol proposisional?

A. 4  
B. 8  
C. 12  
D. 16  
E. 32

---

### Soal 5
Manakah konnektif yang memiliki prioritas (precedence) tertinggi?

A. ∧ (AND)  
B. ∨ (OR)  
C. ¬ (NOT)  
D. ⇒ (IMPLIES)  
E. ⇔ (IFF)

---

### Soal 6
Diketahui P = True dan Q = False. Berapakah nilai kebenaran dari P ⇔ Q?

A. True  
B. False  
C. Tidak dapat ditentukan  
D. Tergantung konteks  
E. Undefined

---

### Soal 7
Aturan inferensi yang menyatakan "Jika P ⇒ Q dan ¬Q, maka ¬P" disebut:

A. Modus Ponens  
B. Modus Tollens  
C. Hypothetical Syllogism  
D. Resolution  
E. And-Elimination

---

### Soal 8
Proposisi yang bernilai True pada **semua** model disebut:

A. Satisfiable  
B. Valid (tautology)  
C. Entailed  
D. Contingent  
E. Consistent

---

### Soal 9
Manakah yang merupakan ekuivalensi logika yang BENAR?

A. P ⇒ Q ≡ P ∨ Q  
B. P ⇒ Q ≡ ¬P ∨ Q  
C. P ⇒ Q ≡ ¬Q ⇒ P  
D. P ⇒ Q ≡ Q ⇒ P  
E. P ⇒ Q ≡ P ∧ Q

---

### Soal 10
Bentuk Conjunctive Normal Form (CNF) adalah:

A. Disjungsi dari klausa-klausa konjungsi  
B. Konjungsi dari klausa-klausa disjungsi  
C. Sekumpulan implikasi  
D. Sekumpulan bikondisional  
E. Negasi dari semua literal

---

### Soal 11
Langkah pertama dalam prosedur konversi ke CNF adalah:

A. Pindahkan NOT ke dalam  
B. Distribusikan OR atas AND  
C. Eliminasi bikondisional (⇔)  
D. Eliminasi implikasi (⇒)  
E. Bentuk klausa

---

### Soal 12
Dalam resolution, jika kita me-resolve klausa {P, Q} dengan klausa {¬P, R}, hasilnya adalah:

A. {P, R}  
B. {¬P, Q}  
C. {Q, R}  
D. {P, ¬P}  
E. Klausa kosong (∅)

---

### Soal 13
Dalam proof by resolution, kita membuktikan KB ⊨ α dengan menunjukkan bahwa:

A. KB ∧ α adalah valid  
B. KB ∧ ¬α adalah unsatisfiable  
C. KB ∨ α adalah satisfiable  
D. KB ∧ α adalah satisfiable  
E. ¬KB ∧ α adalah valid

---

### Soal 14
Hukum De Morgan menyatakan bahwa ¬(P ∨ Q) ekuivalen dengan:

A. ¬P ∨ ¬Q  
B. ¬P ∧ ¬Q  
C. P ∧ Q  
D. ¬P ⇒ ¬Q  
E. P ∨ ¬Q

---

### Soal 15
Dalam Wumpus World, jika agen merasakan Breeze di sel (1,1), hal ini mengindikasikan:

A. Wumpus ada di sel tetangga  
B. Pit (lubang) ada di sel tetangga  
C. Emas ada di sel tetangga  
D. Dinding ada di sel tetangga  
E. Sel (1,1) aman untuk dilalui

---

### Soal 16
KB ⊨ α berarti:

A. α ada di dalam KB  
B. α dapat ditambahkan ke KB  
C. α bernilai True di setiap model di mana KB bernilai True  
D. KB dan α memiliki model yang sama  
E. α adalah kontradiksi

---

### Soal 17
Manakah yang BUKAN merupakan aturan inferensi yang valid?

A. Dari P ∧ Q, simpulkan P  
B. Dari P, simpulkan P ∨ Q  
C. Dari P ⇒ Q dan Q ⇒ R, simpulkan P ⇒ R  
D. Dari P ∨ Q dan P, simpulkan Q  
E. Dari P ⇒ Q dan P, simpulkan Q

---

### Soal 18
Hasil konversi (P ⇒ Q) ∧ (Q ⇒ R) ke CNF adalah:

A. (P ∧ Q) ∨ (Q ∧ R)  
B. (¬P ∨ Q) ∧ (¬Q ∨ R)  
C. (P ∨ ¬Q) ∧ (Q ∨ ¬R)  
D. ¬P ∨ Q ∨ ¬Q ∨ R  
E. (P ⇒ Q) ∨ (Q ⇒ R)

---

### Soal 19
Dalam konteks representasi pengetahuan, kelemahan utama logika proposisional dibanding logika predikat adalah:

A. Tidak dapat merepresentasikan pernyataan benar atau salah  
B. Tidak dapat menggunakan konnektif logika  
C. Tidak dapat merepresentasikan objek individual dan relasi antar objek  
D. Tidak dapat melakukan inferensi  
E. Tidak mendukung tabel kebenaran

---

### Soal 20
Jika klausa kosong (∅) dihasilkan selama proses resolution, ini berarti:

A. Premis tidak memiliki kesimpulan  
B. Knowledge Base kosong  
C. Kontradiksi ditemukan, sehingga α terbukti  
D. Proses resolution gagal  
E. Perlu menambahkan klausa baru

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan perbedaan antara pendekatan pencarian (search) yang dipelajari pada Pertemuan 1–6 dengan pendekatan representasi pengetahuan (knowledge representation) menggunakan logika! Berikan satu contoh situasi di mana masing-masing pendekatan lebih sesuai!

---

### Soal 2 ⭐
Jelaskan operasi TELL dan ASK pada Knowledge Base! Berikan contoh penggunaan keduanya dalam skenario sistem keamanan gedung!

---

### Soal 3 ⭐
Sebutkan dan jelaskan lima konnektif dalam logika proposisional beserta simbol dan tabel kebenarannya!

---

### Soal 4 ⭐
Jelaskan mengapa implikasi P ⇒ Q bernilai True ketika P bernilai False (baik Q True maupun Q False)! Gunakan analogi "janji" atau contoh dunia nyata untuk menjelaskan!

---

### Soal 5 ⭐⭐
Diketahui proposisi: (P ∨ Q) ⇒ (R ∧ S). Buatlah tabel kebenaran lengkap untuk semua kombinasi nilai P, Q, R, S! Tentukan apakah proposisi ini valid, satisfiable, atau unsatisfiable!

---

### Soal 6 ⭐⭐
Jelaskan perbedaan antara entailment (⊨) dan equivalence (≡)! Berikan contoh dua proposisi yang saling entail tetapi tidak ekuivalen, dan dua proposisi yang ekuivalen!

---

### Soal 7 ⭐⭐
Tunjukkan bahwa (P ⇒ Q) ≡ (¬Q ⇒ ¬P) menggunakan tabel kebenaran! Apa nama ekuivalensi ini dan mengapa penting dalam penalaran logis?

---

### Soal 8 ⭐⭐
Diberikan Knowledge Base berikut:
- KB₁: Jika radar aktif dan cuaca cerah, maka deteksi akurat (R ∧ C ⇒ D)
- KB₂: Radar aktif (R)
- KB₃: Cuaca cerah (C)
- KB₄: Jika deteksi akurat, maka aktifkan alert (D ⇒ A)

Gunakan aturan inferensi (Modus Ponens) secara berulang untuk membuktikan bahwa alert diaktifkan (A)! Tuliskan setiap langkah inferensi beserta aturan yang digunakan!

---

### Soal 9 ⭐⭐
Konversikan proposisi berikut ke CNF melalui 4 langkah konversi:

$$P ⇔ (Q ∨ R)$$

Tuliskan setiap langkah secara detail!

---

### Soal 10 ⭐⭐
Jelaskan kedua hukum De Morgan dan buktikan masing-masing menggunakan tabel kebenaran! Berikan contoh penerapan De Morgan dalam konteks logika keamanan siber!

---

### Soal 11 ⭐⭐
Jelaskan konsep satisfiability, validity, dan unsatisfiability! Untuk masing-masing kategori, berikan satu contoh proposisi dan buktikan menggunakan tabel kebenaran!

---

### Soal 12 ⭐⭐⭐
Gunakan algoritma resolution (proof by refutation) untuk membuktikan:

**KB:** {P ⇒ Q, Q ⇒ R, R ⇒ S, P}  
**Buktikan:** S

Tuliskan semua langkah: konversi CNF, penambahan negasi kesimpulan, dan setiap langkah resolusi hingga menghasilkan klausa kosong!

---

### Soal 13 ⭐⭐⭐
Dalam Wumpus World 4×4, agen berada di sel (1,1) dan telah mengunjungi (1,2) dan (2,1). Informasi yang diperoleh:
- (1,1): Tidak ada Breeze, tidak ada Stench
- (1,2): Breeze terdeteksi
- (2,1): Tidak ada Breeze, tidak ada Stench

Representasikan situasi ini dalam logika proposisional dan gunakan inferensi untuk menentukan sel mana yang pasti aman dan sel mana yang mungkin mengandung Pit!

---

### Soal 14 ⭐⭐⭐
Rancang Knowledge Base lengkap dalam logika proposisional untuk sistem deteksi intrusi jaringan militer. KB harus mencakup:
- Minimal 5 proposisi atomik yang relevan
- Minimal 4 aturan (implikasi)
- Tunjukkan chain of inference dari fakta awal hingga kesimpulan akhir menggunakan minimal 3 langkah inferensi berbeda (Modus Ponens, Modus Tollens, atau Hypothetical Syllogism)

---

### Soal 15 ⭐⭐⭐
Konversikan proposisi berikut ke CNF dan kemudian gunakan resolution untuk membuktikan kesimpulan:

**KB:**
1. (A ∧ B) ⇒ C
2. C ⇒ (D ∨ E)
3. ¬E
4. A
5. B

**Buktikan:** D

Tuliskan setiap langkah konversi dan resolusi secara lengkap!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Peringatan Dini Serangan Siber pada Infrastruktur Pertahanan

**Latar Belakang:**

Badan Siber dan Sandi Negara (BSSN) bekerja sama dengan unit siber TNI mengembangkan sistem peringatan dini berbasis knowledge-based agent untuk melindungi infrastruktur pertahanan kritis. Sistem ini memantau jaringan komunikasi militer, server komando, dan sistem senjata yang terkoneksi.

Sistem menggunakan sensor-sensor berikut:
- Intrusion Detection System (IDS) yang mendeteksi pola trafik anomali
- Firewall log analyzer yang mencatat koneksi mencurigakan
- Endpoint Detection and Response (EDR) pada setiap terminal
- Network traffic analyzer untuk analisis deep packet inspection
- Honeypot yang merekam aktivitas penyerang

Proposisi yang digunakan dalam sistem:

| Simbol | Proposisi |
|--------|-----------|
| T | Trafik anomali terdeteksi oleh IDS |
| F | Firewall mendeteksi koneksi dari IP blacklist |
| M | Malware signature terdeteksi oleh EDR |
| E | Eksfiltrasi data terdeteksi (upload besar ke luar) |
| S | Port scanning terdeteksi |
| H | Aktivitas honeypot terdeteksi |
| L | Login gagal berulang (brute force) |
| P | Privilege escalation terdeteksi |
| C | Serangan siber dikonfirmasi |
| A | Alert level tinggi diaktifkan |
| I | Isolasi jaringan dilakukan |
| R | Tim respons insiden dikerahkan |

Aturan (rules) dalam Knowledge Base:

1. (T ∧ F) ⇒ C — Trafik anomali DAN koneksi dari IP blacklist mengonfirmasi serangan
2. (M ∧ P) ⇒ C — Malware DAN privilege escalation mengonfirmasi serangan
3. (E ∧ S) ⇒ C — Eksfiltrasi data DAN port scanning mengonfirmasi serangan
4. H ⇒ S — Jika honeypot aktif, maka port scanning terdeteksi
5. (L ∧ P) ⇒ M — Brute force DAN privilege escalation mengindikasikan malware
6. C ⇒ A — Serangan dikonfirmasi mengaktifkan alert tinggi
7. (C ∧ E) ⇒ I — Serangan DAN eksfiltrasi data memicu isolasi jaringan
8. (A ∧ I) ⇒ R — Alert tinggi DAN isolasi memicu deployment tim respons

**Skenario:** Pada pukul 02:30 WIB, sistem mendeteksi fakta berikut:
- Login gagal berulang terdeteksi (L = True)
- Privilege escalation terdeteksi (P = True)
- Eksfiltrasi data terdeteksi (E = True)
- Aktivitas honeypot terdeteksi (H = True)

**Pertanyaan:**

**1a.** Tentukan semua fakta yang dapat disimpulkan (inferred) dari fakta awal menggunakan aturan inferensi! Tuliskan setiap langkah inferensi beserta aturan yang digunakan dan nomor aturan KB yang diterapkan! (20 poin)

**1b.** Apakah tim respons insiden akan dikerahkan? Buktikan menggunakan chain of inference lengkap dari fakta awal! (15 poin)

**1c.** Konversikan aturan KB 1, 2, 3, dan 6 ke CNF! (10 poin)

**1d.** Gunakan resolution (proof by refutation) untuk membuktikan secara formal bahwa KB ⊨ R (tim respons dikerahkan), berdasarkan fakta awal yang diberikan dan seluruh aturan KB! (20 poin)

**1e.** Identifikasi kelemahan representasi logika proposisional untuk sistem ini! Berikan contoh aturan atau situasi yang TIDAK DAPAT direpresentasikan secara efisien dalam logika proposisional dan jelaskan mengapa logika predikat (FOL) diperlukan! (10 poin)

---

### Studi Kasus 2: Sistem Otorisasi Peluncuran Rudal Pertahanan Udara

**Latar Belakang:**

TNI Angkatan Udara mengembangkan knowledge-based system untuk otorisasi peluncuran rudal Surface-to-Air Missile (SAM) dalam skenario pertahanan udara. Sistem ini harus memenuhi beberapa syarat ketat sebelum mengizinkan peluncuran, mengikuti Rules of Engagement (ROE) yang ketat.

Proposisi yang digunakan:

| Simbol | Proposisi |
|--------|-----------|
| D | Target terdeteksi oleh radar |
| K | Target dikonfirmasi sebagai hostile oleh IFF |
| V | Target berada dalam engagement envelope (jangkauan) |
| W | Cuaca memenuhi syarat peluncuran |
| O | Operator telah melakukan prosedur verifikasi |
| B | Komandan batalion memberikan otorisasi |
| Z | Zona terbang sipil clear (tidak ada pesawat sipil) |
| J | Sistem jamming tidak mengganggu radar |
| G | Sistem guidance rudal operational |
| L | Peluncuran diotorisasi |
| F | Fire command diberikan |
| N | Notifikasi ke komando atas dikirim |

Aturan ROE dalam Knowledge Base:

1. (D ∧ K) ⇒ V — Target terdeteksi DAN dikonfirmasi hostile masuk ke proses engagement
2. ¬K ⇒ ¬L — Target TIDAK dikonfirmasi hostile maka peluncuran TIDAK diotorisasi
3. (V ∧ W ∧ Z) ⇒ O — Dalam jangkauan DAN cuaca baik DAN zona clear memicu prosedur verifikasi
4. (O ∧ B) ⇒ L — Verifikasi DAN otorisasi komandan mengotorisasi peluncuran
5. (L ∧ G) ⇒ F — Peluncuran diotorisasi DAN guidance operational memicu fire command
6. (L ∧ J) ⇒ F — Peluncuran diotorisasi DAN tidak ada jamming memicu fire command
7. F ⇒ N — Fire command diberikan maka notifikasi dikirim
8. ¬Z ⇒ ¬L — Zona sipil TIDAK clear maka peluncuran TIDAK diotorisasi
9. (D ∧ ¬J) ⇒ K — Target terdeteksi DAN tidak ada jamming maka konfirmasi dimungkinkan

**Skenario A — Peluncuran berhasil:**
Fakta awal: D = True, K = True, W = True, Z = True, B = True, G = True, J = True

**Skenario B — Peluncuran ditolak:**
Fakta awal: D = True, K = True, W = True, Z = False, B = True, G = True

**Pertanyaan:**

**2a.** Untuk Skenario A, lakukan inference chain lengkap dari fakta awal dan tentukan apakah fire command diberikan (F) dan notifikasi terkirim (N)! Tuliskan setiap langkah beserta aturan yang digunakan! (20 poin)

**2b.** Untuk Skenario B, tentukan mengapa peluncuran ditolak! Tunjukkan inferensi yang mengarah ke ¬L dan jelaskan mengapa chain of inference berhenti! (15 poin)

**2c.** Konversikan aturan 2, 4, 5, dan 8 ke CNF! (10 poin)

**2d.** Gunakan resolution untuk membuktikan bahwa dalam Skenario A, KB ⊨ N (notifikasi terkirim)! Tuliskan seluruh langkah resolusi! (20 poin)

**2e.** Aturan ROE mensyaratkan bahwa peluncuran TIDAK BOLEH terjadi jika salah satu syarat berikut terpenuhi: (i) target belum dikonfirmasi hostile, (ii) zona sipil tidak clear, atau (iii) komandan tidak mengotorisasi. Representasikan syarat pembatalan ini sebagai satu proposisi logika dan buktikan bahwa KB sudah mencakup semua syarat ini! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **C** | "Radar mendeteksi objek di koordinat Alpha" adalah pernyataan deklaratif yang bernilai True atau False. Pilihan lain berupa pertanyaan (A), perintah (B), variabel bebas (D), atau harapan (E) |
| 2 | **C** | TELL adalah operasi untuk menambahkan fakta atau aturan baru ke Knowledge Base |
| 3 | **D** | Implikasi P ⇒ Q hanya bernilai False ketika premis (P) True tetapi konsekuen (Q) False — "janji dilanggar" |
| 4 | **D** | Jumlah model = 2ⁿ dimana n = jumlah simbol. Dengan 4 simbol: 2⁴ = 16 model |
| 5 | **C** | Urutan precedence: ¬ (tertinggi), ∧, ∨, ⇒, ⇔ (terendah) |
| 6 | **B** | P ⇔ Q bernilai True jika P dan Q memiliki nilai sama. P = True, Q = False → nilai berbeda → False |
| 7 | **B** | Modus Tollens: dari P ⇒ Q dan ¬Q, simpulkan ¬P |
| 8 | **B** | Proposisi yang bernilai True pada semua model disebut valid atau tautology |
| 9 | **B** | Implication Elimination: P ⇒ Q ≡ ¬P ∨ Q |
| 10 | **B** | CNF adalah konjungsi (AND) dari klausa-klausa, di mana setiap klausa adalah disjungsi (OR) dari literal |
| 11 | **C** | Langkah konversi CNF: (1) Eliminasi ⇔, (2) Eliminasi ⇒, (3) Pindahkan ¬ ke dalam, (4) Distribusi ∨ atas ∧ |
| 12 | **C** | Resolution: {P, Q} dan {¬P, R} menghasilkan {Q, R} — literal komplementer P dan ¬P saling menghilangkan |
| 13 | **B** | Proof by refutation: tambahkan ¬α ke KB, jika KB ∧ ¬α unsatisfiable (menghasilkan ∅), maka KB ⊨ α |
| 14 | **B** | De Morgan: ¬(P ∨ Q) ≡ ¬P ∧ ¬Q |
| 15 | **B** | Dalam Wumpus World, Breeze mengindikasikan Pit di sel tetangga (atas/bawah/kiri/kanan) |
| 16 | **C** | KB ⊨ α berarti α bernilai True di setiap model di mana seluruh KB bernilai True |
| 17 | **D** | "Dari P ∨ Q dan P, simpulkan Q" BUKAN valid. P ∨ Q dan P keduanya true tidak menjamin Q true. Yang benar adalah: dari P ∨ Q dan ¬P, simpulkan Q (Disjunctive Syllogism) |
| 18 | **B** | P ⇒ Q menjadi ¬P ∨ Q, dan Q ⇒ R menjadi ¬Q ∨ R. Konjungsi: (¬P ∨ Q) ∧ (¬Q ∨ R) |
| 19 | **C** | Logika proposisional tidak dapat merepresentasikan objek individual, relasi, atau kuantifikasi (∀, ∃). Keterbatasan ini diatasi oleh logika predikat (FOL) |
| 20 | **C** | Klausa kosong menandakan kontradiksi ditemukan pada KB ∧ ¬α, sehingga α terbukti benar (proof by refutation berhasil) |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Pendekatan Pencarian (Search):**
- Memecahkan masalah dengan mengeksplorasi state space dari state awal ke goal
- Agen tidak "mengetahui" mengapa suatu tindakan benar — hanya mencari jalur
- Cocok untuk masalah navigasi, puzzle, pathfinding
- **Contoh:** Robot mencari jalur terpendek dari markas ke pos perbatasan

**Pendekatan Representasi Pengetahuan:**
- Menyimpan fakta dan aturan dalam Knowledge Base
- Agen dapat menalar "mengapa" suatu kesimpulan benar melalui inferensi logis
- Cocok untuk diagnosis, pengambilan keputusan berbasis aturan, verifikasi
- **Contoh:** Sistem deteksi ancaman yang menyimpulkan "ada serangan" dari kombinasi indikator (trafik anomali, IP mencurigakan, pola serangan)

**Perbedaan kunci:** Search fokus pada "bagaimana mencapai tujuan", sedangkan knowledge representation fokus pada "apa yang kita ketahui dan apa yang dapat disimpulkan".

---

#### Jawaban Soal 2 ⭐

**TELL** — Menambahkan fakta atau aturan baru ke Knowledge Base.

**ASK** — Mengajukan query untuk mendapatkan jawaban dari Knowledge Base melalui inferensi.

**Contoh Sistem Keamanan Gedung:**

```
TELL(KB, "Jika kartu akses valid DAN jam kerja, maka akses diizinkan")
    → Menambahkan aturan: (KartuValid ∧ JamKerja) ⇒ AksesIzin

TELL(KB, "Kartu akses valid")
    → Menambahkan fakta: KartuValid = True

TELL(KB, "Sekarang jam kerja")
    → Menambahkan fakta: JamKerja = True

ASK(KB, "Akses diizinkan?")
    → Inference engine menerapkan Modus Ponens
    → Jawaban: True (akses diizinkan)
```

---

#### Jawaban Soal 3 ⭐

**Lima Konnektif Logika Proposisional:**

| No | Konnektif | Simbol | Arti | Tabel Kebenaran Ringkas |
|----|-----------|--------|------|------------------------|
| 1 | **Negasi** | ¬ | "bukan" / NOT | ¬T = F, ¬F = T |
| 2 | **Konjungsi** | ∧ | "dan" / AND | True hanya jika keduanya True |
| 3 | **Disjungsi** | ∨ | "atau" / OR | False hanya jika keduanya False |
| 4 | **Implikasi** | ⇒ | "jika...maka" / IMPLIES | False hanya jika premis True, konsekuen False |
| 5 | **Bikondisional** | ⇔ | "jika dan hanya jika" / IFF | True jika keduanya bernilai sama |

**Tabel kebenaran lengkap:**

| P | Q | ¬P | P ∧ Q | P ∨ Q | P ⇒ Q | P ⇔ Q |
|---|---|----|-------|-------|-------|-------|
| T | T | F | T | T | T | T |
| T | F | F | F | T | F | F |
| F | T | T | F | T | T | F |
| F | F | T | F | F | T | T |

---

#### Jawaban Soal 4 ⭐

**Mengapa P ⇒ Q bernilai True ketika P False:**

Implikasi P ⇒ Q dapat dipahami sebagai "janji":
- P ⇒ Q: "Jika P terjadi, maka Q akan terjadi"

**Analogi Janji:**
Seorang komandan berjanji: "Jika musuh menyerang (P), maka saya akan membalas (Q)"

1. **P = True, Q = True:** Musuh menyerang, komandan membalas → Janji **ditepati** (True)
2. **P = True, Q = False:** Musuh menyerang, komandan TIDAK membalas → Janji **dilanggar** (False)
3. **P = False, Q = True:** Musuh TIDAK menyerang, komandan tetap menyerang → Janji **tidak dilanggar** karena kondisi janji tidak terpenuhi (True)
4. **P = False, Q = False:** Musuh TIDAK menyerang, komandan TIDAK menyerang → Janji **tidak dilanggar** (True)

**Kunci:** Janji hanya bisa dilanggar ketika prasyarat terpenuhi (P = True) tetapi konsekuensi tidak dilakukan (Q = False). Jika prasyarat tidak terpenuhi (P = False), janji secara vakum benar (vacuously true) karena tidak ada kewajiban yang perlu dipenuhi.

---

#### Jawaban Soal 5 ⭐⭐

**Tabel kebenaran (P ∨ Q) ⇒ (R ∧ S):**

| P | Q | R | S | P ∨ Q | R ∧ S | (P∨Q) ⇒ (R∧S) |
|---|---|---|---|-------|-------|----------------|
| T | T | T | T | T | T | **T** |
| T | T | T | F | T | F | **F** |
| T | T | F | T | T | F | **F** |
| T | T | F | F | T | F | **F** |
| T | F | T | T | T | T | **T** |
| T | F | T | F | T | F | **F** |
| T | F | F | T | T | F | **F** |
| T | F | F | F | T | F | **F** |
| F | T | T | T | T | T | **T** |
| F | T | T | F | T | F | **F** |
| F | T | F | T | T | F | **F** |
| F | T | F | F | T | F | **F** |
| F | F | T | T | F | T | **T** |
| F | F | T | F | F | F | **T** |
| F | F | F | T | F | F | **T** |
| F | F | F | F | F | F | **T** |

**Analisis:** Proposisi bernilai True pada beberapa model dan False pada beberapa model lainnya, sehingga proposisi ini **satisfiable** (bukan valid, bukan unsatisfiable).

---

#### Jawaban Soal 6 ⭐⭐

**Entailment (⊨):**
- KB ⊨ α berarti α bernilai True di setiap model di mana KB bernilai True
- Bersifat satu arah: "KB mengikutkan α"
- Contoh: {P, P ⇒ Q} ⊨ Q — setiap model yang memenuhi KB juga memenuhi Q

**Equivalence (≡):**
- α ≡ β berarti α dan β bernilai sama pada **semua** model
- Bersifat dua arah: α ⊨ β DAN β ⊨ α
- Contoh: P ⇒ Q ≡ ¬P ∨ Q — nilainya selalu sama

**Contoh entailment tanpa equivalence:**
- P ∧ Q ⊨ P (dari P ∧ Q kita dapat menyimpulkan P)
- Tapi P ⊭ P ∧ Q (dari P saja kita tidak bisa menyimpulkan P ∧ Q)
- Jadi P ∧ Q dan P TIDAK ekuivalen

**Contoh equivalence:**
- P ⇒ Q ≡ ¬P ∨ Q (Implication Elimination)
- ¬(P ∧ Q) ≡ ¬P ∨ ¬Q (De Morgan)

---

#### Jawaban Soal 7 ⭐⭐

**Tabel kebenaran untuk (P ⇒ Q) dan (¬Q ⇒ ¬P):**

| P | Q | P ⇒ Q | ¬Q | ¬P | ¬Q ⇒ ¬P |
|---|---|-------|-----|-----|----------|
| T | T | T | F | F | T |
| T | F | F | T | F | F |
| F | T | T | F | T | T |
| F | F | T | T | T | T |

Kolom P ⇒ Q dan ¬Q ⇒ ¬P **identik** pada semua baris, sehingga terbukti:

$$(P ⇒ Q) ≡ (¬Q ⇒ ¬P)$$

**Nama ekuivalensi:** **Contrapositive** (kontraposisi)

**Pentingnya dalam penalaran:**
Contrapositive sangat berguna karena memungkinkan kita menalar "mundur". Alih-alih membuktikan secara langsung bahwa P menyebabkan Q, kita bisa membuktikan bahwa ketiadaan Q menyebabkan ketiadaan P. Ini merupakan dasar dari aturan inferensi Modus Tollens: dari P ⇒ Q dan ¬Q, simpulkan ¬P.

**Contoh:** "Jika sistem terenkripsi, maka data aman" ekuivalen dengan "Jika data tidak aman, maka sistem tidak terenkripsi."

---

#### Jawaban Soal 8 ⭐⭐

**Diberikan:** R ∧ C ⇒ D (KB₁), R (KB₂), C (KB₃), D ⇒ A (KB₄)

**Langkah inferensi:**

**Langkah 1:** And-Introduction pada KB₂ dan KB₃
- Dari R (KB₂) dan C (KB₃)
- Simpulkan: R ∧ C
- Aturan: And-Introduction

**Langkah 2:** Modus Ponens pada KB₁ dan hasil Langkah 1
- Dari R ∧ C ⇒ D (KB₁) dan R ∧ C (Langkah 1)
- Simpulkan: **D** (deteksi akurat)
- Aturan: Modus Ponens

**Langkah 3:** Modus Ponens pada KB₄ dan hasil Langkah 2
- Dari D ⇒ A (KB₄) dan D (Langkah 2)
- Simpulkan: **A** (alert diaktifkan) ✓
- Aturan: Modus Ponens

**Kesimpulan:** Alert diaktifkan (A = True), dibuktikan melalui 3 langkah inferensi berturut-turut.

---

#### Jawaban Soal 9 ⭐⭐

**Konversi P ⇔ (Q ∨ R) ke CNF:**

**Langkah 1: Eliminasi ⇔**

$$P ⇔ (Q ∨ R) \equiv (P ⇒ (Q ∨ R)) ∧ ((Q ∨ R) ⇒ P)$$

**Langkah 2: Eliminasi ⇒**

$$(¬P ∨ (Q ∨ R)) ∧ (¬(Q ∨ R) ∨ P)$$

**Langkah 3: Pindahkan ¬ ke dalam (De Morgan)**

$$(¬P ∨ Q ∨ R) ∧ ((¬Q ∧ ¬R) ∨ P)$$

**Langkah 4: Distribusi ∨ atas ∧**

Bagian kedua: (¬Q ∧ ¬R) ∨ P

Distribusikan P atas ∧:

$$(P ∨ ¬Q) ∧ (P ∨ ¬R)$$

**Hasil CNF akhir:**

$$(¬P ∨ Q ∨ R) ∧ (P ∨ ¬Q) ∧ (P ∨ ¬R)$$

Tiga klausa: {¬P, Q, R}, {P, ¬Q}, {P, ¬R}

---

#### Jawaban Soal 10 ⭐⭐

**Hukum De Morgan:**

**De Morgan 1:** ¬(P ∧ Q) ≡ ¬P ∨ ¬Q

| P | Q | P ∧ Q | ¬(P ∧ Q) | ¬P | ¬Q | ¬P ∨ ¬Q |
|---|---|-------|----------|-----|-----|---------|
| T | T | T | F | F | F | F |
| T | F | F | T | F | T | T |
| F | T | F | T | T | F | T |
| F | F | F | T | T | T | T |

Kolom ¬(P ∧ Q) dan ¬P ∨ ¬Q identik ✓

**De Morgan 2:** ¬(P ∨ Q) ≡ ¬P ∧ ¬Q

| P | Q | P ∨ Q | ¬(P ∨ Q) | ¬P | ¬Q | ¬P ∧ ¬Q |
|---|---|-------|----------|-----|-----|---------|
| T | T | T | F | F | F | F |
| T | F | T | F | F | T | F |
| F | T | T | F | T | F | F |
| F | F | F | T | T | T | T |

Kolom ¬(P ∨ Q) dan ¬P ∧ ¬Q identik ✓

**Contoh penerapan dalam keamanan siber:**

Proposisi: "BUKAN (firewall aktif DAN antivirus aktif)" — ¬(F ∧ A)

Menurut De Morgan 1: ¬(F ∧ A) ≡ ¬F ∨ ¬A

Artinya: "Firewall TIDAK aktif ATAU antivirus TIDAK aktif"

Implikasi: Cukup satu komponen keamanan yang tidak aktif untuk membuat pernyataan awal bernilai True — ini menunjukkan celah keamanan jika salah satu saja gagal.

---

#### Jawaban Soal 11 ⭐⭐

**1. Valid (Tautology):** Bernilai True pada **semua** model.

Contoh: P ∨ ¬P

| P | ¬P | P ∨ ¬P |
|---|----|--------|
| T | F | **T** |
| F | T | **T** |

Selalu True → **Valid** ✓

**2. Satisfiable:** Bernilai True pada **minimal satu** model.

Contoh: P ∧ Q

| P | Q | P ∧ Q |
|---|---|-------|
| T | T | **T** ← True pada model ini |
| T | F | F |
| F | T | F |
| F | F | F |

Ada model yang True → **Satisfiable** ✓ (tapi bukan valid karena ada model yang False)

**3. Unsatisfiable (Contradiction):** Bernilai False pada **semua** model.

Contoh: P ∧ ¬P

| P | ¬P | P ∧ ¬P |
|---|----|--------|
| T | F | **F** |
| F | T | **F** |

Selalu False → **Unsatisfiable** ✓

**Hubungan:** Setiap proposisi valid juga satisfiable. Proposisi yang unsatisfiable tidak satisfiable. Proposisi satisfiable belum tentu valid.

---

#### Jawaban Soal 12 ⭐⭐⭐

**KB:** {P ⇒ Q, Q ⇒ R, R ⇒ S, P}. **Buktikan:** S

**Langkah 1: Konversi KB ke CNF**

| Aturan | Asli | CNF |
|--------|------|-----|
| KB₁ | P ⇒ Q | ¬P ∨ Q |
| KB₂ | Q ⇒ R | ¬Q ∨ R |
| KB₃ | R ⇒ S | ¬R ∨ S |
| KB₄ | P | P |

**Langkah 2: Tambahkan negasi kesimpulan**

Tambahkan ¬S ke kumpulan klausa.

**Klausa-klausa:**
- C1: {¬P, Q}
- C2: {¬Q, R}
- C3: {¬R, S}
- C4: {P}
- C5: {¬S} ← negasi kesimpulan

**Langkah 3: Resolusi**

| Langkah | Resolve | Literal Komplementer | Hasil |
|---------|---------|---------------------|-------|
| R1 | C4 + C1 | P, ¬P | C6: {Q} |
| R2 | C6 + C2 | Q, ¬Q | C7: {R} |
| R3 | C7 + C3 | R, ¬R | C8: {S} |
| R4 | C8 + C5 | S, ¬S | **∅** (klausa kosong) |

**Langkah 4: Kesimpulan**

Klausa kosong (∅) dihasilkan → KB ∧ ¬S unsatisfiable → **KB ⊨ S terbukti** ✓

---

#### Jawaban Soal 13 ⭐⭐⭐

**Proposisi yang digunakan:**
- B_{i,j}: Breeze di sel (i,j)
- P_{i,j}: Pit di sel (i,j)

**Fakta yang diketahui:**
- ¬B₁,₁: Tidak ada Breeze di (1,1)
- B₁,₂: Ada Breeze di (1,2)
- ¬B₂,₁: Tidak ada Breeze di (2,1)

**Aturan Wumpus World (tetangga = atas/bawah/kiri/kanan):**

- B₁,₁ ⇔ (P₁,₂ ∨ P₂,₁)
- B₁,₂ ⇔ (P₁,₁ ∨ P₁,₃ ∨ P₂,₂)
- B₂,₁ ⇔ (P₁,₁ ∨ P₂,₂ ∨ P₃,₁)

**Inferensi:**

**Dari ¬B₁,₁:**
- ¬B₁,₁ ⇒ ¬(P₁,₂ ∨ P₂,₁) [Modus Tollens pada kontrapositif]
- ¬P₁,₂ ∧ ¬P₂,₁ [De Morgan]
- **Kesimpulan: (1,2) aman, (2,1) aman** ✓

**Dari ¬B₂,₁:**
- ¬B₂,₁ ⇒ ¬(P₁,₁ ∨ P₂,₂ ∨ P₃,₁)
- ¬P₁,₁ ∧ ¬P₂,₂ ∧ ¬P₃,₁
- **Kesimpulan: (1,1) aman, (2,2) aman, (3,1) aman** ✓

**Dari B₁,₂:**
- B₁,₂ ⇒ P₁,₁ ∨ P₁,₃ ∨ P₂,₂
- Kita tahu ¬P₁,₁ (dari inferensi ¬B₂,₁) dan ¬P₂,₂ (dari inferensi ¬B₂,₁)
- Maka: P₁,₃ [Disjunctive Syllogism berulang]
- **Kesimpulan: (1,3) mengandung Pit!** ⚠️

**Ringkasan:**

| Sel | Status | Justifikasi |
|-----|--------|-------------|
| (1,1) | Aman ✓ | ¬P₁,₁ dari ¬B₂,₁ |
| (1,2) | Aman ✓ | ¬P₁,₂ dari ¬B₁,₁ |
| (2,1) | Aman ✓ | ¬P₂,₁ dari ¬B₁,₁ |
| (2,2) | Aman ✓ | ¬P₂,₂ dari ¬B₂,₁ |
| (3,1) | Aman ✓ | ¬P₃,₁ dari ¬B₂,₁ |
| **(1,3)** | **Pit** ⚠️ | P₁,₃ dari B₁,₂ + eliminasi |

---

#### Jawaban Soal 14 ⭐⭐⭐

**Knowledge Base Sistem Deteksi Intrusi Jaringan Militer:**

**Proposisi atomik:**
- T: Trafik anomali terdeteksi
- P: Port scanning terdeteksi
- F: Koneksi dari IP asing (foreign)
- M: Malware signature ditemukan
- I: Intrusi terjadi
- A: Alert keamanan diaktifkan
- B: Blokir IP dilakukan
- R: Respons keamanan diluncurkan

**Aturan (implikasi):**
1. (T ∧ P) ⇒ I — Trafik anomali DAN port scanning → intrusi
2. (F ∧ M) ⇒ I — IP asing DAN malware → intrusi
3. I ⇒ A — Intrusi → alert aktif
4. (A ∧ M) ⇒ B — Alert DAN malware → blokir IP
5. (A ∧ B) ⇒ R — Alert DAN blokir → respons keamanan

**Fakta awal:**
- T = True (trafik anomali terdeteksi)
- P = True (port scanning terdeteksi)
- M = True (malware ditemukan)

**Chain of inference:**

**Langkah 1 — And-Introduction:**
Dari T dan P → T ∧ P

**Langkah 2 — Modus Ponens (Aturan 1):**
Dari (T ∧ P) ⇒ I dan T ∧ P → **I** (intrusi terjadi)

**Langkah 3 — Modus Ponens (Aturan 3):**
Dari I ⇒ A dan I → **A** (alert aktif)

**Langkah 4 — Modus Ponens (Aturan 4):**
Dari (A ∧ M) ⇒ B, A (Langkah 3), M (fakta) → A ∧ M → **B** (blokir IP)

**Langkah 5 — Modus Ponens (Aturan 5):**
Dari (A ∧ B) ⇒ R, A (Langkah 3), B (Langkah 4) → A ∧ B → **R** (respons keamanan diluncurkan) ✓

**Demonstrasi Modus Tollens (tambahan):**
Jika diketahui ¬A (alert TIDAK aktif), maka dari I ⇒ A dan ¬A:
→ ¬I (intrusi TIDAK terjadi) — **Modus Tollens**

**Demonstrasi Hypothetical Syllogism (tambahan):**
Dari (T ∧ P) ⇒ I (Aturan 1) dan I ⇒ A (Aturan 3):
→ (T ∧ P) ⇒ A — **Hypothetical Syllogism**

---

#### Jawaban Soal 15 ⭐⭐⭐

**KB:** (A ∧ B) ⇒ C, C ⇒ (D ∨ E), ¬E, A, B. **Buktikan:** D

**Langkah 1: Konversi KB ke CNF**

| No | Asli | CNF |
|----|------|-----|
| KB₁ | (A ∧ B) ⇒ C | ¬(A ∧ B) ∨ C = ¬A ∨ ¬B ∨ C |
| KB₂ | C ⇒ (D ∨ E) | ¬C ∨ D ∨ E |
| KB₃ | ¬E | ¬E |
| KB₄ | A | A |
| KB₅ | B | B |

**Langkah 2: Tambahkan negasi kesimpulan**

Tambahkan ¬D.

**Klausa-klausa:**
- C1: {¬A, ¬B, C}
- C2: {¬C, D, E}
- C3: {¬E}
- C4: {A}
- C5: {B}
- C6: {¬D} ← negasi kesimpulan

**Langkah 3: Resolusi**

| Langkah | Resolve | Literal Komplementer | Hasil |
|---------|---------|---------------------|-------|
| R1 | C1 + C4 | ¬A, A | C7: {¬B, C} |
| R2 | C7 + C5 | ¬B, B | C8: {C} |
| R3 | C2 + C3 | E, ¬E | C9: {¬C, D} |
| R4 | C9 + C6 | D, ¬D | C10: {¬C} |
| R5 | C8 + C10 | C, ¬C | **∅** (klausa kosong) |

**Langkah 4: Kesimpulan**

Klausa kosong dihasilkan → KB ∧ ¬D unsatisfiable → **KB ⊨ D terbukti** ✓

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Peringatan Dini Serangan Siber

**1a. Inferensi dari fakta awal (20 poin)**

Fakta awal: L = True, P = True, E = True, H = True

| Langkah | Inferensi | Aturan | Keterangan |
|---------|-----------|--------|------------|
| 1 | H → S | Modus Ponens (Aturan 4) | Honeypot aktif → port scanning |
| 2 | L ∧ P → M | Modus Ponens (Aturan 5) | Brute force + priv. escalation → malware |
| 3 | E ∧ S → C | Modus Ponens (Aturan 3) | Eksfiltrasi + port scanning → serangan dikonfirmasi |
| 4 | M ∧ P → C | Modus Ponens (Aturan 2) | Malware + priv. escalation → serangan dikonfirmasi (konfirmasi kedua) |
| 5 | C → A | Modus Ponens (Aturan 6) | Serangan dikonfirmasi → alert tinggi |
| 6 | C ∧ E → I | Modus Ponens (Aturan 7) | Serangan + eksfiltrasi → isolasi jaringan |
| 7 | A ∧ I → R | Modus Ponens (Aturan 8) | Alert + isolasi → tim respons dikerahkan |

**Fakta yang disimpulkan:** S, M, C, A, I, R

**1b. Pembuktian R (15 poin)**

**Chain of inference lengkap:**

```
Fakta:  H = T, L = T, P = T, E = T
  │
  ├─ Aturan 4: H → S                    ∴ S = True
  │
  ├─ Aturan 5: L ∧ P → M                ∴ M = True
  │
  ├─ Aturan 3: E ∧ S → C                ∴ C = True
  │
  ├─ Aturan 6: C → A                    ∴ A = True
  │
  ├─ Aturan 7: C ∧ E → I               ∴ I = True
  │
  └─ Aturan 8: A ∧ I → R               ∴ R = True  ✓
```

**Ya, tim respons insiden akan dikerahkan (R = True).**

**1c. Konversi ke CNF (10 poin)**

| No | Aturan Asli | CNF |
|----|-------------|-----|
| 1 | (T ∧ F) ⇒ C | ¬T ∨ ¬F ∨ C |
| 2 | (M ∧ P) ⇒ C | ¬M ∨ ¬P ∨ C |
| 3 | (E ∧ S) ⇒ C | ¬E ∨ ¬S ∨ C |
| 6 | C ⇒ A | ¬C ∨ A |

**1d. Resolution proof KB ⊨ R (20 poin)**

**Klausa CNF (dari seluruh KB + fakta awal):**
- C1: {¬T, ¬F, C} — Aturan 1
- C2: {¬M, ¬P, C} — Aturan 2
- C3: {¬E, ¬S, C} — Aturan 3
- C4: {¬H, S} — Aturan 4 (H ⇒ S)
- C5: {¬L, ¬P, M} — Aturan 5 ((L∧P)⇒M)
- C6: {¬C, A} — Aturan 6
- C7: {¬C, ¬E, I} — Aturan 7 ((C∧E)⇒I)
- C8: {¬A, ¬I, R} — Aturan 8 ((A∧I)⇒R)
- C9: {L} — Fakta
- C10: {P} — Fakta
- C11: {E} — Fakta
- C12: {H} — Fakta
- C13: {¬R} — Negasi kesimpulan

**Resolusi:**

| Langkah | Resolve | Komplementer | Hasil |
|---------|---------|--------------|-------|
| R1 | C4 + C12 | ¬H, H | C14: {S} |
| R2 | C5 + C9 | ¬L, L | C15: {¬P, M} |
| R3 | C15 + C10 | ¬P, P | C16: {M} |
| R4 | C3 + C11 | ¬E, E | C17: {¬S, C} |
| R5 | C17 + C14 | ¬S, S | C18: {C} |
| R6 | C6 + C18 | ¬C, C | C19: {A} |
| R7 | C7 + C18 | ¬C, C | C20: {¬E, I} |
| R8 | C20 + C11 | ¬E, E | C21: {I} |
| R9 | C8 + C19 | ¬A, A | C22: {¬I, R} |
| R10 | C22 + C21 | ¬I, I | C23: {R} |
| R11 | C23 + C13 | R, ¬R | **∅** |

**Klausa kosong ditemukan → KB ⊨ R terbukti** ✓

**1e. Kelemahan logika proposisional (10 poin)**

**Kelemahan utama:**

1. **Tidak dapat merepresentasikan kuantifikasi:** Aturan "Untuk SETIAP terminal yang terinfeksi malware, lakukan isolasi" tidak bisa direpresentasikan secara ringkas. Dalam logika proposisional, kita perlu membuat aturan terpisah untuk setiap terminal:
   - M_terminal1 ⇒ I_terminal1
   - M_terminal2 ⇒ I_terminal2
   - ... (ratusan aturan untuk ratusan terminal)

   Dalam FOL cukup satu aturan: ∀x (Malware(x) ⇒ Isolasi(x))

2. **Tidak dapat merepresentasikan relasi antar objek:** "Server X terhubung ke server Y" tidak bisa diungkapkan sebagai relasi. Dalam FOL: Connected(server_X, server_Y)

3. **Ledakan jumlah proposisi:** Jika ada 100 terminal dan 10 jenis serangan, logika proposisional memerlukan 100 × 10 = 1000 simbol proposisional unik, sedangkan FOL hanya memerlukan predikat AttackType(terminal, type).

4. **Tidak dapat merepresentasikan properti temporal:** "Jika serangan terjadi SEBELUM backup selesai, maka data hilang" memerlukan representasi waktu yang tidak tersedia di logika proposisional dasar.

---

#### Studi Kasus 2: Sistem Otorisasi Peluncuran Rudal

**2a. Inference chain Skenario A (20 poin)**

Fakta awal: D = T, K = T, W = T, Z = T, B = T, G = T, J = T

| Langkah | Inferensi | Aturan | Keterangan |
|---------|-----------|--------|------------|
| 1 | D ∧ K → V | Modus Ponens (Aturan 1) | Target terdeteksi + hostile → engagement |
| 2 | V ∧ W ∧ Z → O | Modus Ponens (Aturan 3) | Dalam jangkauan + cuaca baik + zona clear → verifikasi |
| 3 | O ∧ B → L | Modus Ponens (Aturan 4) | Verifikasi + otorisasi → peluncuran diotorisasi |
| 4 | L ∧ G → F | Modus Ponens (Aturan 5) | Peluncuran + guidance OK → fire command |
| 5 | F → N | Modus Ponens (Aturan 7) | Fire command → notifikasi terkirim |

**Hasil:**
- V = True (target dalam engagement envelope)
- O = True (prosedur verifikasi dilakukan)
- L = True (peluncuran diotorisasi)
- **F = True** (fire command diberikan) ✓
- **N = True** (notifikasi terkirim) ✓

Catatan: Aturan 6 (L ∧ J → F) juga terpenuhi karena J = True, memberikan konfirmasi tambahan untuk F.

**2b. Analisis Skenario B — Peluncuran ditolak (15 poin)**

Fakta awal: D = T, K = T, W = T, **Z = False**, B = T, G = T

**Inferensi yang berjalan:**

**Langkah 1:** D ∧ K → V (Aturan 1) → V = True

**Langkah yang TERHENTI:**

**Aturan 3:** V ∧ W ∧ Z → O
- V = True, W = True, tapi **Z = False**
- V ∧ W ∧ Z = True ∧ True ∧ False = **False**
- Modus Ponens TIDAK dapat diterapkan karena premis tidak terpenuhi
- **O tidak dapat disimpulkan**

**Aturan 8 (pembatalan eksplisit):** ¬Z → ¬L
- Z = False → ¬Z = True
- Modus Ponens: ¬L (**peluncuran TIDAK diotorisasi**) ✓

**Mengapa chain of inference berhenti:**
1. Tanpa O, Aturan 4 (O ∧ B → L) tidak bisa diterapkan
2. Aturan 8 secara eksplisit menyatakan ¬L ketika Z false
3. Tanpa L, Aturan 5 dan 6 tidak bisa menghasilkan F
4. Tanpa F, Aturan 7 tidak bisa menghasilkan N

**Kesimpulan:** Peluncuran **ditolak** karena zona terbang sipil tidak clear (Z = False), sesuai ROE yang mengutamakan keselamatan penerbangan sipil.

**2c. Konversi ke CNF (10 poin)**

| No | Aturan Asli | Langkah Konversi | CNF |
|----|-------------|------------------|-----|
| 2 | ¬K ⇒ ¬L | K ∨ ¬L (eliminasi ⇒) | {K, ¬L} |
| 4 | (O ∧ B) ⇒ L | ¬(O ∧ B) ∨ L = ¬O ∨ ¬B ∨ L | {¬O, ¬B, L} |
| 5 | (L ∧ G) ⇒ F | ¬(L ∧ G) ∨ F = ¬L ∨ ¬G ∨ F | {¬L, ¬G, F} |
| 8 | ¬Z ⇒ ¬L | Z ∨ ¬L (eliminasi ⇒) | {Z, ¬L} |

**2d. Resolution proof Skenario A: KB ⊨ N (20 poin)**

**Klausa CNF (aturan + fakta Skenario A):**
- C1: {¬D, ¬K, V} — Aturan 1
- C2: {K, ¬L} — Aturan 2
- C3: {¬V, ¬W, ¬Z, O} — Aturan 3
- C4: {¬O, ¬B, L} — Aturan 4
- C5: {¬L, ¬G, F} — Aturan 5
- C6: {¬L, ¬J, F} — Aturan 6
- C7: {¬F, N} — Aturan 7
- C8: {Z, ¬L} — Aturan 8
- C9: {D} — Fakta
- C10: {K} — Fakta
- C11: {W} — Fakta
- C12: {Z} — Fakta
- C13: {B} — Fakta
- C14: {G} — Fakta
- C15: {J} — Fakta
- C16: {¬N} — Negasi kesimpulan

**Resolusi:**

| Langkah | Resolve | Komplementer | Hasil |
|---------|---------|--------------|-------|
| R1 | C1 + C9 | ¬D, D | C17: {¬K, V} |
| R2 | C17 + C10 | ¬K, K | C18: {V} |
| R3 | C3 + C18 | ¬V, V | C19: {¬W, ¬Z, O} |
| R4 | C19 + C11 | ¬W, W | C20: {¬Z, O} |
| R5 | C20 + C12 | ¬Z, Z | C21: {O} |
| R6 | C4 + C21 | ¬O, O | C22: {¬B, L} |
| R7 | C22 + C13 | ¬B, B | C23: {L} |
| R8 | C5 + C23 | ¬L, L | C24: {¬G, F} |
| R9 | C24 + C14 | ¬G, G | C25: {F} |
| R10 | C7 + C25 | ¬F, F | C26: {N} |
| R11 | C26 + C16 | N, ¬N | **∅** |

**Klausa kosong ditemukan → KB ⊨ N terbukti** ✓

**2e. Syarat pembatalan peluncuran (10 poin)**

**Syarat pembatalan:** Peluncuran TIDAK BOLEH jika:
- (i) target belum dikonfirmasi hostile (¬K), ATAU
- (ii) zona sipil tidak clear (¬Z), ATAU
- (iii) komandan tidak mengotorisasi (¬B)

**Representasi logika:**

$$(¬K ∨ ¬Z ∨ ¬B) ⇒ ¬L$$

Atau secara ekuivalen (kontraposisi):

$$L ⇒ (K ∧ Z ∧ B)$$

"Jika peluncuran diotorisasi, maka target hostile DAN zona clear DAN komandan mengotorisasi."

**Pembuktian bahwa KB sudah mencakup semua syarat:**

1. **Syarat (i):** Aturan 2 menyatakan ¬K ⇒ ¬L ✓
2. **Syarat (ii):** Aturan 8 menyatakan ¬Z ⇒ ¬L ✓
3. **Syarat (iii):** Dari Aturan 4: (O ∧ B) ⇒ L. Kontraposisinya: ¬L ∨ ¬O ∨ ¬B ∨ L, tapi lebih relevan: tanpa B, premis O ∧ B tidak terpenuhi sehingga L tidak bisa disimpulkan. Meskipun ¬B ⇒ ¬L tidak dinyatakan secara eksplisit, L hanya dapat bernilai True melalui Aturan 4 yang memerlukan B. Jadi KB secara implisit menjamin syarat (iii) ✓

**Catatan:** Untuk membuat syarat (iii) lebih eksplisit, sebaiknya ditambahkan aturan: ¬B ⇒ ¬L ke KB.

---

## Rubrik Penilaian

### Pilihan Ganda
- Setiap soal benar: 2 poin
- Total: 40 poin

### Uraian
- Soal ⭐: maksimal 5 poin
- Soal ⭐⭐: maksimal 8 poin
- Soal ⭐⭐⭐: maksimal 12 poin
- Total: 120 poin

### Studi Kasus
- Studi Kasus 1: 75 poin
- Studi Kasus 2: 75 poin
- Total: 150 poin

### Total Keseluruhan: 310 poin

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
