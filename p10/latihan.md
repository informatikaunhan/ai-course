# Latihan Pertemuan 10: Representasi Pengetahuan - Logika Predikat (First-Order Logic)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 10  
**Topik:** Representasi Pengetahuan - Logika Predikat (First-Order Logic)  
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
Manakah yang merupakan keterbatasan utama logika proposisional dibandingkan logika predikat?

A. Tidak dapat menggunakan konnektif logika  
B. Tidak dapat merepresentasikan objek individual, properti, dan relasi secara umum  
C. Tidak dapat melakukan inferensi  
D. Tidak dapat merepresentasikan nilai kebenaran  
E. Tidak dapat menggunakan tabel kebenaran

---

### Soal 2
Dalam sintaks FOL, elemen yang merujuk pada objek tertentu yang sudah diketahui disebut:

A. Variabel  
B. Predikat  
C. Konstanta  
D. Fungsi  
E. Kuantor

---

### Soal 3
Manakah yang merupakan **term** dalam FOL?

A. Pilot(Adi)  
B. ∀x  
C. komandanDari(Adi)  
D. ⇒  
E. ∧

---

### Soal 4
Kalimat FOL `LebihCepat(DroneAlpha, HeliBlack)` termasuk dalam kategori:

A. Kalimat kompleks  
B. Kalimat atomik  
C. Term  
D. Kuantor  
E. Fungsi

---

### Soal 5
Representasi FOL yang BENAR untuk "Semua tentara berani" adalah:

A. ∀x [Tentara(x) ∧ Berani(x)]  
B. ∀x [Tentara(x) ⇒ Berani(x)]  
C. ∃x [Tentara(x) ⇒ Berani(x)]  
D. ∃x [Tentara(x) ∧ Berani(x)]  
E. ∀x [Berani(x) ⇒ Tentara(x)]

---

### Soal 6
Representasi FOL yang BENAR untuk "Ada kapal selam di perairan Natuna" adalah:

A. ∀x [KapalSelam(x) ⇒ DiPerairan(x, Natuna)]  
B. ∀x [KapalSelam(x) ∧ DiPerairan(x, Natuna)]  
C. ∃x [KapalSelam(x) ⇒ DiPerairan(x, Natuna)]  
D. ∃x [KapalSelam(x) ∧ DiPerairan(x, Natuna)]  
E. ¬∀x [¬KapalSelam(x) ∧ DiPerairan(x, Natuna)]

---

### Soal 7
Pernyataan FOL ∀x ∃y Suka(x, y) berarti:

A. Ada seseorang yang menyukai semua orang  
B. Semua orang menyukai semua orang  
C. Setiap orang menyukai setidaknya satu orang  
D. Ada seseorang yang disukai semua orang  
E. Tidak ada yang menyukai siapapun

---

### Soal 8
Manakah pernyataan yang BENAR tentang hubungan kuantor?

A. ∀x P(x) ≡ ∃x P(x)  
B. ¬∀x P(x) ≡ ∀x ¬P(x)  
C. ¬∀x P(x) ≡ ∃x ¬P(x)  
D. ∃x P(x) ≡ ∀x P(x)  
E. ¬∃x P(x) ≡ ∃x ¬P(x)

---

### Soal 9
Hasil unifikasi `Menembak(x, y)` dengan `Menembak(DroneA, TargetB)` adalah:

A. GAGAL  
B. θ = {x/DroneA}  
C. θ = {y/TargetB}  
D. θ = {x/DroneA, y/TargetB}  
E. θ = {DroneA/x, TargetB/y}

---

### Soal 10
Unifikasi `Pilot(Adi)` dengan `Pilot(Budi)` menghasilkan:

A. θ = {Adi/Budi}  
B. θ = {Budi/Adi}  
C. θ = {}  
D. GAGAL  
E. θ = {x/Adi, x/Budi}

---

### Soal 11
Apa yang dimaksud dengan Most General Unifier (MGU)?

A. Substitusi yang paling banyak variabelnya  
B. Substitusi paling umum yang membuat dua ekspresi identik  
C. Substitusi yang mengganti semua variabel dengan konstanta  
D. Substitusi yang hanya menggunakan satu variabel  
E. Substitusi yang selalu berhasil untuk semua ekspresi

---

### Soal 12
Unifikasi `Q(x, x)` dengan `Q(Adi, Budi)` akan:

A. Berhasil dengan θ = {x/Adi}  
B. Berhasil dengan θ = {x/Budi}  
C. Berhasil dengan θ = {x/Adi, x/Budi}  
D. GAGAL karena x tidak bisa menjadi dua konstanta berbeda  
E. Berhasil dengan θ = {}

---

### Soal 13
Forward chaining dimulai dari:

A. Query yang ingin dibuktikan  
B. Fakta-fakta yang sudah diketahui  
C. Aturan yang paling kompleks  
D. Kesimpulan yang diharapkan  
E. Variabel yang belum ter-assign

---

### Soal 14
Backward chaining juga disebut:

A. Data-driven reasoning  
B. Bottom-up reasoning  
C. Goal-driven reasoning  
D. Breadth-first reasoning  
E. Forward reasoning

---

### Soal 15
Diberikan fakta Pilot(Adi) dan aturan ∀x [Pilot(x) ⇒ Terlatih(x)]. Hasil forward chaining dengan θ = {x/Adi} adalah:

A. Pilot(x)  
B. Terlatih(x)  
C. Terlatih(Adi)  
D. ¬Pilot(Adi)  
E. Pilot(Adi) ⇒ Terlatih(Adi)

---

### Soal 16
Pada proses konversi ke CNF dalam FOL, langkah Skolemisasi berfungsi untuk:

A. Menghapus kuantor universal  
B. Mengganti kuantor eksistensial dengan fungsi Skolem  
C. Mendistribusikan disjungsi atas konjungsi  
D. Mengeliminasi implikasi  
E. Melakukan negasi seluruh kalimat

---

### Soal 17
Komponen Expert System yang berfungsi melakukan inferensi (forward/backward chaining) adalah:

A. Knowledge Base  
B. Inference Engine  
C. User Interface  
D. Explanation Facility  
E. Working Memory

---

### Soal 18
Knowledge Graph triple (KRI_Nanggala, jenisKapal, KapalSelam) ekuivalen dengan FOL:

A. ∀x [KRI_Nanggala(x) ⇒ KapalSelam(x)]  
B. JenisKapal(KRI_Nanggala, KapalSelam)  
C. KapalSelam(KRI_Nanggala)  
D. ∃x [JenisKapal(x, KapalSelam)]  
E. KRI_Nanggala = KapalSelam

---

### Soal 19
Unifikasi `R(x, f(x))` dengan `R(y, y)` akan:

A. Berhasil dengan θ = {x/y}  
B. Berhasil dengan θ = {y/f(x)}  
C. GAGAL karena occur check  
D. Berhasil dengan θ = {x/f(y), y/f(x)}  
E. Berhasil dengan θ = {}

---

### Soal 20
Generalized Modus Ponens menggabungkan:

A. Modus Ponens dengan resolusi  
B. Modus Ponens dengan unifikasi  
C. Modus Tollens dengan forward chaining  
D. Resolusi dengan backward chaining  
E. Modus Tollens dengan unifikasi

---

## Bagian B: Soal Uraian (15 Soal)

### Soal 1 ⭐
Jelaskan tiga keterbatasan utama logika proposisional yang diatasi oleh logika predikat! Berikan contoh untuk masing-masing keterbatasan!

---

### Soal 2 ⭐
Sebutkan dan jelaskan enam elemen dasar sintaks FOL! Berikan satu contoh untuk masing-masing elemen!

---

### Soal 3 ⭐
Jelaskan perbedaan antara term dan kalimat atomik dalam FOL! Berikan dua contoh masing-masing!

---

### Soal 4 ⭐
Jelaskan mengapa ∀x [Tentara(x) ∧ Berani(x)] adalah representasi yang SALAH untuk "Semua tentara berani"! Berikan representasi yang benar!

---

