# Modul 09: Representasi Pengetahuan - Logika Proposisional

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 09  
**Topik:** Representasi Pengetahuan - Logika Proposisional  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan kebutuhan representasi pengetahuan formal dalam sistem AI
2. Menjelaskan sintaks dan semantik logika proposisional
3. Menggunakan konnektif logika (NOT, AND, OR, IMPLIES, IFF) untuk merepresentasikan pengetahuan
4. Mengevaluasi proposisi menggunakan tabel kebenaran
5. Menjelaskan dan membuktikan entailment dan satisfiability
6. Menerapkan aturan inferensi dasar (Modus Ponens, Modus Tollens, dll.) untuk melakukan penalaran
7. Mengonversi proposisi ke Conjunctive Normal Form (CNF) dan menerapkan algoritma resolution

---

## 1. Kebutuhan Representasi Pengetahuan Formal

### 1.1 Mengapa Representasi Pengetahuan?

Pada Pertemuan 1-6, kita telah mempelajari bagaimana agen cerdas memecahkan masalah melalui algoritma pencarian. Namun, agen yang hanya menggunakan pencarian memiliki keterbatasan: ia tidak dapat **menalar** tentang dunia secara umum. Agen memerlukan cara untuk merepresentasikan **pengetahuan** tentang dunia dan menarik **kesimpulan** baru dari pengetahuan tersebut.

> **Representasi Pengetahuan (Knowledge Representation)** adalah metode formal untuk merepresentasikan informasi tentang dunia sehingga sistem komputer dapat menggunakannya untuk memecahkan masalah kompleks, termasuk membuat keputusan dan menarik kesimpulan.

Perhatikan perbedaan berikut:

| Pendekatan | Mekanisme | Keterbatasan |
|------------|-----------|--------------|
| **Pencarian (Search)** | Eksplorasi state space | Tidak menalar tentang "mengapa" |
| **Representasi Pengetahuan** | Penalaran formal | Dapat menarik kesimpulan baru |

### 1.2 Knowledge Base dan Inference Engine

> **Knowledge Base (KB)** adalah kumpulan pernyataan (sentences) yang merepresentasikan fakta tentang dunia, ditulis dalam bahasa representasi pengetahuan.

> **Inference Engine** adalah mekanisme yang memproses knowledge base untuk menarik kesimpulan baru.

Sistem berbasis pengetahuan bekerja melalui dua operasi utama:
- **TELL**: Menambahkan informasi baru ke knowledge base
- **ASK**: Mengajukan query dan mendapatkan jawaban melalui inferensi

![Arsitektur Knowledge-Based Agent](images/p09-01-knowledge-based-agent.png)

*Gambar 9.1: Arsitektur agen berbasis pengetahuan*

#### Solved Problem 1 ⭐

**Soal:** Jelaskan perbedaan antara operasi TELL dan ASK pada knowledge-based agent!

**Penyelesaian:**

*Step 1:* Identifikasi fungsi TELL
- TELL digunakan untuk menambahkan pengetahuan baru ke KB
- Pengetahuan berasal dari percept agen atau fakta bawaan

*Step 2:* Identifikasi fungsi ASK
- ASK digunakan untuk mengajukan pertanyaan (query) ke KB
- Inference engine memproses KB untuk menghasilkan jawaban
- Jawaban dapat berupa fakta yang sudah ada atau kesimpulan baru

*Step 3:* Berikan contoh

| Operasi | Contoh |
|---------|--------|
| TELL | "Radar mendeteksi objek terbang di sektor Alpha" |
| ASK | "Apakah ada ancaman di sektor Alpha?" |

**Jawaban:** TELL menambahkan informasi baru ke knowledge base (seperti hasil sensor), sedangkan ASK mengajukan query yang dijawab melalui inferensi terhadap pengetahuan yang ada di KB. TELL bersifat *informatif* (memberitahu), ASK bersifat *interogatif* (menanyakan).

---

### 1.3 Bahasa Representasi Pengetahuan

Ada berbagai bahasa untuk merepresentasikan pengetahuan, salah satunya adalah **logika**. Modul ini membahas **logika proposisional** sebagai fondasi, sebelum melanjutkan ke logika predikat pada Pertemuan 10.

| Bahasa | Kelebihan | Kekurangan |
|--------|-----------|------------|
| **Bahasa Natural** | Ekspresif, mudah dipahami | Ambigu, sulit diproses mesin |
| **Logika Proposisional** | Formal, tidak ambigu | Ekspresivitas terbatas |
| **Logika Predikat** | Sangat ekspresif, formal | Lebih kompleks |

#### Solved Problem 2 ⭐

**Soal:** Mengapa bahasa natural tidak cocok sebagai bahasa representasi pengetahuan untuk sistem AI? Berikan contoh ambiguitas!

**Penyelesaian:**

*Step 1:* Identifikasi masalah bahasa natural
- Bahasa natural memiliki ambiguitas leksikal, sintaksis, dan semantik

*Step 2:* Berikan contoh ambiguitas

**Contoh 1 (Leksikal):** "Pesawat itu ditembak musuh dari jarak dekat."
- Apakah "pesawat" merujuk pada pesawat terbang atau pesawat telepon?

**Contoh 2 (Sintaksis):** "Tentara yang membawa senjata berat itu kelelahan."
- Apakah senjatanya yang berat, atau tentaranya yang membawa senjata dan berat badannya besar?

**Contoh 3 (Semantik):** "Semua radar bisa mendeteksi pesawat tempur."
- Apakah semua radar mendeteksi semua pesawat, atau setiap radar setidaknya bisa mendeteksi satu pesawat?

**Jawaban:** Bahasa natural tidak cocok untuk AI karena mengandung **ambiguitas** di berbagai level (leksikal, sintaksis, semantik) sehingga mesin tidak dapat memproses dan menarik kesimpulan secara pasti. Logika formal menghilangkan ambiguitas ini dengan sintaks dan semantik yang didefinisikan secara ketat.

---

## 2. Logika Proposisional: Sintaks dan Semantik

### 2.1 Simbol Proposisional

> **Proposisi** adalah pernyataan deklaratif yang bernilai benar (True) atau salah (False), tidak keduanya sekaligus.

> **Simbol Proposisional** adalah huruf yang merepresentasikan proposisi atomik, biasanya menggunakan huruf kapital seperti P, Q, R, atau nama deskriptif seperti RadarAktif, AncamanTerdeteksi.

**Contoh proposisi:**
- P = "Radar di sektor Alpha aktif" → bisa True atau False
- Q = "Objek terbang terdeteksi" → bisa True atau False
- "Berapa jarak objek?" → **bukan proposisi** (pertanyaan)
- "Aktifkan pertahanan udara!" → **bukan proposisi** (perintah)

#### Solved Problem 3 ⭐

**Soal:** Tentukan mana yang merupakan proposisi dan berikan simbol proposisionalnya!

a. "Suhu mesin pesawat melebihi 800°C"
b. "Serang target di koordinat tersebut!"
c. "Berapa ketinggian drone?"
d. "Kapal selam berada di kedalaman lebih dari 100 meter"
e. "x + 5 = 10"

**Penyelesaian:**

*Step 1:* Uji setiap pernyataan apakah bisa bernilai True/False

| Pernyataan | Proposisi? | Alasan | Simbol |
|------------|-----------|--------|--------|
| (a) | ✅ Ya | Bisa True/False | P = "Suhu mesin > 800°C" |
| (b) | ❌ Bukan | Perintah, bukan pernyataan | - |
| (c) | ❌ Bukan | Pertanyaan, bukan pernyataan | - |
| (d) | ✅ Ya | Bisa True/False | Q = "Kapal selam > 100m" |
| (e) | ✅ Ya | True jika x=5, False jika x≠5 | R = "x + 5 = 10" |

**Jawaban:** Pernyataan (a), (d), dan (e) adalah proposisi karena dapat dievaluasi kebenarannya. Pernyataan (b) adalah perintah dan (c) adalah pertanyaan, keduanya bukan proposisi.

---

### 2.2 Konnektif Logika

Proposisi atomik dapat digabungkan menggunakan **konnektif logika** untuk membentuk proposisi majemuk (compound proposition).

![Lima Konnektif Logika Proposisional](images/p09-02-logical-connectives.png)

*Gambar 9.2: Lima konnektif logika proposisional beserta simbol dan contohnya*

| Konnektif | Simbol | Nama | Contoh |
|-----------|--------|------|--------|
| **NOT** | ¬ | Negasi | ¬P ("Radar **tidak** aktif") |
| **AND** | ∧ | Konjungsi | P ∧ Q ("Radar aktif **dan** target terdeteksi") |
| **OR** | ∨ | Disjungsi | P ∨ Q ("Radar aktif **atau** sonar aktif") |
| **IMPLIES** | ⇒ | Implikasi | P ⇒ Q ("**Jika** radar aktif **maka** bisa mendeteksi") |
| **IFF** | ⇔ | Bikonditional | P ⇔ Q ("Alarm aktif **jika dan hanya jika** ancaman ada") |

**Prioritas operator** (dari tertinggi ke terendah):
1. ¬ (NOT)
2. ∧ (AND)
3. ∨ (OR)
4. ⇒ (IMPLIES)
5. ⇔ (IFF)

#### Solved Problem 4 ⭐

**Soal:** Representasikan pernyataan berikut ke dalam logika proposisional!

"Jika radar aktif dan objek terbang terdeteksi, maka alarm berbunyi."

**Penyelesaian:**

*Step 1:* Identifikasi proposisi atomik
- P = "Radar aktif"
- Q = "Objek terbang terdeteksi"
- R = "Alarm berbunyi"

*Step 2:* Identifikasi konnektif
- "dan" → ∧ (AND)
- "Jika...maka..." → ⇒ (IMPLIES)

*Step 3:* Susun formula

$$(P \wedge Q) \Rightarrow R$$

**Jawaban:** $(P \wedge Q) \Rightarrow R$ di mana P = "Radar aktif", Q = "Objek terbang terdeteksi", R = "Alarm berbunyi".

---

#### Solved Problem 5 ⭐

**Soal:** Representasikan pernyataan berikut ke dalam logika proposisional!

"Pasukan akan bergerak maju jika dan hanya jika jalur aman atau ada dukungan tembakan udara, dan tidak ada ancaman ranjau."

**Penyelesaian:**

*Step 1:* Identifikasi proposisi atomik
- M = "Pasukan bergerak maju"
- S = "Jalur aman"
- A = "Ada dukungan tembakan udara"
- R = "Ada ancaman ranjau"

*Step 2:* Analisis struktur kalimat
- "jika dan hanya jika" → ⇔
- "atau" → ∨
- "dan" → ∧
- "tidak" → ¬

*Step 3:* Perhatikan prioritas dan grouping
- "Jalur aman atau ada dukungan tembakan udara" → S ∨ A
- "tidak ada ancaman ranjau" → ¬R
- Kedua kondisi digabungkan dengan "dan" → (S ∨ A) ∧ ¬R

*Step 4:* Susun formula lengkap

$$M \Leftrightarrow ((S \vee A) \wedge \neg R)$$

**Jawaban:** $M \Leftrightarrow ((S \vee A) \wedge \neg R)$

---

### 2.3 Tabel Kebenaran

> **Tabel Kebenaran (Truth Table)** adalah tabel yang menunjukkan nilai kebenaran proposisi majemuk untuk semua kombinasi nilai kebenaran proposisi atomiknya.

**Tabel kebenaran konnektif dasar:**

| P | Q | ¬P | P ∧ Q | P ∨ Q | P ⇒ Q | P ⇔ Q |
|:-:|:-:|:--:|:-----:|:-----:|:-----:|:-----:|
| T | T | F  | T     | T     | T     | T     |
| T | F | F  | F     | T     | F     | F     |
| F | T | T  | F     | T     | T     | F     |
| F | F | T  | F     | F     | T     | T     |

**Catatan penting tentang implikasi (⇒):**
- P ⇒ Q bernilai **False hanya jika** P bernilai True dan Q bernilai False
- Jika P False, maka P ⇒ Q **selalu True** (vacuously true)
- Analogi: "Jika saya lulus ujian, saya akan mentraktir." Janji ini hanya dilanggar jika lulus tapi tidak mentraktir.

#### Solved Problem 6 ⭐

**Soal:** Buatkan tabel kebenaran untuk $(P \wedge Q) \Rightarrow R$!

**Penyelesaian:**

*Step 1:* Identifikasi variabel: P, Q, R → 2³ = 8 baris

*Step 2:* Hitung kolom antara: P ∧ Q

*Step 3:* Hitung kolom hasil: (P ∧ Q) ⇒ R

| P | Q | R | P ∧ Q | (P ∧ Q) ⇒ R |
|:-:|:-:|:-:|:-----:|:-----------:|
| T | T | T | T     | **T**       |
| T | T | F | T     | **F**       |
| T | F | T | F     | **T**       |
| T | F | F | F     | **T**       |
| F | T | T | F     | **T**       |
| F | T | F | F     | **T**       |
| F | F | T | F     | **T**       |
| F | F | F | F     | **T**       |

**Jawaban:** Formula $(P \wedge Q) \Rightarrow R$ hanya bernilai False pada satu kasus: ketika P dan Q keduanya True tetapi R False. Ini sesuai dengan makna: "Jika radar aktif DAN target terdeteksi, MAKA alarm berbunyi" — hanya dilanggar jika radar aktif dan target ada tapi alarm tidak berbunyi.