### Soal 5 ⭐⭐
Terjemahkan kalimat-kalimat berikut ke dalam FOL:
1. "Adi adalah pilot dan Adi ditempatkan di Madiun"
2. "Semua pesawat tempur di Skuadron 11 dilengkapi rudal"
3. "Ada drone yang lebih cepat dari semua helikopter"
4. "Tidak semua radar berfungsi normal"

---

### Soal 6 ⭐⭐
Terjemahkan dan bandingkan dua kalimat berikut dalam FOL:
- (a) "Setiap markas memiliki setidaknya satu penjaga"
- (b) "Ada satu penjaga yang menjaga semua markas"

Jelaskan mengapa kedua kalimat ini TIDAK ekuivalen!

---

### Soal 7 ⭐⭐
Temukan MGU untuk setiap pasangan ekspresi berikut, atau nyatakan jika gagal:
1. `Patroli(x, y)` dan `Patroli(KapalA, Natuna)`
2. `Atasan(komandanDari(x), x)` dan `Atasan(y, Adi)`
3. `Senjata(x, x)` dan `Senjata(Rudal, Torpedo)`
4. `Misi(x, f(y))` dan `Misi(g(z), f(z))`

---

### Soal 8 ⭐⭐
Jelaskan perbedaan antara forward chaining dan backward chaining! Kapan masing-masing metode lebih efisien? Berikan contoh situasi untuk masing-masing!

---

### Soal 9 ⭐⭐
Diberikan knowledge base:

**Fakta:** Pilot(Adi), Perwira(Adi), Berpengalaman(Adi)

**Aturan:**
- ∀x [Pilot(x) ⇒ Terlatih(x)]
- ∀x [(Perwira(x) ∧ Terlatih(x)) ⇒ BolehMemimpin(x)]
- ∀x [(BolehMemimpin(x) ∧ Berpengalaman(x)) ⇒ KandidatKomandan(x)]

Gunakan forward chaining untuk membuktikan KandidatKomandan(Adi)! Tunjukkan tabel trace lengkap!

---

### Soal 10 ⭐⭐
Menggunakan knowledge base yang sama pada Soal 9, gunakan backward chaining untuk membuktikan KandidatKomandan(Adi)! Gambarkan pohon backward chaining!

---

### Soal 11 ⭐⭐
Jelaskan apa yang dimaksud dengan occur check dalam unifikasi! Mengapa unifikasi `x` dengan `f(x)` harus gagal? Berikan contoh konsekuensi jika occur check diabaikan!

---

### Soal 12 ⭐⭐⭐
Diberikan knowledge base sistem keamanan cyber:

**Fakta:**
1. ServerWeb(S1)
2. TerhubungInternet(S1)
3. VersiLama(S1)
4. ServerDB(S2)
5. TerhubungKe(S1, S2)

**Aturan:**
6. ∀x [(ServerWeb(x) ∧ TerhubungInternet(x)) ⇒ DapatDiserang(x)]
7. ∀x [(DapatDiserang(x) ∧ VersiLama(x)) ⇒ Rentan(x)]
8. ∀x ∀y [(Rentan(x) ∧ TerhubungKe(x, y)) ⇒ TerancamLateral(y)]
9. ∀x [(TerancamLateral(x) ∧ ServerDB(x)) ⇒ DataTerancam(x)]

Gunakan forward chaining untuk membuktikan DataTerancam(S2)! Tunjukkan trace lengkap dan jelaskan chain of reasoning!

---

### Soal 13 ⭐⭐⭐
Konversi kalimat FOL berikut ke Conjunctive Normal Form (CNF). Tunjukkan setiap langkah transformasi!

$$\forall x \, [\text{Tentara}(x) \Rightarrow \exists y \, [\text{Senjata}(y) \wedge \text{Membawa}(x, y)]]$$

---

### Soal 14 ⭐⭐⭐
Terapkan Generalized Modus Ponens pada kasus berikut:

**Fakta:**
- Drone(Alpha7)
- BersenajataLengkap(Alpha7)
- WilayahKonflik(Natuna)

**Aturan:** ∀d ∀w [(Drone(d) ∧ BersenajataLengkap(d) ∧ WilayahKonflik(w)) ⇒ SiapTempur(d, w)]

Tunjukkan proses unifikasi dan kesimpulan yang dihasilkan!

---

### Soal 15 ⭐⭐⭐
Rancang knowledge base sederhana (dalam FOL) untuk expert system diagnosis kerusakan radar militer! Knowledge base harus mencakup:
- Minimal 4 fakta gejala
- Minimal 4 aturan diagnosis
- Minimal 2 aturan tindakan

Tunjukkan bagaimana forward chaining menghasilkan diagnosis dan rekomendasi tindakan untuk satu skenario!

---

## Bagian C: Studi Kasus (2 Kasus)

### Studi Kasus 1: Sistem Intelijen Ancaman Maritim

**Latar Belakang:**

Pusat Informasi dan Koordinasi Pengamanan Maritim Indonesia sedang mengembangkan knowledge-based system untuk analisis ancaman maritim di perairan Indonesia. Sistem ini harus mampu merepresentasikan dan menganalisis pengetahuan tentang kapal-kapal yang melintas di perairan Indonesia menggunakan logika predikat.

**Domain pengetahuan yang tersedia:**

**Entitas:** Kapal (KapalX1, KapalX2, KapalY1), Perairan (Natuna, Makassar, Malaka), Negara (Indonesia, Xlandia, Ylandia), Pangkalan AL (Surabaya, Jakarta, Manado)

**Fakta yang teridentifikasi:**
1. KapalX1 adalah kapal selam, berbendera Xlandia
2. KapalX2 adalah kapal perang destroyer, berbendera Xlandia
3. KapalY1 adalah kapal riset, berbendera Ylandia
4. KapalX1 terdeteksi di perairan Natuna
5. KapalX2 terdeteksi di perairan Natuna
6. KapalY1 terdeteksi di perairan Makassar
7. KapalX1 mematikan transponder AIS
8. KapalX1 melakukan pola manuver pengintaian
9. Xlandia memiliki klaim teritorial atas Natuna
10. Indonesia memiliki kedaulatan atas Natuna
11. Indonesia memiliki kedaulatan atas Makassar
12. Pangkalan AL terdekat dari Natuna adalah Jakarta
13. Pangkalan AL terdekat dari Makassar adalah Surabaya

**Aturan analisis ancaman:**
- Jika kapal asing berada di perairan yang diklaim Indonesia, maka kapal tersebut perlu diverifikasi
- Jika kapal selam asing mematikan transponder di perairan Indonesia, maka kapal tersebut mencurigakan
- Jika kapal mencurigakan melakukan pola manuver pengintaian, maka kapal tersebut merupakan ancaman intelijen
- Jika kapal berasal dari negara yang memiliki klaim teritorial atas perairan tempat kapal berada, maka situasi adalah sengketa
- Jika terdapat ancaman intelijen di perairan tertentu dan situasi sengketa di perairan yang sama, maka tingkat ancaman adalah TINGGI
- Jika tingkat ancaman TINGGI di suatu perairan, maka kerahkan aset dari pangkalan terdekat

**Pertanyaan:**

**1a.** Definisikan semua predikat yang diperlukan untuk merepresentasikan domain ini! Minimal 12 predikat beserta aritas dan penjelasannya. (10 poin)

**1b.** Representasikan SEMUA fakta (1-13) dalam FOL! (15 poin)

**1c.** Representasikan SEMUA aturan analisis ancaman dalam FOL menggunakan kuantor! (15 poin)

**1d.** Gunakan forward chaining untuk menentukan tingkat ancaman di perairan Natuna! Tunjukkan trace lengkap setiap langkah inferensi! (15 poin)

**1e.** Gunakan backward chaining untuk membuktikan bahwa aset dari pangkalan Jakarta harus dikerahkan! Gambarkan pohon backward chaining lengkap! (10 poin)

---

### Studi Kasus 2: Expert System Kesiapan Tempur Skuadron Udara

**Latar Belakang:**

TNI Angkatan Udara mengembangkan expert system berbasis FOL untuk mengevaluasi kesiapan tempur skuadron pesawat tempur. Sistem ini mengintegrasikan informasi tentang personel, pesawat, persenjataan, dan kondisi operasional.

**Domain pengetahuan:**

**Entitas:** Pilot (Adi, Budi, Citra), Pesawat (F16_01, F16_02, SU30_01), Senjata (AIM9, AIM120, BombGBU), Skuadron (Skuadron11, Skuadron14)

**Knowledge Base:**

*Fakta personel:*
1. Pilot(Adi), Pilot(Budi), Pilot(Citra)
2. Perwira(Adi), Perwira(Budi), Perwira(Citra)
3. JamTerbang(Adi, 2500), JamTerbang(Budi, 800), JamTerbang(Citra, 1500)
4. SertifikasiTempur(Adi), SertifikasiTempur(Citra)
5. LolosKesehatanTerbang(Adi), LolosKesehatanTerbang(Budi), LolosKesehatanTerbang(Citra)
6. DiSkuadron(Adi, Skuadron11), DiSkuadron(Budi, Skuadron11), DiSkuadron(Citra, Skuadron14)

*Fakta pesawat:*
7. Pesawat(F16_01), Pesawat(F16_02), Pesawat(SU30_01)
8. TipePesawat(F16_01, F16), TipePesawat(F16_02, F16), TipePesawat(SU30_01, SU30)
9. StatusTeknisOK(F16_01), StatusTeknisOK(SU30_01)
10. BahanBakarPenuh(F16_01), BahanBakarPenuh(F16_02), BahanBakarPenuh(SU30_01)
11. DiSkuadron(F16_01, Skuadron11), DiSkuadron(F16_02, Skuadron11), DiSkuadron(SU30_01, Skuadron14)

*Fakta persenjataan:*
12. Terpasang(AIM9, F16_01), Terpasang(AIM120, F16_01)
13. Terpasang(AIM9, SU30_01), Terpasang(BombGBU, SU30_01)

*Aturan kesiapan:*
14. ∀p [(Pilot(p) ∧ SertifikasiTempur(p) ∧ LolosKesehatanTerbang(p)) ⇒ PilotSiap(p)]
15. ∀p [(Pilot(p) ∧ ¬SertifikasiTempur(p)) ⇒ PerluSertifikasi(p)]
16. ∀a [(Pesawat(a) ∧ StatusTeknisOK(a) ∧ BahanBakarPenuh(a)) ⇒ PesawatSiap(a)]
17. ∀a [(Pesawat(a) ∧ ¬StatusTeknisOK(a)) ⇒ PerluPerbaikan(a)]
18. ∀a [∃s (Terpasang(s, a)) ⇒ Bersenjata(a)]
19. ∀p ∀a ∀sk [(PilotSiap(p) ∧ PesawatSiap(a) ∧ Bersenjata(a) ∧ DiSkuadron(p, sk) ∧ DiSkuadron(a, sk)) ⇒ PasanganSiapTempur(p, a)]
20. ∀sk [∃p ∃a (PasanganSiapTempur(p, a) ∧ DiSkuadron(p, sk)) ⇒ SkuadronOperasional(sk)]
21. ∀p [(Pilot(p) ∧ JamTerbangTinggi(p) ∧ PilotSiap(p)) ⇒ PilotSenior(p)]
22. JamTerbangTinggi(x) ⇐ JamTerbang(x, n) ∧ n ≥ 1000

**Pertanyaan:**

**2a.** Gunakan forward chaining untuk menentukan semua pilot yang siap tempur (PilotSiap) dan semua pesawat yang siap (PesawatSiap)! Tunjukkan trace untuk setiap individu! (15 poin)

**2b.** Identifikasi semua pasangan pilot-pesawat yang siap tempur (PasanganSiapTempur)! Jelaskan mengapa beberapa pasangan tidak terbentuk! (15 poin)

**2c.** Gunakan backward chaining untuk membuktikan SkuadronOperasional(Skuadron11)! Gambarkan pohon backward chaining! (15 poin)

**2d.** Pilot Budi tidak memiliki SertifikasiTempur. Buat representasi FOL untuk menambahkan aturan berikut ke knowledge base:
- "Jika pilot perlu sertifikasi dan jam terbangnya di atas 500, maka pilot eligible untuk ujian sertifikasi"
- "Jika pilot eligible untuk ujian sertifikasi dan lulus ujian, maka pilot mendapatkan sertifikasi tempur"

Lakukan forward chaining untuk menentukan apakah Budi eligible untuk ujian sertifikasi! (10 poin)

**2e.** Rancang tiga aturan tambahan (dalam FOL) untuk menangani skenario eskalasi: jika skuadron operasional dan ada perintah dari komando, maka skuadron melakukan scramble. Definisikan predikat baru yang diperlukan dan tunjukkan contoh forward chaining untuk skenario tersebut! (10 poin)

---

## Kunci Jawaban

### Bagian A: Pilihan Ganda

| No | Jawaban | Penjelasan |
|----|---------|------------|
| 1 | **B** | Logika proposisional tidak dapat merepresentasikan objek individual, properti objek, dan relasi antar objek secara umum (general) |
| 2 | **C** | Konstanta merujuk pada objek tertentu yang sudah diketahui (contoh: Adi, Jakarta, DroneAlpha7) |
| 3 | **C** | Term dapat berupa konstanta, variabel, atau fungsi yang diterapkan pada term. `komandanDari(Adi)` adalah fungsi pada konstanta, jadi merupakan term. `Pilot(Adi)` adalah kalimat atomik (predikat), bukan term |
| 4 | **B** | Kalimat atomik terbentuk dari predikat yang diterapkan pada term. `LebihCepat(DroneAlpha, HeliBlack)` adalah predikat biner pada dua konstanta |
| 5 | **B** | Kuantor universal biasanya dipasangkan dengan implikasi (⇒). Opsi A salah karena menyatakan "semua objek di dunia adalah tentara DAN berani" |
| 6 | **D** | Kuantor eksistensial biasanya dipasangkan dengan konjungsi (∧). Opsi C misleading karena terpenuhi oleh objek apapun yang bukan kapal selam |
| 7 | **C** | ∀x ∃y Suka(x, y) berarti "untuk setiap x, ada setidaknya satu y sehingga x menyukai y", yaitu setiap orang menyukai setidaknya satu orang |
| 8 | **C** | Negasi kuantor universal menjadi kuantor eksistensial dengan negasi predikat: ¬∀x P(x) ≡ ∃x ¬P(x) |
| 9 | **D** | Unifikasi argumen per posisi: x dengan DroneA dan y dengan TargetB menghasilkan θ = {x/DroneA, y/TargetB} |
| 10 | **D** | Dua konstanta berbeda (Adi dan Budi) tidak dapat diunifikasikan. Konstanta hanya berhasil diunifikasi jika identik |
| 11 | **B** | MGU adalah substitusi paling umum (minimal) yang membuat dua ekspresi menjadi identik |
| 12 | **D** | Variabel x harus diikat ke satu nilai. Unifikasi argumen 1 memberi x/Adi, tetapi argumen 2 memerlukan x/Budi. Kontradiksi, sehingga gagal |
| 13 | **B** | Forward chaining (data-driven) dimulai dari fakta yang diketahui dan menerapkan aturan untuk menghasilkan fakta baru |
| 14 | **C** | Backward chaining disebut goal-driven reasoning karena dimulai dari query (goal) dan bekerja mundur mencari fakta pendukung |
| 15 | **C** | Substitusi θ = {x/Adi} diterapkan pada conclusion Terlatih(x), menghasilkan Terlatih(Adi) |
| 16 | **B** | Skolemisasi mengganti kuantor eksistensial (∃) dengan fungsi Skolem, memungkinkan penghapusan kuantor eksistensial dari kalimat |
| 17 | **B** | Inference Engine adalah komponen yang melakukan proses inferensi menggunakan forward atau backward chaining |
| 18 | **B** | Triple (subjek, predikat, objek) diterjemahkan langsung menjadi kalimat atomik FOL: JenisKapal(KRI_Nanggala, KapalSelam) |
| 19 | **C** | Unifikasi x/y dari argumen 1, lalu argumen 2 menjadi f(y) vs y. Karena y muncul di dalam f(y), occur check gagal — substitusi akan menghasilkan loop tak terhingga |
| 20 | **B** | Generalized Modus Ponens menggabungkan aturan Modus Ponens standar dengan proses unifikasi untuk menangani variabel dalam FOL |