---

#### Solved Problem 7 ⭐⭐

**Soal:** Buktikan menggunakan tabel kebenaran bahwa $P \Rightarrow Q$ ekuivalen dengan $\neg P \vee Q$!

**Penyelesaian:**

*Step 1:* Buat tabel kebenaran untuk kedua formula

| P | Q | ¬P | P ⇒ Q | ¬P ∨ Q |
|:-:|:-:|:--:|:-----:|:------:|
| T | T | F  | T     | T      |
| T | F | F  | F     | F      |
| F | T | T  | T     | T      |
| F | F | T  | T     | T      |

*Step 2:* Bandingkan kolom P ⇒ Q dan ¬P ∨ Q

Kedua kolom menghasilkan nilai yang **identik** untuk semua kombinasi.

**Jawaban:** Karena P ⇒ Q dan ¬P ∨ Q memiliki nilai kebenaran yang sama untuk semua kemungkinan assignment, keduanya **ekuivalen secara logis**. Kita tulis: $P \Rightarrow Q \equiv \neg P \vee Q$. Ekuivalensi ini sangat penting dan akan digunakan saat konversi ke CNF.

---

### 2.4 Model dan Semantik

> **Model** adalah assignment (penetapan) nilai kebenaran untuk setiap simbol proposisional. Untuk n simbol, terdapat $2^n$ model yang mungkin.

> **Sebuah model $m$ memenuhi (satisfies) formula $\alpha$** jika $\alpha$ bernilai True dalam model $m$.

**Contoh:** Jika P = True, Q = False, maka model $m = \{P = T, Q = F\}$:
- $m$ memenuhi $P \vee Q$ (karena P True)
- $m$ tidak memenuhi $P \wedge Q$ (karena Q False)

#### Solved Problem 8 ⭐

**Soal:** Diberikan formula $\alpha = (P \vee Q) \wedge \neg R$. Tentukan model mana yang memenuhi $\alpha$!

a. $m_1 = \{P=T, Q=F, R=F\}$
b. $m_2 = \{P=F, Q=F, R=F\}$
c. $m_3 = \{P=T, Q=T, R=T\}$

**Penyelesaian:**

*Step 1:* Evaluasi $\alpha$ pada setiap model

**Model $m_1$: P=T, Q=F, R=F**
- P ∨ Q = T ∨ F = T
- ¬R = ¬F = T
- (P ∨ Q) ∧ ¬R = T ∧ T = **True** ✅

**Model $m_2$: P=F, Q=F, R=F**
- P ∨ Q = F ∨ F = F
- ¬R = ¬F = T
- (P ∨ Q) ∧ ¬R = F ∧ T = **False** ❌

**Model $m_3$: P=T, Q=T, R=T**
- P ∨ Q = T ∨ T = T
- ¬R = ¬T = F
- (P ∨ Q) ∧ ¬R = T ∧ F = **False** ❌

**Jawaban:** Hanya model $m_1 = \{P=T, Q=F, R=F\}$ yang memenuhi formula $\alpha$.

---

## 3. Entailment dan Satisfiability

### 3.1 Entailment (Pemenuhan Logis)

> **Entailment** ($\alpha \models \beta$): Formula $\alpha$ meng-entail formula $\beta$ jika dan hanya jika **setiap model** yang memenuhi $\alpha$ juga memenuhi $\beta$.

Secara informal: $\alpha \models \beta$ berarti "$\beta$ pasti benar kapanpun $\alpha$ benar."

**Penting:** Entailment bukan tentang "membuat" sesuatu menjadi benar, melainkan tentang hubungan logis yang **sudah ada**.

#### Solved Problem 9 ⭐

**Soal:** Buktikan bahwa $P \wedge Q \models P$!

**Penyelesaian:**

*Step 1:* Identifikasi semua model yang memenuhi $P \wedge Q$

| P | Q | P ∧ Q |
|:-:|:-:|:-----:|
| T | T | **T** ← model yang memenuhi |
| T | F | F     |
| F | T | F     |
| F | F | F     |

*Step 2:* Periksa apakah P juga True pada model tersebut

Satu-satunya model yang memenuhi $P \wedge Q$ adalah $\{P=T, Q=T\}$.
Pada model ini, P = True. ✅

*Step 3:* Kesimpulan

Karena **setiap** model yang memenuhi $P \wedge Q$ juga memenuhi P, maka $P \wedge Q \models P$.

**Jawaban:** $P \wedge Q \models P$ terbukti karena satu-satunya model yang membuat $P \wedge Q$ bernilai True adalah {P=T, Q=T}, dan pada model tersebut P bernilai True.

---

### 3.2 Satisfiability, Validity, dan Unsatisfiability

> **Satisfiable (Terpenuhi):** Formula yang bernilai True pada **setidaknya satu** model.

> **Valid (Tautologi):** Formula yang bernilai True pada **semua** model.

> **Unsatisfiable (Kontradiksi):** Formula yang bernilai False pada **semua** model.

![Hubungan Satisfiability, Validity, dan Unsatisfiability](images/p09-03-satisfiability-categories.png)

*Gambar 9.3: Kategori formula berdasarkan satisfiability*

**Hubungan penting:**
- Setiap formula valid pasti satisfiable, tetapi tidak sebaliknya
- $\alpha \models \beta$ jika dan hanya jika $\alpha \wedge \neg\beta$ adalah unsatisfiable

| Kategori | Definisi | Contoh |
|----------|----------|--------|
| **Valid** (Tautologi) | True di semua model | $P \vee \neg P$ |
| **Satisfiable** | True di minimal satu model | $P \wedge Q$ |
| **Unsatisfiable** (Kontradiksi) | False di semua model | $P \wedge \neg P$ |

#### Solved Problem 10 ⭐⭐

**Soal:** Tentukan apakah formula berikut valid, satisfiable (bukan valid), atau unsatisfiable!

a. $(P \Rightarrow Q) \Leftrightarrow (\neg P \vee Q)$
b. $P \wedge \neg P$
c. $P \Rightarrow (Q \Rightarrow P)$

**Penyelesaian:**

*Step 1:* Evaluasi formula (a)

| P | Q | P ⇒ Q | ¬P ∨ Q | (P ⇒ Q) ⇔ (¬P ∨ Q) |
|:-:|:-:|:-----:|:------:|:-------------------:|
| T | T | T     | T      | T                   |
| T | F | F     | F      | T                   |
| F | T | T     | T      | T                   |
| F | F | T     | T      | T                   |

Selalu True → **Valid (Tautologi)** ✅

*Step 2:* Evaluasi formula (b)

| P | P ∧ ¬P |
|:-:|:------:|
| T | F      |
| F | F      |

Selalu False → **Unsatisfiable (Kontradiksi)** ❌

*Step 3:* Evaluasi formula (c)