---

### Bagian B: Uraian

#### Jawaban Soal 1 ⭐

**Tiga keterbatasan utama logika proposisional:**

1. **Tidak ada objek individual:** Logika proposisional tidak dapat merujuk pada objek spesifik.
   - Contoh: Tidak bisa menyatakan "Drone Alpha-7" sebagai entitas tersendiri. Hanya bisa menyatakan proposisi `P = "Drone Alpha-7 aktif"` tanpa bisa memisahkan objek dari properti.

2. **Tidak ada properti dan relasi:** Tidak dapat menyatakan properti objek atau hubungan antar objek.
   - Contoh: Tidak bisa menyatakan "X adalah drone" atau "X lebih cepat dari Y" secara terpisah. Harus membuat proposisi baru untuk setiap kombinasi: `P1 = "Alpha lebih cepat dari Bravo"`, `P2 = "Alpha lebih cepat dari Charlie"`, dst.

3. **Tidak ada kuantifikasi:** Tidak dapat menyatakan "semua" atau "ada" secara umum.
   - Contoh: "Semua tentara harus berani" memerlukan satu proposisi per tentara: `Tentara1_Berani ∧ Tentara2_Berani ∧ ...`. Jika ada 10.000 tentara, diperlukan 10.000 proposisi. Dalam FOL cukup: `∀x [Tentara(x) ⇒ Berani(x)]`.

---

#### Jawaban Soal 2 ⭐

| Elemen | Penjelasan | Contoh |
|--------|------------|--------|
| **Konstanta** | Simbol yang merujuk pada objek tertentu yang sudah diketahui dalam domain | `Adi`, `Jakarta`, `DroneAlpha7` |
| **Variabel** | Simbol placeholder yang dapat merujuk pada objek apapun dalam domain | `x`, `y`, `z` |
| **Predikat** | Simbol yang menyatakan properti objek (unary) atau relasi antar objek (n-ary) | `Pilot(x)`, `LebihCepat(x, y)` |
| **Fungsi** | Simbol yang memetakan objek ke objek lain, menghasilkan term baru | `komandanDari(Adi)`, `ayahDari(x)` |
| **Konnektif** | Penghubung logika untuk membangun kalimat kompleks | ∧ (AND), ∨ (OR), ¬ (NOT), ⇒ (implikasi), ⇔ (bikonditional) |
| **Kuantor** | Simbol untuk kuantifikasi variabel dalam domain | ∀ (untuk semua), ∃ (ada/setidaknya satu) |

---

#### Jawaban Soal 3 ⭐

**Perbedaan term dan kalimat atomik:**

| Aspek | Term | Kalimat Atomik |
|-------|------|----------------|
| Definisi | Ekspresi yang merujuk pada **objek** | Ekspresi yang memiliki **nilai kebenaran** |
| Komponen | Konstanta, variabel, atau fungsi pada term | Predikat diterapkan pada term |
| Nilai | Merujuk ke suatu objek | True atau False |

**Contoh term:**
1. `Adi` — konstanta, merujuk pada individu bernama Adi
2. `komandanDari(Adi)` — fungsi, merujuk pada objek "komandan dari Adi"

**Contoh kalimat atomik:**
1. `Pilot(Adi)` — predikat unary, bernilai true/false
2. `LebihCepat(DroneAlpha, HeliBlack)` — predikat binary, bernilai true/false

---

#### Jawaban Soal 4 ⭐

**Mengapa ∀x [Tentara(x) ∧ Berani(x)] salah:**

Kalimat ini menyatakan: "Untuk semua x di dunia, x adalah tentara DAN x berani." Artinya setiap objek di seluruh domain (meja, kucing, bangunan) semuanya adalah tentara dan semuanya berani. Ini jelas salah secara semantik.

**Representasi yang benar:**

$$\forall x \, [\text{Tentara}(x) \Rightarrow \text{Berani}(x)]$$

Arti: "Untuk semua x, JIKA x adalah tentara, MAKA x berani." Implikasi membatasi pernyataan hanya pada objek yang memenuhi antecedent (tentara). Objek yang bukan tentara membuat implikasi bernilai true secara vakus (vacuously true), sehingga tidak memaksakan properti pada seluruh domain.

**Aturan umum:** Kuantor universal (∀) biasanya dipasangkan dengan implikasi (⇒), bukan konjungsi (∧).

---

#### Jawaban Soal 5 ⭐⭐

**1.** "Adi adalah pilot dan Adi ditempatkan di Madiun"

$$\text{Pilot}(\text{Adi}) \wedge \text{Ditempatkan}(\text{Adi}, \text{Madiun})$$

**2.** "Semua pesawat tempur di Skuadron 11 dilengkapi rudal"

$$\forall x \, [(\text{PesawatTempur}(x) \wedge \text{DiSkuadron}(x, \text{Skuadron11})) \Rightarrow \text{Dilengkapi}(x, \text{Rudal})]$$

**3.** "Ada drone yang lebih cepat dari semua helikopter"

$$\exists x \, [\text{Drone}(x) \wedge \forall y \, [\text{Helikopter}(y) \Rightarrow \text{LebihCepat}(x, y)]]$$

**4.** "Tidak semua radar berfungsi normal"

$$\neg \forall x \, [\text{Radar}(x) \Rightarrow \text{Normal}(x)]$$

Ekuivalen dengan:

$$\exists x \, [\text{Radar}(x) \wedge \neg\text{Normal}(x)]$$

---

#### Jawaban Soal 6 ⭐⭐

**Predikat:**
- `Markas(x)` — x adalah markas
- `Penjaga(y)` — y adalah penjaga
- `Menjaga(y, x)` — y menjaga x

**(a)** "Setiap markas memiliki setidaknya satu penjaga"

$$\forall x \, [\text{Markas}(x) \Rightarrow \exists y \, [\text{Penjaga}(y) \wedge \text{Menjaga}(y, x)]]$$

**(b)** "Ada satu penjaga yang menjaga semua markas"

$$\exists y \, [\text{Penjaga}(y) \wedge \forall x \, [\text{Markas}(x) \Rightarrow \text{Menjaga}(y, x)]]$$

**Mengapa TIDAK ekuivalen:**

| Aspek | Kalimat (a) | Kalimat (b) |
|-------|-------------|-------------|
| Kuantor luar | ∀x (setiap markas) | ∃y (ada satu penjaga) |
| Kuantor dalam | ∃y (ada penjaga, bisa berbeda) | ∀x (semua markas) |
| Arti | Penjaga bisa berbeda per markas | Satu penjaga yang sama untuk semua |
| (b) ⇒ (a)? | Ya, selalu | — |
| (a) ⇒ (b)? | — | Tidak selalu |

Kalimat (b) lebih kuat: jika ada satu penjaga yang menjaga semua markas, maka pasti setiap markas punya penjaga. Tetapi sebaliknya tidak berlaku — bisa saja setiap markas punya penjaga yang berbeda-beda tanpa ada satu penjaga universal.

---

#### Jawaban Soal 7 ⭐⭐

**Pasangan 1:** `Patroli(x, y)` dan `Patroli(KapalA, Natuna)`
- Predikat sama: Patroli ✅
- Argumen 1: x ↔ KapalA → {x/KapalA}
- Argumen 2: y ↔ Natuna → {y/Natuna}
- **MGU = {x/KapalA, y/Natuna}** ✅