| P | Q | Q ⇒ P | P ⇒ (Q ⇒ P) |
|:-:|:-:|:-----:|:-----------:|
| T | T | T     | T           |
| T | F | T     | T           |
| F | T | F     | T           |
| F | F | T     | T           |

Selalu True → **Valid (Tautologi)** ✅

**Jawaban:** (a) Valid, (b) Unsatisfiable, (c) Valid.

---

#### Solved Problem 11 ⭐⭐

**Soal:** Gunakan metode pembuktian tidak langsung (proof by contradiction) untuk menunjukkan bahwa $\{P, P \Rightarrow Q\} \models Q$!

**Penyelesaian:**

*Step 1:* Untuk membuktikan entailment, tunjukkan bahwa $P \wedge (P \Rightarrow Q) \wedge \neg Q$ adalah unsatisfiable

*Step 2:* Buat tabel kebenaran

| P | Q | P ⇒ Q | ¬Q | P ∧ (P ⇒ Q) ∧ ¬Q |
|:-:|:-:|:-----:|:--:|:-----------------:|
| T | T | T     | F  | F                 |
| T | F | F     | T  | F                 |
| F | T | T     | F  | F                 |
| F | F | T     | T  | F                 |

*Step 3:* Analisis hasil

Formula $P \wedge (P \Rightarrow Q) \wedge \neg Q$ bernilai False di semua model → **Unsatisfiable**.

**Jawaban:** Karena $P \wedge (P \Rightarrow Q) \wedge \neg Q$ adalah unsatisfiable, maka $\{P, P \Rightarrow Q\} \models Q$ terbukti. Ini adalah fondasi dari aturan inferensi Modus Ponens.

---

## 4. Aturan Inferensi

### 4.1 Aturan Inferensi Dasar

> **Aturan Inferensi** adalah pola penalaran yang terbukti valid (sound) — jika premis benar, maka kesimpulan pasti benar.

Aturan inferensi memungkinkan kita menarik kesimpulan baru dari fakta yang sudah ada di knowledge base **tanpa perlu membuat tabel kebenaran lengkap**.

| Aturan | Premis | Kesimpulan | Notasi |
|--------|--------|------------|--------|
| **Modus Ponens** | $\alpha \Rightarrow \beta$, $\alpha$ | $\beta$ | $\frac{\alpha \Rightarrow \beta, \quad \alpha}{\beta}$ |
| **Modus Tollens** | $\alpha \Rightarrow \beta$, $\neg\beta$ | $\neg\alpha$ | $\frac{\alpha \Rightarrow \beta, \quad \neg\beta}{\neg\alpha}$ |
| **And-Elimination** | $\alpha \wedge \beta$ | $\alpha$ (atau $\beta$) | $\frac{\alpha \wedge \beta}{\alpha}$ |
| **And-Introduction** | $\alpha$, $\beta$ | $\alpha \wedge \beta$ | $\frac{\alpha, \quad \beta}{\alpha \wedge \beta}$ |
| **Or-Introduction** | $\alpha$ | $\alpha \vee \beta$ | $\frac{\alpha}{\alpha \vee \beta}$ |
| **Double Negation** | $\neg\neg\alpha$ | $\alpha$ | $\frac{\neg\neg\alpha}{\alpha}$ |
| **Hypothetical Syllogism** | $\alpha \Rightarrow \beta$, $\beta \Rightarrow \gamma$ | $\alpha \Rightarrow \gamma$ | $\frac{\alpha \Rightarrow \beta, \quad \beta \Rightarrow \gamma}{\alpha \Rightarrow \gamma}$ |

#### Solved Problem 12 ⭐

**Soal:** Diberikan KB berikut. Gunakan Modus Ponens untuk menarik kesimpulan!

- KB1: RadarAktif ⇒ DapatDeteksi
- KB2: RadarAktif

**Penyelesaian:**

*Step 1:* Identifikasi pola Modus Ponens: $\alpha \Rightarrow \beta$ dan $\alpha$

- $\alpha$ = RadarAktif
- $\beta$ = DapatDeteksi
- Premis 1: RadarAktif ⇒ DapatDeteksi ✅
- Premis 2: RadarAktif ✅

*Step 2:* Terapkan Modus Ponens

$$\frac{\text{RadarAktif} \Rightarrow \text{DapatDeteksi}, \quad \text{RadarAktif}}{\text{DapatDeteksi}}$$

**Jawaban:** Dari KB tersebut, kita dapat menyimpulkan **DapatDeteksi** (sistem dapat mendeteksi).

---

#### Solved Problem 13 ⭐⭐

**Soal:** Diberikan knowledge base:
1. HujanLebat ⇒ JalanBanjir
2. JalanBanjir ⇒ KonvoiTerhenti
3. HujanLebat

Buktikan bahwa KonvoiTerhenti!

**Penyelesaian:**

*Step 1:* Dari KB(3) HujanLebat dan KB(1) HujanLebat ⇒ JalanBanjir, gunakan **Modus Ponens**:

$$\frac{\text{HujanLebat} \Rightarrow \text{JalanBanjir}, \quad \text{HujanLebat}}{\text{JalanBanjir}}$$

Kesimpulan 1: **JalanBanjir**

*Step 2:* Dari Kesimpulan 1 (JalanBanjir) dan KB(2) JalanBanjir ⇒ KonvoiTerhenti, gunakan **Modus Ponens**:

$$\frac{\text{JalanBanjir} \Rightarrow \text{KonvoiTerhenti}, \quad \text{JalanBanjir}}{\text{KonvoiTerhenti}}$$

Kesimpulan 2: **KonvoiTerhenti**

*Alternatif:* Menggunakan **Hypothetical Syllogism** pada KB(1) dan KB(2):

$$\frac{\text{HujanLebat} \Rightarrow \text{JalanBanjir}, \quad \text{JalanBanjir} \Rightarrow \text{KonvoiTerhenti}}{\text{HujanLebat} \Rightarrow \text{KonvoiTerhenti}}$$

Kemudian Modus Ponens dengan KB(3): KonvoiTerhenti. ✅

**Jawaban:** KonvoiTerhenti terbukti melalui dua kali penerapan Modus Ponens, atau melalui Hypothetical Syllogism diikuti Modus Ponens.

---

#### Solved Problem 14 ⭐

**Soal:** Diberikan knowledge base:
1. MusuhTerdeteksi ⇒ SiagaTempur
2. ¬SiagaTempur

Apa yang dapat disimpulkan? Aturan inferensi apa yang digunakan?

**Penyelesaian:**

*Step 1:* Identifikasi pola — cocok dengan **Modus Tollens**: $\alpha \Rightarrow \beta$ dan $\neg\beta$, maka $\neg\alpha$

- $\alpha$ = MusuhTerdeteksi
- $\beta$ = SiagaTempur
- Premis 1: MusuhTerdeteksi ⇒ SiagaTempur ✅
- Premis 2: ¬SiagaTempur ✅

*Step 2:* Terapkan Modus Tollens

$$\frac{\text{MusuhTerdeteksi} \Rightarrow \text{SiagaTempur}, \quad \neg\text{SiagaTempur}}{\neg\text{MusuhTerdeteksi}}$$

**Jawaban:** Dari KB tersebut, menggunakan **Modus Tollens**, kita menyimpulkan **¬MusuhTerdeteksi** (musuh tidak terdeteksi). Logikanya: jika musuh terdeteksi pasti siaga tempur, tapi tidak siaga tempur, berarti musuh tidak terdeteksi.

---

#### Solved Problem 15 ⭐⭐

**Soal:** Diberikan knowledge base berikut, tentukan semua kesimpulan yang dapat ditarik!
1. A ∧ B
2. A ⇒ C
3. C ⇒ D

**Penyelesaian:**

*Step 1:* Dari KB(1) A ∧ B, gunakan **And-Elimination**:
- Kesimpulan 1: **A**
- Kesimpulan 2: **B**

*Step 2:* Dari Kesimpulan 1 (A) dan KB(2) A ⇒ C, gunakan **Modus Ponens**:
- Kesimpulan 3: **C**

*Step 3:* Dari Kesimpulan 3 (C) dan KB(3) C ⇒ D, gunakan **Modus Ponens**:
- Kesimpulan 4: **D**

*Step 4:* Dari Kesimpulan 3 (C) dan Kesimpulan 4 (D), gunakan **And-Introduction**:
- Kesimpulan 5: **C ∧ D**

*Step 5:* Dari Kesimpulan 1 (A), gunakan **Or-Introduction**:
- Kesimpulan 6: **A ∨ X** (untuk sembarang X)

**Jawaban:** Kesimpulan yang dapat ditarik: A, B, C, D, serta berbagai kombinasinya (C ∧ D, A ∧ C, dll.).

---

### 4.2 Ekuivalensi Logika

Beberapa ekuivalensi penting yang sering digunakan dalam manipulasi formula:

| Nama | Ekuivalensi |
|------|-------------|
| **Eliminasi Implikasi** | $\alpha \Rightarrow \beta \equiv \neg\alpha \vee \beta$ |
| **Eliminasi Bikonditional** | $\alpha \Leftrightarrow \beta \equiv (\alpha \Rightarrow \beta) \wedge (\beta \Rightarrow \alpha)$ |
| **De Morgan 1** | $\neg(\alpha \wedge \beta) \equiv \neg\alpha \vee \neg\beta$ |
| **De Morgan 2** | $\neg(\alpha \vee \beta) \equiv \neg\alpha \wedge \neg\beta$ |
| **Double Negation** | $\neg\neg\alpha \equiv \alpha$ |
| **Komutatif (AND)** | $\alpha \wedge \beta \equiv \beta \wedge \alpha$ |
| **Komutatif (OR)** | $\alpha \vee \beta \equiv \beta \vee \alpha$ |
| **Distributif** | $\alpha \vee (\beta \wedge \gamma) \equiv (\alpha \vee \beta) \wedge (\alpha \vee \gamma)$ |
| **Distributif** | $\alpha \wedge (\beta \vee \gamma) \equiv (\alpha \wedge \beta) \vee (\alpha \wedge \gamma)$ |
| **Kontrapositif** | $\alpha \Rightarrow \beta \equiv \neg\beta \Rightarrow \neg\alpha$ |

#### Solved Problem 16 ⭐⭐

**Soal:** Sederhanakan formula $\neg(P \wedge (Q \vee R))$ menggunakan hukum De Morgan!

**Penyelesaian:**

*Step 1:* Terapkan De Morgan pada ∧
$$\neg(P \wedge (Q \vee R)) \equiv \neg P \vee \neg(Q \vee R)$$

*Step 2:* Terapkan De Morgan pada ∨
$$\equiv \neg P \vee (\neg Q \wedge \neg R)$$

*Step 3:* Verifikasi (opsional) — tabel kebenaran untuk P=T, Q=T, R=F:
- Asli: ¬(T ∧ (T ∨ F)) = ¬(T ∧ T) = ¬T = F
- Hasil: ¬T ∨ (¬T ∧ ¬F) = F ∨ (F ∧ T) = F ∨ F = F ✅

**Jawaban:** $\neg(P \wedge (Q \vee R)) \equiv \neg P \vee (\neg Q \wedge \neg R)$

---

## 5. Conjunctive Normal Form (CNF)

### 5.1 Definisi CNF

> **Literal** adalah simbol proposisional (P) atau negasinya (¬P).

> **Klausa (Clause)** adalah disjungsi (OR) dari satu atau lebih literal. Contoh: $P \vee \neg Q \vee R$.

> **Conjunctive Normal Form (CNF)** adalah konjungsi (AND) dari klausa-klausa. Bentuk: $(klausa_1) \wedge (klausa_2) \wedge ... \wedge (klausa_n)$.

**Contoh CNF:**
$$(P \vee Q) \wedge (\neg P \vee R) \wedge (\neg Q \vee \neg R \vee S)$$

Setiap klausa dihubungkan dengan AND, dan di dalam klausa hanya terdapat literal yang dihubungkan dengan OR.

### 5.2 Prosedur Konversi ke CNF

Langkah konversi formula ke CNF:

1. **Eliminasi bikonditional (⇔):** $\alpha \Leftrightarrow \beta$ → $(\alpha \Rightarrow \beta) \wedge (\beta \Rightarrow \alpha)$
2. **Eliminasi implikasi (⇒):** $\alpha \Rightarrow \beta$ → $\neg\alpha \vee \beta$
3. **Pindahkan NOT ke dalam:** Gunakan De Morgan dan Double Negation
4. **Distribusikan OR ke atas AND:** $\alpha \vee (\beta \wedge \gamma)$ → $(\alpha \vee \beta) \wedge (\alpha \vee \gamma)$

![Prosedur Konversi ke CNF](images/p09-04-cnf-conversion-steps.png)

*Gambar 9.4: Empat langkah konversi formula ke Conjunctive Normal Form (CNF)*

#### Solved Problem 17 ⭐⭐

**Soal:** Konversikan formula $(P \Rightarrow Q) \Rightarrow R$ ke CNF!

**Penyelesaian:**

*Step 1:* Eliminasi implikasi luar: $\alpha \Rightarrow R$ → $\neg\alpha \vee R$
$$\neg(P \Rightarrow Q) \vee R$$

*Step 2:* Eliminasi implikasi dalam: $P \Rightarrow Q$ → $\neg P \vee Q$
$$\neg(\neg P \vee Q) \vee R$$