**Pasangan 2:** `Atasan(komandanDari(x), x)` dan `Atasan(y, Adi)`
- Predikat sama: Atasan ✅
- Argumen 1: komandanDari(x) ↔ y → {y/komandanDari(x)}
- Argumen 2: x ↔ Adi → {x/Adi}
- Terapkan x/Adi ke y: y = komandanDari(Adi)
- **MGU = {x/Adi, y/komandanDari(Adi)}** ✅

**Pasangan 3:** `Senjata(x, x)` dan `Senjata(Rudal, Torpedo)`
- Predikat sama: Senjata ✅
- Argumen 1: x ↔ Rudal → {x/Rudal}
- Argumen 2: terapkan substitusi → Senjata(Rudal, Rudal) vs Senjata(Rudal, Torpedo)
- Rudal ≠ Torpedo → **GAGAL** ❌

**Pasangan 4:** `Misi(x, f(y))` dan `Misi(g(z), f(z))`
- Predikat sama: Misi ✅
- Argumen 1: x ↔ g(z) → {x/g(z)}
- Argumen 2: f(y) ↔ f(z) → fungsi sama, unifikasi argumen: y ↔ z → {y/z}
- **MGU = {x/g(z), y/z}** ✅

---

#### Jawaban Soal 8 ⭐⭐

**Perbedaan:**

| Aspek | Forward Chaining | Backward Chaining |
|-------|------------------|-------------------|
| Arah | Fakta → Kesimpulan | Goal → Fakta |
| Nama lain | Data-driven | Goal-driven |
| Mulai dari | Fakta yang diketahui | Query yang ditanyakan |
| Strategi | Bottom-up | Top-down |
| Proses | Menerapkan semua aturan pada fakta yang ada | Mencari aturan yang conclusion-nya cocok dengan goal |

**Kapan forward chaining lebih efisien:**
- KB kecil dengan sedikit fakta awal tetapi banyak query
- Semua fakta relevan terhadap query
- Contoh: Monitoring real-time di mana semua data sensor harus diproses dan banyak alert yang mungkin dihasilkan

**Kapan backward chaining lebih efisien:**
- KB besar dengan banyak fakta tetapi satu query spesifik
- Banyak fakta yang tidak relevan terhadap query
- Contoh: Diagnosis spesifik — "Apakah radar ini rusak karena masalah antena?" di mana hanya perlu memeriksa fakta terkait antena

---

#### Jawaban Soal 9 ⭐⭐

**Forward Chaining untuk KandidatKomandan(Adi):**

**KB awal:**
- Fakta: Pilot(Adi), Perwira(Adi), Berpengalaman(Adi)
- Aturan 1: ∀x [Pilot(x) ⇒ Terlatih(x)]
- Aturan 2: ∀x [(Perwira(x) ∧ Terlatih(x)) ⇒ BolehMemimpin(x)]
- Aturan 3: ∀x [(BolehMemimpin(x) ∧ Berpengalaman(x)) ⇒ KandidatKomandan(x)]

**Trace:**

| Langkah | Aturan | Premis yang Cocok | Substitusi | Fakta Baru |
|---------|--------|-------------------|------------|------------|
| 1 | Aturan 1 | Pilot(Adi) ✅ | {x/Adi} | **Terlatih(Adi)** |
| 2 | Aturan 2 | Perwira(Adi) ✅ ∧ Terlatih(Adi) ✅ | {x/Adi} | **BolehMemimpin(Adi)** |
| 3 | Aturan 3 | BolehMemimpin(Adi) ✅ ∧ Berpengalaman(Adi) ✅ | {x/Adi} | **KandidatKomandan(Adi)** 🎯 |

**Kesimpulan:** KandidatKomandan(Adi) terbukti dalam 3 langkah inferensi.

---

#### Jawaban Soal 10 ⭐⭐

**Backward Chaining untuk KandidatKomandan(Adi):**

```
Goal: KandidatKomandan(Adi)
│
├── Cocok dengan Aturan 3: (BolehMemimpin(x) ∧ Berpengalaman(x)) ⇒ KandidatKomandan(x)
│   θ = {x/Adi}
│
├── Sub-goal 1: BolehMemimpin(Adi)
│   │
│   ├── Cocok dengan Aturan 2: (Perwira(x) ∧ Terlatih(x)) ⇒ BolehMemimpin(x)
│   │   θ = {x/Adi}
│   │
│   ├── Sub-goal 1.1: Perwira(Adi)
│   │   └── Fakta di KB ✅
│   │
│   └── Sub-goal 1.2: Terlatih(Adi)
│       │
│       ├── Cocok dengan Aturan 1: Pilot(x) ⇒ Terlatih(x)
│       │   θ = {x/Adi}
│       │
│       └── Sub-goal 1.2.1: Pilot(Adi)
│           └── Fakta di KB ✅
│
└── Sub-goal 2: Berpengalaman(Adi)
    └── Fakta di KB ✅

Semua sub-goal terbukti → KandidatKomandan(Adi) TERBUKTI ✅
```

---

#### Jawaban Soal 11 ⭐⭐

**Occur Check:** Mekanisme pengecekan dalam algoritma unifikasi yang mencegah unifikasi suatu variabel x dengan term yang mengandung x itu sendiri.

**Mengapa unifikasi x dengan f(x) harus gagal:**

Jika kita mengizinkan θ = {x/f(x)}, maka terapkan substitusi:
- x menjadi f(x)
- Tetapi x di dalam f(x) juga harus disubstitusi: f(f(x))
- Lalu f(f(f(x))), dan seterusnya...
- Hasil: f(f(f(f(...)))) → **substitusi tak terhingga**

**Contoh konsekuensi jika occur check diabaikan:**

Unifikasi `R(x, f(x))` dengan `R(y, y)`:
1. Argumen 1: x ↔ y → {x/y}
2. Argumen 2: f(y) ↔ y → tanpa occur check: {y/f(y)}
3. Terapkan: y = f(y) = f(f(y)) = f(f(f(y))) = ...
4. Term menjadi tak terhingga, program tidak akan berhenti (infinite loop)

Oleh karena itu occur check wajib dilakukan untuk menjamin terminasi algoritma unifikasi.

---

#### Jawaban Soal 12 ⭐⭐⭐

**Forward Chaining untuk DataTerancam(S2):**

**KB awal:** ServerWeb(S1), TerhubungInternet(S1), VersiLama(S1), ServerDB(S2), TerhubungKe(S1, S2)

| Langkah | Aturan | Premis yang Cocok | Substitusi | Fakta Baru |
|---------|--------|-------------------|------------|------------|
| 1 | Aturan 6 | ServerWeb(S1) ✅ ∧ TerhubungInternet(S1) ✅ | {x/S1} | **DapatDiserang(S1)** |
| 2 | Aturan 7 | DapatDiserang(S1) ✅ ∧ VersiLama(S1) ✅ | {x/S1} | **Rentan(S1)** |
| 3 | Aturan 8 | Rentan(S1) ✅ ∧ TerhubungKe(S1, S2) ✅ | {x/S1, y/S2} | **TerancamLateral(S2)** |
| 4 | Aturan 9 | TerancamLateral(S2) ✅ ∧ ServerDB(S2) ✅ | {x/S2} | **DataTerancam(S2)** 🎯 |

**Chain of reasoning:** Server web S1 terhubung ke internet sehingga dapat diserang. Karena menjalankan versi lama, S1 menjadi rentan. Kerentanan S1 menyebar melalui koneksi ke S2 (lateral movement), dan karena S2 adalah server database, data di S2 menjadi terancam.

**Kesimpulan:** DataTerancam(S2) terbukti dalam 4 langkah. Ini mengilustrasikan bagaimana serangan cyber dapat mengeksploitasi chain of vulnerabilities dari web server ke database melalui lateral movement.

---

#### Jawaban Soal 13 ⭐⭐⭐

**Kalimat awal:**

$$\forall x \, [\text{Tentara}(x) \Rightarrow \exists y \, [\text{Senjata}(y) \wedge \text{Membawa}(x, y)]]$$

**Step 1: Eliminasi implikasi (⇒)**