*Step 3:* Pindahkan NOT ke dalam menggunakan De Morgan:
$$\neg(\neg P \vee Q) \equiv \neg\neg P \wedge \neg Q \equiv P \wedge \neg Q$$

Sehingga:
$$(P \wedge \neg Q) \vee R$$

*Step 4:* Distribusikan OR atas AND:
$$(P \vee R) \wedge (\neg Q \vee R)$$

**Jawaban:** CNF dari $(P \Rightarrow Q) \Rightarrow R$ adalah $\mathbf{(P \vee R) \wedge (\neg Q \vee R)}$

---

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Konversikan formula berikut ke CNF:
$$P \Leftrightarrow (Q \vee R)$$

**Penyelesaian:**

*Step 1:* Eliminasi bikonditional
$$P \Leftrightarrow (Q \vee R) \equiv (P \Rightarrow (Q \vee R)) \wedge ((Q \vee R) \Rightarrow P)$$

*Step 2:* Eliminasi implikasi pada kedua bagian
$$(P \Rightarrow (Q \vee R)) \equiv \neg P \vee (Q \vee R) \equiv \neg P \vee Q \vee R$$

$$((Q \vee R) \Rightarrow P) \equiv \neg(Q \vee R) \vee P$$

*Step 3:* Pindahkan NOT ke dalam pada bagian kedua (De Morgan)
$$\neg(Q \vee R) \equiv \neg Q \wedge \neg R$$

Sehingga bagian kedua menjadi:
$$(\neg Q \wedge \neg R) \vee P$$

*Step 4:* Distribusikan OR atas AND pada bagian kedua
$$(\neg Q \wedge \neg R) \vee P \equiv (\neg Q \vee P) \wedge (\neg R \vee P)$$

*Step 5:* Gabungkan kedua bagian (AND)
$$(\neg P \vee Q \vee R) \wedge (\neg Q \vee P) \wedge (\neg R \vee P)$$

**Jawaban:** CNF dari $P \Leftrightarrow (Q \vee R)$ adalah:
$$\mathbf{(\neg P \vee Q \vee R) \wedge (P \vee \neg Q) \wedge (P \vee \neg R)}$$

Terdapat 3 klausa.

---

## 6. Algoritma Resolution

### 6.1 Aturan Resolution

> **Resolution** adalah aturan inferensi tunggal yang **lengkap** (complete) untuk logika proposisional — artinya, resolution saja sudah cukup untuk membuktikan setiap entailment yang valid.

**Aturan Resolution:**

$$\frac{l_1 \vee \cdots \vee l_k, \qquad m_1 \vee \cdots \vee m_n}{l_1 \vee \cdots \vee l_{i-1} \vee l_{i+1} \vee \cdots \vee l_k \vee m_1 \vee \cdots \vee m_{j-1} \vee m_{j+1} \vee \cdots \vee m_n}$$

di mana $l_i$ dan $m_j$ adalah **literal komplementer** ($l_i = \neg m_j$ atau sebaliknya).

**Secara sederhana:** Jika satu klausa mengandung $P$ dan klausa lain mengandung $\neg P$, kita dapat menghapus keduanya dan menggabungkan sisa literal.

**Contoh:**
$$\frac{P \vee Q, \qquad \neg P \vee R}{Q \vee R}$$

P dan ¬P saling menghilangkan, tersisa Q ∨ R.

### 6.2 Proof by Resolution (Refutation)

Untuk membuktikan $KB \models \alpha$:
1. Konversi KB ∧ ¬α ke CNF
2. Terapkan resolution pada pasangan klausa berulang kali
3. Jika dihasilkan **klausa kosong** (□ atau ⊥), maka $KB \models \alpha$ terbukti
4. Jika tidak ada resolusi baru yang bisa dibuat dan □ tidak ditemukan, maka entailment tidak berlaku

![Proses Resolution Refutation](images/p09-05-resolution-refutation-process.png)

*Gambar 9.5: Proses pembuktian dengan resolution refutation*

#### Solved Problem 19 ⭐⭐⭐

**Soal:** Diberikan knowledge base:
1. P ⇒ Q
2. Q ⇒ R
3. P

Buktikan bahwa KB ⊨ R menggunakan resolution!

**Penyelesaian:**

*Step 1:* Konversi KB ke CNF
- KB(1): P ⇒ Q → ¬P ∨ Q → **Klausa: {¬P, Q}**
- KB(2): Q ⇒ R → ¬Q ∨ R → **Klausa: {¬Q, R}**
- KB(3): P → **Klausa: {P}**

*Step 2:* Negasi goal: ¬R → **Klausa: {¬R}**

*Step 3:* Himpunan klausa:
1. {¬P, Q}
2. {¬Q, R}
3. {P}
4. {¬R} ← negasi goal

*Step 4:* Terapkan resolution

**Resolusi 1:** Klausa 2 {¬Q, R} dan Klausa 4 {¬R}
- Literal komplementer: R dan ¬R
- Resolvent: **{¬Q}** ← Klausa 5

**Resolusi 2:** Klausa 1 {¬P, Q} dan Klausa 5 {¬Q}
- Literal komplementer: Q dan ¬Q
- Resolvent: **{¬P}** ← Klausa 6

**Resolusi 3:** Klausa 3 {P} dan Klausa 6 {¬P}
- Literal komplementer: P dan ¬P
- Resolvent: **□ (klausa kosong)** ← KONTRADIKSI!

*Step 5:* Karena diperoleh klausa kosong, maka **KB ⊨ R terbukti**. ✅

**Jawaban:** Resolution refutation menghasilkan klausa kosong, membuktikan bahwa R adalah konsekuensi logis dari KB. Langkah: {¬Q,R} + {¬R} → {¬Q}, lalu {¬P,Q} + {¬Q} → {¬P}, lalu {P} + {¬P} → □.

---

#### Solved Problem 20 ⭐⭐⭐

**Soal:** Diberikan knowledge base untuk sistem keamanan pangkalan:
1. JendalaRusak ∨ PintuRusak → AlarmAktif
2. AlarmAktif → PenjagaDatang
3. PenjagaDatang → IntruderDitangkap
4. JendalaRusak

Buktikan bahwa IntruderDitangkap menggunakan resolution!

**Penyelesaian:**

*Step 1:* Definisikan simbol
- J = JendalaRusak, D = PintuRusak, A = AlarmAktif
- P = PenjagaDatang, I = IntruderDitangkap

*Step 2:* Konversi KB ke CNF

KB(1): $(J \vee D) \Rightarrow A$
$$\equiv \neg(J \vee D) \vee A \equiv (\neg J \wedge \neg D) \vee A$$
$$\equiv (\neg J \vee A) \wedge (\neg D \vee A)$$
→ **Klausa 1a: {¬J, A}** dan **Klausa 1b: {¬D, A}**

KB(2): $A \Rightarrow P$ → **Klausa 2: {¬A, P}**

KB(3): $P \Rightarrow I$ → **Klausa 3: {¬P, I}**

KB(4): J → **Klausa 4: {J}**

Negasi goal: ¬I → **Klausa 5: {¬I}**

*Step 3:* Terapkan resolution

| Langkah | Klausa 1 | Klausa 2 | Literal Dihapus | Resolvent |
|---------|----------|----------|-----------------|-----------|
| R1 | {¬P, I} (3) | {¬I} (5) | I, ¬I | **{¬P}** (6) |
| R2 | {¬A, P} (2) | {¬P} (6) | P, ¬P | **{¬A}** (7) |
| R3 | {¬J, A} (1a) | {¬A} (7) | A, ¬A | **{¬J}** (8) |
| R4 | {J} (4) | {¬J} (8) | J, ¬J | **□** |

*Step 4:* Klausa kosong diperoleh → **KB ⊨ IntruderDitangkap** terbukti. ✅

**Jawaban:** Melalui 4 langkah resolution, dibuktikan bahwa IntruderDitangkap adalah konsekuensi logis dari KB. Inferensi chain: JendalaRusak → AlarmAktif → PenjagaDatang → IntruderDitangkap.

---

## 7. Wumpus World: Studi Kasus Representasi Pengetahuan

### 7.1 Deskripsi Wumpus World

> **Wumpus World** adalah lingkungan klasik dalam AI yang digunakan untuk mengilustrasikan penalaran logis. Agen harus menavigasi gua untuk menemukan emas sambil menghindari jebakan (pit) dan monster Wumpus.

**Aturan Wumpus World:**
- Grid 4×4 dengan posisi-posisi yang mungkin berisi Wumpus, pit, atau emas
- Agen merasakan **Breeze** di sel yang bersebelahan dengan pit
- Agen merasakan **Stench** di sel yang bersebelahan dengan Wumpus
- Agen merasakan **Glitter** di sel yang mengandung emas

![Ilustrasi Wumpus World](images/p09-06-wumpus-world-grid.png)

*Gambar 9.6: Contoh konfigurasi Wumpus World 4×4*

### 7.2 Representasi dalam Logika Proposisional

Kita dapat merepresentasikan pengetahuan tentang Wumpus World menggunakan simbol proposisional:

| Simbol | Makna |
|--------|-------|
| $P_{i,j}$ | Ada pit di sel [i,j] |
| $W_{i,j}$ | Ada Wumpus di sel [i,j] |
| $B_{i,j}$ | Ada breeze di sel [i,j] |
| $S_{i,j}$ | Ada stench di sel [i,j] |

**Contoh aturan (knowledge base):**
- "Ada breeze di [1,1] jika dan hanya jika ada pit di [1,2] atau pit di [2,1]":

$$B_{1,1} \Leftrightarrow (P_{1,2} \vee P_{2,1})$$

- "Tidak ada pit di [1,1]" (tempat awal agen):

$$\neg P_{1,1}$$

#### Solved Problem 21 ⭐⭐

**Soal:** Agen berada di [1,1] dan merasakan NO breeze. Kemudian pindah ke [2,1] dan merasakan breeze. Apa yang dapat disimpulkan tentang keberadaan pit?

**Penyelesaian:**

*Step 1:* Tuliskan knowledge base

**Aturan lingkungan:**
- $B_{1,1} \Leftrightarrow (P_{1,2} \vee P_{2,1})$ — breeze di [1,1] iff pit di tetangga
- $B_{2,1} \Leftrightarrow (P_{1,1} \vee P_{2,2} \vee P_{3,1})$ — breeze di [2,1] iff pit di tetangga

**Percept (fakta):**
- $\neg B_{1,1}$ — tidak ada breeze di [1,1]
- $B_{2,1}$ — ada breeze di [2,1]
- $\neg P_{1,1}$ — tidak ada pit di start

*Step 2:* Inferensi dari ¬B₁,₁

Dari $B_{1,1} \Leftrightarrow (P_{1,2} \vee P_{2,1})$ dan $\neg B_{1,1}$:
$$\neg(P_{1,2} \vee P_{2,1}) \equiv \neg P_{1,2} \wedge \neg P_{2,1}$$

Kesimpulan: **¬P₁,₂** dan **¬P₂,₁** (tidak ada pit di [1,2] dan [2,1])

*Step 3:* Inferensi dari B₂,₁

Dari $B_{2,1} \Leftrightarrow (P_{1,1} \vee P_{2,2} \vee P_{3,1})$ dan $B_{2,1}$:
$$(P_{1,1} \vee P_{2,2} \vee P_{3,1})$$

Kita tahu $\neg P_{1,1}$, sehingga:
$$P_{2,2} \vee P_{3,1}$$

**Jawaban:** Dari percept, kita menyimpulkan:
- **Pasti tidak ada** pit di [1,2] dan [2,1]
- **Ada pit** di [2,2] **atau** [3,1] (atau keduanya), tapi kita belum tahu yang mana

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Lanjutkan Solved Problem 21. Setelah itu, agen pindah ke [1,2] dan merasakan NO breeze. Apakah sekarang kita bisa menentukan lokasi pit secara pasti?

**Penyelesaian:**

*Step 1:* Tambahkan pengetahuan baru ke KB

Percept baru: $\neg B_{1,2}$ — tidak ada breeze di [1,2]

Aturan: $B_{1,2} \Leftrightarrow (P_{1,1} \vee P_{1,3} \vee P_{2,2})$

*Step 2:* Inferensi dari ¬B₁,₂

Dari $\neg B_{1,2}$:
$$\neg(P_{1,1} \vee P_{1,3} \vee P_{2,2}) \equiv \neg P_{1,1} \wedge \neg P_{1,3} \wedge \neg P_{2,2}$$

Kesimpulan baru: **¬P₂,₂** (tidak ada pit di [2,2])

*Step 3:* Kombinasikan dengan pengetahuan sebelumnya

Dari SP21 kita tahu: $P_{2,2} \vee P_{3,1}$
Sekarang kita tahu: $\neg P_{2,2}$

Menggunakan resolution: {P₂,₂, P₃,₁} dan {¬P₂,₂}:
$$\frac{P_{2,2} \vee P_{3,1}, \qquad \neg P_{2,2}}{P_{3,1}}$$

**Jawaban:** **Ya!** Sekarang kita dapat menyimpulkan secara pasti bahwa **ada pit di [3,1]**. Informasi dari tiga percept dikombinasikan melalui inferensi logis untuk menghasilkan kesimpulan definitif. Ini menunjukkan kekuatan penalaran logis dalam menggabungkan informasi parsial.

---

## 8. Aplikasi dalam Konteks Pertahanan

### 8.1 Knowledge Base untuk Sistem Pertahanan