$$\forall x \, [\neg\text{Tentara}(x) \vee \exists y \, [\text{Senjata}(y) \wedge \text{Membawa}(x, y)]]$$

**Step 2: Skolemisasi** — ganti ∃y dengan fungsi Skolem

Karena y berada dalam scope ∀x, ganti y dengan fungsi Skolem f(x) yang bergantung pada x:

$$\forall x \, [\neg\text{Tentara}(x) \vee [\text{Senjata}(f(x)) \wedge \text{Membawa}(x, f(x))]]$$

**Step 3: Hapus kuantor universal (∀)**

$$\neg\text{Tentara}(x) \vee [\text{Senjata}(f(x)) \wedge \text{Membawa}(x, f(x))]$$

**Step 4: Distribusi ∨ atas ∧**

$$[\neg\text{Tentara}(x) \vee \text{Senjata}(f(x))] \wedge [\neg\text{Tentara}(x) \vee \text{Membawa}(x, f(x))]$$

**Hasil CNF — dua klausa:**
- Klausa 1: ¬Tentara(x) ∨ Senjata(f(x))
- Klausa 2: ¬Tentara(x) ∨ Membawa(x, f(x))

Fungsi Skolem f(x) merepresentasikan "senjata yang dibawa oleh tentara x". Setiap tentara memiliki senjata masing-masing yang bergantung pada identitas tentara.

---

#### Jawaban Soal 14 ⭐⭐⭐

**Generalized Modus Ponens:**