Logika proposisional dapat digunakan untuk merepresentasikan aturan dalam sistem pertahanan. Meskipun untuk sistem nyata biasanya digunakan logika predikat (akan dibahas pada Pertemuan 10) atau metode probabilistik (Pertemuan 11-12), logika proposisional memberikan fondasi penting.

**Contoh KB Sistem Identifikasi Ancaman Udara:**

| No | Aturan |
|----|--------|
| 1 | $\text{RadarDeteksi} \wedge \neg\text{TransponderAktif} \Rightarrow \text{ObjekTakDikenal}$ |
| 2 | $\text{ObjekTakDikenal} \wedge \text{KecepatanTinggi} \Rightarrow \text{AncamanPotensial}$ |
| 3 | $\text{AncamanPotensial} \Rightarrow \text{AlertKomandan}$ |
| 4 | $\text{AlertKomandan} \wedge \text{KonfirmasiMusuh} \Rightarrow \text{SiagaTempur}$ |
| 5 | $\text{SiagaTempur} \Rightarrow \text{AktifkanSAM} \vee \text{ScrambleInterceptor}$ |

## Supplementary Problems

### Problem S1 ⭐

**Soal:** Dari KB di atas, jika diketahui RadarDeteksi = True, TransponderAktif = False, dan KecepatanTinggi = True, apa yang dapat disimpulkan?

**Jawaban:** Dari aturan 1, karena RadarDeteksi ∧ ¬TransponderAktif, disimpulkan ObjekTakDikenal. Dari aturan 2, karena ObjekTakDikenal ∧ KecepatanTinggi, disimpulkan AncamanPotensial. Dari aturan 3, disimpulkan AlertKomandan. Tanpa informasi KonfirmasiMusuh, aturan 4 belum bisa diterapkan.

---

---

### Problem S2 ⭐⭐

**Soal:** Buktikan dengan tabel kebenaran bahwa $(P \Rightarrow Q) \equiv (\neg Q \Rightarrow \neg P)$ (kontrapositif).

**Jawaban:**

| P | Q | P ⇒ Q | ¬Q | ¬P | ¬Q ⇒ ¬P |
|:-:|:-:|:-----:|:--:|:--:|:-------:|
| T | T | T     | F  | F  | T       |
| T | F | F     | T  | F  | F       |
| F | T | T     | F  | T  | T       |
| F | F | T     | T  | T  | T       |

Kolom P ⇒ Q dan ¬Q ⇒ ¬P identik, sehingga terbukti ekuivalen.

---

### Problem S3 ⭐⭐

**Soal:** Konversikan formula $(P \wedge Q) \Rightarrow (R \vee S)$ ke CNF!

**Jawaban:**
1. Eliminasi ⇒: $\neg(P \wedge Q) \vee (R \vee S)$
2. De Morgan: $(\neg P \vee \neg Q) \vee (R \vee S)$
3. Flatten: $\neg P \vee \neg Q \vee R \vee S$

CNF: **{¬P, ¬Q, R, S}** — satu klausa.

---

### Problem S4 ⭐⭐⭐

**Soal:** Diberikan KB:
1. A ⇒ (B ∧ C)
2. B ⇒ D
3. C ⇒ E
4. A

Gunakan resolution untuk membuktikan KB ⊨ D ∧ E!

**Jawaban:**
Konversi ke CNF:
- KB(1): {¬A, B} dan {¬A, C}
- KB(2): {¬B, D}
- KB(3): {¬C, E}
- KB(4): {A}
- Negasi goal: ¬(D ∧ E) = ¬D ∨ ¬E → {¬D, ¬E}

Resolution:
- {A} + {¬A, B} → {B}
- {A} + {¬A, C} → {C}
- {B} + {¬B, D} → {D}
- {C} + {¬C, E} → {E}
- {D} + {¬D, ¬E} → {¬E}
- {E} + {¬E} → □

Terbukti KB ⊨ D ∧ E.

---

### Problem S5 ⭐⭐⭐

**Soal:** Sebuah sistem deteksi intrusi jaringan memiliki aturan: "Jika ada traffic anomali DAN port terbuka, maka ada potensi serangan. Jika ada potensi serangan DAN bukan false positive, maka kirim alert." Representasikan dalam logika proposisional dan buktikan bahwa jika traffic anomali, port terbuka, dan bukan false positive, maka alert dikirim!

**Jawaban:**
Simbol: T = TrafficAnomali, O = PortTerbuka, S = PotensiSerangan, F = FalsePositive, A = KirimAlert

KB:
1. (T ∧ O) ⇒ S → CNF: {¬T, S}, {¬O, S} — Perhatian: ini salah, yang benar: {¬T, ¬O, S}... Koreksi:
   - (T ∧ O) ⇒ S → ¬(T ∧ O) ∨ S → ¬T ∨ ¬O ∨ S → **{¬T, ¬O, S}**
2. (S ∧ ¬F) ⇒ A → ¬S ∨ F ∨ A → **{¬S, F, A}**
3. T → **{T}**
4. O → **{O}**
5. ¬F → **{¬F}**
6. Negasi goal: ¬A → **{¬A}**

Resolution:
- {¬T, ¬O, S} + {T} → {¬O, S}
- {¬O, S} + {O} → {S}
- {¬S, F, A} + {S} → {F, A}
- {F, A} + {¬F} → {A}
- {A} + {¬A} → □

Terbukti: alert dikirim.

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Knowledge Base** | Kumpulan pernyataan formal tentang dunia |
| **Inference Engine** | Mekanisme untuk menarik kesimpulan dari KB |
| **Proposisi** | Pernyataan yang bernilai True atau False |
| **Konnektif Logika** | ¬ (NOT), ∧ (AND), ∨ (OR), ⇒ (IMPLIES), ⇔ (IFF) |
| **Tabel Kebenaran** | Evaluasi formula untuk semua kombinasi nilai |
| **Entailment** | KB ⊨ α: setiap model yang memenuhi KB juga memenuhi α |
| **Valid (Tautologi)** | True di semua model |
| **Satisfiable** | True di setidaknya satu model |
| **Unsatisfiable** | False di semua model |
| **Modus Ponens** | Dari α ⇒ β dan α, simpulkan β |
| **Modus Tollens** | Dari α ⇒ β dan ¬β, simpulkan ¬α |
| **CNF** | Konjungsi (AND) dari klausa (disjungsi/OR dari literal) |
| **Resolution** | Aturan inferensi yang lengkap — eliminasi literal komplementer |
| **Resolution Refutation** | Buktikan KB ⊨ α dengan menunjukkan KB ∧ ¬α unsatisfiable |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 7**.
2. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press. **Chapter 5**.
3. CS188 Berkeley AI Materials: [https://inst.eecs.berkeley.edu/~cs188/](https://inst.eecs.berkeley.edu/~cs188/)

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