$$\frac{p_1', p_2', ..., p_n', \quad (p_1 \wedge p_2 \wedge ... \wedge p_n \Rightarrow q)}{q\theta}$$

**Step 1: Identifikasi premis dan aturan**

- p₁' = Drone(Alpha7)
- p₂' = BersenajataLengkap(Alpha7)
- p₃' = WilayahKonflik(Natuna)
- Aturan: ∀d ∀w [(Drone(d) ∧ BersenajataLengkap(d) ∧ WilayahKonflik(w)) ⇒ SiapTempur(d, w)]

**Step 2: Proses unifikasi**

| Premis Aturan | Premis Fakta | Substitusi |
|---------------|--------------|------------|
| Drone(d) | Drone(Alpha7) | {d/Alpha7} |
| BersenajataLengkap(d) | BersenajataLengkap(Alpha7) | {d/Alpha7} ✅ konsisten |
| WilayahKonflik(w) | WilayahKonflik(Natuna) | {w/Natuna} |

MGU: θ = {d/Alpha7, w/Natuna}

**Step 3: Terapkan θ ke conclusion**

$$\text{SiapTempur}(d, w) \cdot \theta = \text{SiapTempur}(\text{Alpha7}, \text{Natuna})$$

**Jawaban:** Dari Generalized Modus Ponens, kita menyimpulkan **SiapTempur(Alpha7, Natuna)** — Drone Alpha7 siap tempur di wilayah Natuna.

---

#### Jawaban Soal 15 ⭐⭐⭐

**Knowledge Base Expert System Diagnosis Radar Militer:**

**Predikat:**

| Predikat | Arti |
|----------|------|
| Gejala(r, g) | Radar r menunjukkan gejala g |
| Kerusakan(r, k) | Radar r mengalami kerusakan jenis k |
| Tindakan(r, t) | Tindakan t harus dilakukan pada radar r |

**Fakta gejala (contoh skenario):**
1. Gejala(Radar3, TidakAdaSinyal)
2. Gejala(Radar3, LayarGelap)
3. Gejala(Radar3, IndikatorMati)
4. Gejala(Radar3, TidakAdaBunyi)

**Aturan diagnosis:**
```
Aturan 1: ∀r [(Gejala(r, TidakAdaSinyal) ∧ Gejala(r, IndikatorMati))
           ⇒ Kerusakan(r, PowerSupply)]

Aturan 2: ∀r [(Gejala(r, SinyalLemah) ∧ Gejala(r, JangkauanBerkurang))
           ⇒ Kerusakan(r, Transmitter)]

Aturan 3: ∀r [(Gejala(r, GambarBerbayang) ∧ Gejala(r, NoiseEkstrem))
           ⇒ Kerusakan(r, Receiver)]

Aturan 4: ∀r [(Gejala(r, RotasiBerhenti) ∧ Gejala(r, BungiMotorAbnormal))
           ⇒ Kerusakan(r, MotorAntena)]
```

**Aturan tindakan:**
```
Aturan 5: ∀r [Kerusakan(r, PowerSupply) 
           ⇒ Tindakan(r, GantiPowerSupplyDanUjiUlang)]

Aturan 6: ∀r [Kerusakan(r, Transmitter) 
           ⇒ Tindakan(r, KirimKeDepotPemeliharaan)]
```

**Forward chaining untuk skenario Radar3:**

| Langkah | Aturan | Premis Cocok | Substitusi | Fakta Baru |
|---------|--------|--------------|------------|------------|
| 1 | Aturan 1 | Gejala(Radar3, TidakAdaSinyal) ✅ ∧ Gejala(Radar3, IndikatorMati) ✅ | {r/Radar3} | **Kerusakan(Radar3, PowerSupply)** |
| 2 | Aturan 5 | Kerusakan(Radar3, PowerSupply) ✅ | {r/Radar3} | **Tindakan(Radar3, GantiPowerSupplyDanUjiUlang)** |

**Diagnosis:** Radar3 mengalami kerusakan power supply. Tindakan: ganti power supply dan lakukan uji ulang.

---

### Bagian C: Studi Kasus

#### Studi Kasus 1: Sistem Intelijen Ancaman Maritim

**1a. Definisi Predikat (10 poin)**

| No | Predikat | Aritas | Penjelasan |
|----|----------|--------|------------|
| 1 | KapalSelam(x) | 1 | x adalah kapal selam |
| 2 | KapalPerang(x) | 1 | x adalah kapal perang |
| 3 | KapalRiset(x) | 1 | x adalah kapal riset |
| 4 | Berbendera(x, n) | 2 | Kapal x berbendera negara n |
| 5 | DiPerairan(x, p) | 2 | Kapal x terdeteksi di perairan p |
| 6 | TransponderMati(x) | 1 | Kapal x mematikan transponder AIS |
| 7 | PolaPengintaian(x) | 1 | Kapal x melakukan pola manuver pengintaian |
| 8 | KlaimTeritorial(n, p) | 2 | Negara n memiliki klaim teritorial atas perairan p |
| 9 | Kedaulatan(n, p) | 2 | Negara n memiliki kedaulatan atas perairan p |
| 10 | PangkalanTerdekat(p, b) | 2 | Pangkalan AL terdekat dari perairan p adalah b |
| 11 | PerluVerifikasi(x) | 1 | Kapal x perlu diverifikasi |
| 12 | Mencurigakan(x) | 1 | Kapal x mencurigakan |
| 13 | AncamanIntelijen(x) | 1 | Kapal x merupakan ancaman intelijen |
| 14 | SituasiSengketa(p) | 1 | Terdapat situasi sengketa di perairan p |
| 15 | TingkatAncamanTinggi(p) | 1 | Tingkat ancaman TINGGI di perairan p |
| 16 | KerahkanAset(b) | 1 | Kerahkan aset dari pangkalan b |

---

**1b. Representasi Fakta dalam FOL (15 poin)**

```
1.  KapalSelam(KapalX1) ∧ Berbendera(KapalX1, Xlandia)
2.  KapalPerang(KapalX2) ∧ Berbendera(KapalX2, Xlandia)
3.  KapalRiset(KapalY1) ∧ Berbendera(KapalY1, Ylandia)
4.  DiPerairan(KapalX1, Natuna)
5.  DiPerairan(KapalX2, Natuna)
6.  DiPerairan(KapalY1, Makassar)
7.  TransponderMati(KapalX1)
8.  PolaPengintaian(KapalX1)
9.  KlaimTeritorial(Xlandia, Natuna)
10. Kedaulatan(Indonesia, Natuna)
11. Kedaulatan(Indonesia, Makassar)
12. PangkalanTerdekat(Natuna, Jakarta)
13. PangkalanTerdekat(Makassar, Surabaya)
```

---

**1c. Representasi Aturan dalam FOL (15 poin)**

```
R1: ∀x ∀p [(¬Berbendera(x, Indonesia) ∧ DiPerairan(x, p) ∧ 
     Kedaulatan(Indonesia, p)) ⇒ PerluVerifikasi(x)]

R2: ∀x ∀p [(KapalSelam(x) ∧ ¬Berbendera(x, Indonesia) ∧ 
     TransponderMati(x) ∧ DiPerairan(x, p) ∧ 
     Kedaulatan(Indonesia, p)) ⇒ Mencurigakan(x)]

R3: ∀x [(Mencurigakan(x) ∧ PolaPengintaian(x)) ⇒ AncamanIntelijen(x)]

R4: ∀n ∀p [(KlaimTeritorial(n, p) ∧ Kedaulatan(Indonesia, p) ∧ 
     n ≠ Indonesia) ⇒ SituasiSengketa(p)]

R5: ∀x ∀p [(AncamanIntelijen(x) ∧ DiPerairan(x, p) ∧ 
     SituasiSengketa(p)) ⇒ TingkatAncamanTinggi(p)]

R6: ∀p ∀b [(TingkatAncamanTinggi(p) ∧ PangkalanTerdekat(p, b)) 
     ⇒ KerahkanAset(b)]
```

---

**1d. Forward Chaining — Tingkat Ancaman Natuna (15 poin)**

| Langkah | Aturan | Substitusi | Premis Cocok | Fakta Baru |
|---------|--------|------------|--------------|------------|
| 1 | R1 | {x/KapalX1, p/Natuna} | ¬Berbendera(KapalX1, Indonesia) ✅, DiPerairan(KapalX1, Natuna) ✅, Kedaulatan(Indonesia, Natuna) ✅ | **PerluVerifikasi(KapalX1)** |
| 2 | R1 | {x/KapalX2, p/Natuna} | Sama untuk KapalX2 ✅ | **PerluVerifikasi(KapalX2)** |
| 3 | R2 | {x/KapalX1, p/Natuna} | KapalSelam(KapalX1) ✅, ¬Berbendera(KapalX1, Indonesia) ✅, TransponderMati(KapalX1) ✅, DiPerairan(KapalX1, Natuna) ✅, Kedaulatan(Indonesia, Natuna) ✅ | **Mencurigakan(KapalX1)** |
| 4 | R3 | {x/KapalX1} | Mencurigakan(KapalX1) ✅, PolaPengintaian(KapalX1) ✅ | **AncamanIntelijen(KapalX1)** |
| 5 | R4 | {n/Xlandia, p/Natuna} | KlaimTeritorial(Xlandia, Natuna) ✅, Kedaulatan(Indonesia, Natuna) ✅, Xlandia ≠ Indonesia ✅ | **SituasiSengketa(Natuna)** |
| 6 | R5 | {x/KapalX1, p/Natuna} | AncamanIntelijen(KapalX1) ✅, DiPerairan(KapalX1, Natuna) ✅, SituasiSengketa(Natuna) ✅ | **TingkatAncamanTinggi(Natuna)** 🎯 |

**Kesimpulan:** Tingkat ancaman di perairan Natuna adalah **TINGGI** karena terdapat kapal selam asing (KapalX1) dari negara yang memiliki klaim teritorial, mematikan transponder, dan melakukan pola pengintaian.

---

**1e. Backward Chaining — KerahkanAset(Jakarta) (10 poin)**

```
Goal: KerahkanAset(Jakarta)
│
├── Cocok dengan R6: TingkatAncamanTinggi(p) ∧ PangkalanTerdekat(p, b) ⇒ KerahkanAset(b)
│   θ = {b/Jakarta}
│
├── Sub-goal 1: PangkalanTerdekat(p, Jakarta)
│   └── Fakta: PangkalanTerdekat(Natuna, Jakarta) ✅ → p = Natuna
│
└── Sub-goal 2: TingkatAncamanTinggi(Natuna)
    │
    ├── Cocok dengan R5: AncamanIntelijen(x) ∧ DiPerairan(x, Natuna) 
    │                      ∧ SituasiSengketa(Natuna) ⇒ TingkatAncamanTinggi(Natuna)
    │
    ├── Sub-goal 2.1: SituasiSengketa(Natuna)
    │   ├── Cocok R4: KlaimTeritorial(n, Natuna) ∧ Kedaulatan(Indonesia, Natuna)
    │   ├── KlaimTeritorial(Xlandia, Natuna) ✅
    │   └── Kedaulatan(Indonesia, Natuna) ✅ → TERBUKTI ✅
    │
    ├── Sub-goal 2.2: DiPerairan(x, Natuna) → coba x = KapalX1
    │   └── DiPerairan(KapalX1, Natuna) ✅
    │
    └── Sub-goal 2.3: AncamanIntelijen(KapalX1)
        ├── Cocok R3: Mencurigakan(KapalX1) ∧ PolaPengintaian(KapalX1)
        ├── PolaPengintaian(KapalX1) ✅
        └── Sub-goal 2.3.1: Mencurigakan(KapalX1)
            ├── Cocok R2: KapalSelam ∧ ¬Berbendera(Indonesia) ∧ TransponderMati ∧ ...
            ├── KapalSelam(KapalX1) ✅
            ├── TransponderMati(KapalX1) ✅
            └── Semua premis terpenuhi → TERBUKTI ✅

Semua sub-goal terbukti → KerahkanAset(Jakarta) TERBUKTI ✅
```

**Kesimpulan:** Aset dari pangkalan Jakarta harus dikerahkan karena tingkat ancaman di perairan Natuna adalah TINGGI.

---

#### Studi Kasus 2: Expert System Kesiapan Tempur Skuadron Udara

**2a. Forward Chaining — PilotSiap dan PesawatSiap (15 poin)**

**Pilot Siap (Aturan 14):** ∀p [(Pilot(p) ∧ SertifikasiTempur(p) ∧ LolosKesehatanTerbang(p)) ⇒ PilotSiap(p)]

| Pilot | Pilot(p) | SertifikasiTempur(p) | LolosKesehatanTerbang(p) | Hasil |
|-------|----------|---------------------|-------------------------|-------|
| Adi | ✅ | ✅ | ✅ | **PilotSiap(Adi)** ✅ |
| Budi | ✅ | ❌ | ✅ | Gagal — tidak punya sertifikasi |
| Citra | ✅ | ✅ | ✅ | **PilotSiap(Citra)** ✅ |

**Pilot Perlu Sertifikasi (Aturan 15):** ∀p [(Pilot(p) ∧ ¬SertifikasiTempur(p)) ⇒ PerluSertifikasi(p)]

| Pilot | Hasil |
|-------|-------|
| Budi | Pilot(Budi) ✅ ∧ ¬SertifikasiTempur(Budi) ✅ → **PerluSertifikasi(Budi)** |

**Pesawat Siap (Aturan 16):** ∀a [(Pesawat(a) ∧ StatusTeknisOK(a) ∧ BahanBakarPenuh(a)) ⇒ PesawatSiap(a)]

| Pesawat | Pesawat(a) | StatusTeknisOK(a) | BahanBakarPenuh(a) | Hasil |
|---------|------------|--------------------|--------------------|-------|
| F16_01 | ✅ | ✅ | ✅ | **PesawatSiap(F16_01)** ✅ |
| F16_02 | ✅ | ❌ | ✅ | Gagal — status teknis tidak OK |
| SU30_01 | ✅ | ✅ | ✅ | **PesawatSiap(SU30_01)** ✅ |

**Pesawat Perlu Perbaikan (Aturan 17):**

| Pesawat | Hasil |
|---------|-------|
| F16_02 | Pesawat(F16_02) ✅ ∧ ¬StatusTeknisOK(F16_02) ✅ → **PerluPerbaikan(F16_02)** |

**Pesawat Bersenjata (Aturan 18):** ∀a [∃s (Terpasang(s, a)) ⇒ Bersenjata(a)]

| Pesawat | Senjata Terpasang | Hasil |
|---------|-------------------|-------|
| F16_01 | AIM9, AIM120 | **Bersenjata(F16_01)** ✅ |
| F16_02 | (tidak ada fakta) | Tidak terbukti bersenjata |
| SU30_01 | AIM9, BombGBU | **Bersenjata(SU30_01)** ✅ |

---

**2b. Pasangan Siap Tempur (15 poin)**

**Aturan 19:** ∀p ∀a ∀sk [(PilotSiap(p) ∧ PesawatSiap(a) ∧ Bersenjata(a) ∧ DiSkuadron(p, sk) ∧ DiSkuadron(a, sk)) ⇒ PasanganSiapTempur(p, a)]

| Pilot | Pesawat | PilotSiap | PesawatSiap | Bersenjata | Skuadron Sama | Hasil |
|-------|---------|-----------|-------------|------------|---------------|-------|
| Adi | F16_01 | ✅ | ✅ | ✅ | Skuadron11 = Skuadron11 ✅ | **PasanganSiapTempur(Adi, F16_01)** ✅ |
| Adi | F16_02 | ✅ | ❌ | — | — | ❌ F16_02 tidak siap (teknis) |
| Adi | SU30_01 | ✅ | ✅ | ✅ | Skuadron11 ≠ Skuadron14 ❌ | ❌ Beda skuadron |
| Budi | F16_01 | ❌ | — | — | — | ❌ Budi tidak siap (no sertifikasi) |
| Citra | SU30_01 | ✅ | ✅ | ✅ | Skuadron14 = Skuadron14 ✅ | **PasanganSiapTempur(Citra, SU30_01)** ✅ |
| Citra | F16_01 | ✅ | ✅ | ✅ | Skuadron14 ≠ Skuadron11 ❌ | ❌ Beda skuadron |

**Pasangan yang terbentuk:**
1. **PasanganSiapTempur(Adi, F16_01)** — Skuadron 11
2. **PasanganSiapTempur(Citra, SU30_01)** — Skuadron 14

**Alasan pasangan tidak terbentuk:**
- Budi tidak bisa berpasangan karena tidak memiliki SertifikasiTempur
- F16_02 tidak bisa berpasangan karena StatusTeknisOK tidak terpenuhi
- Pasangan lintas skuadron tidak diizinkan (constraint DiSkuadron sama)

---

**2c. Backward Chaining — SkuadronOperasional(Skuadron11) (15 poin)**

```
Goal: SkuadronOperasional(Skuadron11)
│
├── Cocok dengan Aturan 20: ∃p ∃a (PasanganSiapTempur(p, a) ∧ 
│                             DiSkuadron(p, sk)) ⇒ SkuadronOperasional(sk)
│   θ = {sk/Skuadron11}
│
└── Sub-goal: ∃p ∃a [PasanganSiapTempur(p, a) ∧ DiSkuadron(p, Skuadron11)]
    │
    ├── Coba p = Adi (DiSkuadron(Adi, Skuadron11) ✅)
    │
    └── Sub-goal: PasanganSiapTempur(Adi, a) — cari a
        │
        ├── Cocok Aturan 19, coba a = F16_01
        │   θ = {p/Adi, a/F16_01, sk/Skuadron11}
        │
        ├── Sub-goal: PilotSiap(Adi)
        │   ├── Cocok Aturan 14: Pilot ∧ Sertifikasi ∧ LolosKesehatan
        │   ├── Pilot(Adi) ✅
        │   ├── SertifikasiTempur(Adi) ✅
        │   └── LolosKesehatanTerbang(Adi) ✅ → TERBUKTI ✅
        │
        ├── Sub-goal: PesawatSiap(F16_01)
        │   ├── Cocok Aturan 16: Pesawat ∧ StatusTeknisOK ∧ BahanBakarPenuh
        │   ├── Pesawat(F16_01) ✅
        │   ├── StatusTeknisOK(F16_01) ✅
        │   └── BahanBakarPenuh(F16_01) ✅ → TERBUKTI ✅
        │
        ├── Sub-goal: Bersenjata(F16_01)
        │   ├── Cocok Aturan 18: ∃s Terpasang(s, F16_01)
        │   └── Terpasang(AIM9, F16_01) ✅ → TERBUKTI ✅
        │
        └── Sub-goal: DiSkuadron(F16_01, Skuadron11)
            └── Fakta ✅ → TERBUKTI ✅

PasanganSiapTempur(Adi, F16_01) TERBUKTI ✅
→ SkuadronOperasional(Skuadron11) TERBUKTI ✅
```

---

**2d. Aturan Baru dan Forward Chaining untuk Budi (10 poin)**

**Aturan baru dalam FOL:**

```
Aturan 23: ∀p ∀n [(PerluSertifikasi(p) ∧ JamTerbang(p, n) ∧ n ≥ 500) 
           ⇒ EligibleUjian(p)]

Aturan 24: ∀p [(EligibleUjian(p) ∧ LulusUjian(p)) 
           ⇒ SertifikasiTempur(p)]
```

**Forward chaining untuk Budi:**

Dari hasil 2a, kita sudah punya: PerluSertifikasi(Budi)

| Langkah | Aturan | Premis Cocok | Substitusi | Fakta Baru |
|---------|--------|--------------|------------|------------|
| 1 | (dari 2a) | Pilot(Budi) ✅ ∧ ¬SertifikasiTempur(Budi) ✅ | {p/Budi} | PerluSertifikasi(Budi) |
| 2 | Aturan 23 | PerluSertifikasi(Budi) ✅ ∧ JamTerbang(Budi, 800) ✅ ∧ 800 ≥ 500 ✅ | {p/Budi, n/800} | **EligibleUjian(Budi)** ✅ |

**Kesimpulan:** Budi eligible untuk ujian sertifikasi karena jam terbangnya (800) melebihi threshold 500. Jika kemudian ditambahkan fakta LulusUjian(Budi), maka aturan 24 akan menghasilkan SertifikasiTempur(Budi), dan selanjutnya Budi bisa menjadi PilotSiap.

---

**2e. Aturan Eskalasi Scramble (10 poin)**

**Predikat baru:**

| Predikat | Arti |
|----------|------|
| PerintahKomando(sk, misi) | Ada perintah dari komando untuk skuadron sk dengan misi tertentu |
| SiapScramble(sk) | Skuadron sk siap melakukan scramble |
| Scramble(sk, misi) | Skuadron sk melakukan scramble untuk misi tertentu |

**Tiga aturan eskalasi:**

```
Aturan 25: ∀sk [(SkuadronOperasional(sk) ∧ ∃m PerintahKomando(sk, m)) 
           ⇒ SiapScramble(sk)]

Aturan 26: ∀sk ∀m [(SiapScramble(sk) ∧ PerintahKomando(sk, m)) 
           ⇒ Scramble(sk, m)]

Aturan 27: ∀sk ∀m ∀p ∀a [(Scramble(sk, m) ∧ PasanganSiapTempur(p, a) ∧ 
           DiSkuadron(p, sk)) ⇒ Ditugaskan(p, a, m)]
```

**Contoh forward chaining:**

Tambahkan fakta: PerintahKomando(Skuadron11, IntercepBogey)

| Langkah | Aturan | Substitusi | Fakta Baru |
|---------|--------|------------|------------|
| 1 | Aturan 25 | {sk/Skuadron11} | **SiapScramble(Skuadron11)** |
| 2 | Aturan 26 | {sk/Skuadron11, m/IntercepBogey} | **Scramble(Skuadron11, IntercepBogey)** |
| 3 | Aturan 27 | {sk/Skuadron11, m/IntercepBogey, p/Adi, a/F16_01} | **Ditugaskan(Adi, F16_01, IntercepBogey)** |

**Kesimpulan:** Pilot Adi ditugaskan dengan pesawat F16_01 untuk misi intercept bogey sebagai respons terhadap perintah komando.

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
