# Modul 10: Representasi Pengetahuan - Logika Predikat (First-Order Logic)

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 10  
**Topik:** Representasi Pengetahuan - Logika Predikat (First-Order Logic)  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan keterbatasan logika proposisional dan kebutuhan logika predikat
2. Memahami sintaks first-order logic: konstanta, variabel, predikat, fungsi, dan kuantor
3. Merepresentasikan pengetahuan dunia nyata dalam logika predikat
4. Menerapkan kuantor universal (∀) dan eksistensial (∃) dengan benar
5. Melakukan proses unifikasi dan menemukan Most General Unifier (MGU)
6. Menjelaskan dan menerapkan forward chaining dan backward chaining
7. Mengidentifikasi aplikasi logika predikat dalam expert systems dan knowledge graphs

---

## 1. Keterbatasan Logika Proposisional

### 1.1 Mengapa Logika Proposisional Tidak Cukup?

Pada Pertemuan 9, kita telah mempelajari logika proposisional sebagai alat representasi pengetahuan. Meskipun berguna, logika proposisional memiliki keterbatasan fundamental yang membuatnya tidak memadai untuk banyak domain pengetahuan.

> **Keterbatasan utama logika proposisional** adalah ketidakmampuannya untuk merepresentasikan objek individual, properti objek, dan hubungan antar objek secara umum (general).

Perhatikan contoh berikut:

| Pernyataan | Logika Proposisional | Masalah |
|------------|---------------------|---------|
| "Semua tentara harus berani" | Perlu satu proposisi per tentara | Tidak scalable |
| "Ada kapal selam di perairan Natuna" | P = "Ada kapal selam..." | Tidak bisa menanyakan *kapal selam mana* |
| "Jika seseorang adalah perwira, maka dia memimpin pasukan" | Perlu rule per individu | Tidak bisa generalisasi |

**Tiga masalah utama:**

1. **Tidak ada objek individual:** Logika proposisional tidak dapat merujuk pada objek spesifik (misalnya, "Drone Alpha-7")
2. **Tidak ada properti dan relasi:** Tidak dapat menyatakan "X adalah drone" atau "X lebih cepat dari Y"
3. **Tidak ada kuantifikasi:** Tidak dapat menyatakan "semua" atau "ada" secara umum

### 1.2 Dari Proposisional ke Predikat

> **Logika Predikat (First-Order Logic/FOL)** adalah perluasan logika proposisional yang menambahkan kemampuan untuk merepresentasikan objek, properti, relasi, dan kuantifikasi.

| Aspek | Logika Proposisional | Logika Predikat (FOL) |
|-------|---------------------|-----------------------|
| Unit dasar | Proposisi (P, Q, R) | Term, predikat, kuantor |
| Objek | Tidak ada | Konstanta, variabel |
| Properti | Tidak ada | Predikat unary: `Brave(x)` |
| Relasi | Tidak ada | Predikat n-ary: `CommandedBy(x, y)` |
| Generalisasi | Tidak bisa | ∀x, ∃x |
| Ekspresivitas | Terbatas | Jauh lebih ekspresif |

#### Solved Problem 1 ⭐

**Soal:** Representasikan pernyataan "Semua pilot TNI AU harus terampil menerbangkan pesawat" dalam logika proposisional dan logika predikat. Bandingkan hasilnya!

**Penyelesaian:**

*Step 1:* Representasi dalam logika proposisional

Misalkan ada 3 pilot: Adi, Budi, Citra.
- P₁ = "Adi adalah pilot TNI AU"
- Q₁ = "Adi terampil menerbangkan pesawat"
- P₂ = "Budi adalah pilot TNI AU"
- Q₂ = "Budi terampil menerbangkan pesawat"
- P₃ = "Citra adalah pilot TNI AU"
- Q₃ = "Citra terampil menerbangkan pesawat"

Kalimat: (P₁ ⇒ Q₁) ∧ (P₂ ⇒ Q₂) ∧ (P₃ ⇒ Q₃)

*Step 2:* Representasi dalam logika predikat

$$\forall x \, [\text{PilotTNIAU}(x) \Rightarrow \text{Terampil}(x, \text{Pesawat})]$$

*Step 3:* Perbandingan

| Aspek | Proposisional | Predikat |
|-------|---------------|----------|
| Jumlah simbol | 6 proposisi | 1 kalimat universal |
| Scalability | Perlu tambah untuk pilot baru | Otomatis berlaku untuk semua |
| Kejelasan | Kurang jelas | Sangat jelas |

**Jawaban:** Logika predikat jauh lebih ringkas dan scalable. Satu kalimat FOL merepresentasikan apa yang memerlukan banyak proposisi terpisah, dan otomatis berlaku untuk semua pilot yang ada maupun yang akan datang.

---

## 2. Sintaks First-Order Logic

### 2.1 Elemen Dasar FOL

> **Sintaks FOL** terdiri dari simbol-simbol yang digunakan untuk membangun kalimat (sentence) yang merepresentasikan pengetahuan.

![Elemen Sintaks FOL](images/p10-01-fol-syntax-elements.png)

*Gambar 10.1: Elemen-elemen sintaks First-Order Logic*

**Elemen-elemen sintaks FOL:**

| Elemen | Deskripsi | Contoh |
|--------|-----------|--------|
| **Konstanta** | Merujuk pada objek tertentu | `Adi`, `Jakarta`, `DroneAlpha7` |
| **Variabel** | Merujuk pada objek yang belum ditentukan | `x`, `y`, `z` |
| **Predikat** | Menyatakan properti atau relasi | `Pilot(x)`, `LebihCepat(x,y)` |
| **Fungsi** | Memetakan objek ke objek lain | `ayahDari(x)`, `komandanDari(y)` |
| **Konnektif** | Penghubung logika | ∧, ∨, ¬, ⇒, ⇔ |
| **Kuantor** | Kuantifikasi variabel | ∀ (untuk semua), ∃ (ada) |
| **Equality** | Menyatakan kesamaan objek | = |

### 2.2 Term

> **Term** adalah ekspresi yang merujuk pada objek. Term dapat berupa konstanta, variabel, atau fungsi yang diterapkan pada term.

**Definisi rekursif term:**
1. Setiap **konstanta** adalah term
2. Setiap **variabel** adalah term
3. Jika $f$ adalah fungsi n-ary dan $t_1, ..., t_n$ adalah term, maka $f(t_1, ..., t_n)$ adalah term

**Contoh term:**
- `Adi` (konstanta)
- `x` (variabel)
- `komandanDari(Adi)` (fungsi diterapkan pada konstanta)
- `markasBesar(komandanDari(x))` (fungsi bersarang)

#### Solved Problem 2 ⭐

**Soal:** Identifikasi semua term dalam kalimat FOL berikut: `LebihTinggi(pangkatDari(Adi), pangkatDari(Budi))`

**Penyelesaian:**

*Step 1:* Identifikasi konstanta
- `Adi` → term (konstanta)
- `Budi` → term (konstanta)

*Step 2:* Identifikasi fungsi yang diterapkan
- `pangkatDari(Adi)` → term (fungsi pada konstanta)
- `pangkatDari(Budi)` → term (fungsi pada konstanta)

*Step 3:* Identifikasi predikat (bukan term)
- `LebihTinggi(...)` → ini adalah **predikat** (bukan term)

**Jawaban:** Term dalam kalimat tersebut adalah: `Adi`, `Budi`, `pangkatDari(Adi)`, dan `pangkatDari(Budi)`. `LebihTinggi` adalah predikat, bukan term.

---

### 2.3 Kalimat Atomik (Atomic Sentence)

> **Kalimat atomik** dalam FOL terbentuk dari predikat yang diterapkan pada term, atau pernyataan kesamaan (equality) antara dua term.

**Bentuk:**
- $\text{Predicate}(t_1, t_2, ..., t_n)$ dimana $t_i$ adalah term
- $t_1 = t_2$ (equality)

**Contoh:**
- `Pilot(Adi)` — "Adi adalah pilot"
- `MenembakKe(DroneAlpha, TargetBravo)` — "Drone Alpha menembak ke Target Bravo"
- `komandanDari(Adi) = Budi` — "Komandan dari Adi adalah Budi"

### 2.4 Kalimat Kompleks (Complex Sentence)

Kalimat atomik dapat dikombinasikan menggunakan konnektif logika (sama seperti logika proposisional):

| Konnektif | Simbol | Contoh FOL |
|-----------|--------|------------|
| Negasi | ¬ | ¬Musuh(Indonesia, Malaysia) |
| Konjungsi | ∧ | Pilot(Adi) ∧ Berani(Adi) |
| Disjungsi | ∨ | DiDarat(x) ∨ DiLaut(x) |
| Implikasi | ⇒ | Pilot(x) ⇒ Terlatih(x) |
| Bikonditional | ⇔ | Perwira(x) ⇔ Pangkat(x, Letnan) ∨ Pangkat(x, Kapten) |

#### Solved Problem 3 ⭐

**Soal:** Terjemahkan kalimat berikut ke dalam FOL: "Adi adalah pilot dan Adi ditempatkan di Madiun"

**Penyelesaian:**

*Step 1:* Identifikasi predikat yang diperlukan
- `Pilot(x)` — x adalah pilot
- `Ditempatkan(x, y)` — x ditempatkan di y

*Step 2:* Identifikasi konstanta
- `Adi` — individu bernama Adi
- `Madiun` — lokasi Madiun

*Step 3:* Bangun kalimat FOL

$$\text{Pilot}(\text{Adi}) \wedge \text{Ditempatkan}(\text{Adi}, \text{Madiun})$$

**Jawaban:** `Pilot(Adi) ∧ Ditempatkan(Adi, Madiun)`

---

## 3. Kuantor (Quantifiers)

### 3.1 Kuantor Universal (∀)

> **Kuantor universal (∀)** menyatakan bahwa suatu properti berlaku untuk **semua** objek dalam domain.

**Sintaks:** $\forall x \, P(x)$

Dibaca: "Untuk semua x, P(x) berlaku"

**Contoh:**
- $\forall x \, [\text{Tentara}(x) \Rightarrow \text{Berani}(x)]$ — "Semua tentara berani"
- $\forall x \, [\text{Drone}(x) \Rightarrow \text{PunyaSensor}(x)]$ — "Semua drone memiliki sensor"

> **Pola umum kuantor universal:**
> $$\forall x \, [\text{Kategori}(x) \Rightarrow \text{Properti}(x)]$$
> Biasanya digunakan dengan implikasi (⇒), **bukan** konjungsi (∧).

**Peringatan — Kesalahan umum:**

| Kalimat | Benar/Salah | Penjelasan |
|---------|-------------|------------|
| ∀x [Tentara(x) ⇒ Berani(x)] | ✅ Benar | "Jika x tentara, maka x berani" |
| ∀x [Tentara(x) ∧ Berani(x)] | ❌ Salah | "Semua objek di dunia adalah tentara DAN berani" |

#### Solved Problem 4 ⭐

**Soal:** Representasikan "Semua pesawat tempur di Skuadron 11 dilengkapi rudal" dalam FOL!

**Penyelesaian:**

*Step 1:* Tentukan predikat
- `PesawatTempur(x)` — x adalah pesawat tempur
- `DiSkuadron(x, s)` — x berada di skuadron s
- `Dilengkapi(x, y)` — x dilengkapi dengan y

*Step 2:* Tentukan konstanta
- `Skuadron11` — Skuadron 11
- `Rudal` — rudal

*Step 3:* Bangun kalimat FOL

$$\forall x \, [(\text{PesawatTempur}(x) \wedge \text{DiSkuadron}(x, \text{Skuadron11})) \Rightarrow \text{Dilengkapi}(x, \text{Rudal})]$$

**Jawaban:** ∀x [(PesawatTempur(x) ∧ DiSkuadron(x, Skuadron11)) ⇒ Dilengkapi(x, Rudal)]

---

### 3.2 Kuantor Eksistensial (∃)

> **Kuantor eksistensial (∃)** menyatakan bahwa terdapat **setidaknya satu** objek dalam domain yang memenuhi properti tertentu.

**Sintaks:** $\exists x \, P(x)$

Dibaca: "Ada x sedemikian sehingga P(x) berlaku"

**Contoh:**
- $\exists x \, [\text{KapalSelam}(x) \wedge \text{DiPerairan}(x, \text{Natuna})]$ — "Ada kapal selam di perairan Natuna"
- $\exists x \, [\text{Mata\text{-}mata}(x) \wedge \text{Tertangkap}(x)]$ — "Ada mata-mata yang tertangkap"

> **Pola umum kuantor eksistensial:**
> $$\exists x \, [\text{Kategori}(x) \wedge \text{Properti}(x)]$$
> Biasanya digunakan dengan konjungsi (∧), **bukan** implikasi (⇒).

**Peringatan — Kesalahan umum:**

| Kalimat | Benar/Salah | Penjelasan |
|---------|-------------|------------|
| ∃x [KapalSelam(x) ∧ DiNatuna(x)] | ✅ Benar | "Ada objek yang kapal selam DAN di Natuna" |
| ∃x [KapalSelam(x) ⇒ DiNatuna(x)] | ❌ Misleading | Terpenuhi oleh objek apapun yang bukan kapal selam |

#### Solved Problem 5 ⭐

**Soal:** Representasikan "Ada drone yang lebih cepat dari semua helikopter" dalam FOL!

**Penyelesaian:**

*Step 1:* Tentukan predikat
- `Drone(x)` — x adalah drone
- `Helikopter(y)` — y adalah helikopter
- `LebihCepat(x, y)` — x lebih cepat dari y

*Step 2:* Analisis struktur kalimat
- "Ada drone" → kuantor eksistensial pada x
- "semua helikopter" → kuantor universal pada y
- Hubungan: drone tersebut lebih cepat dari setiap helikopter

*Step 3:* Bangun kalimat FOL

$$\exists x \, [\text{Drone}(x) \wedge \forall y \, [\text{Helikopter}(y) \Rightarrow \text{LebihCepat}(x, y)]]$$

**Jawaban:** ∃x [Drone(x) ∧ ∀y [Helikopter(y) ⇒ LebihCepat(x, y)]]

---

### 3.3 Kuantor Bersarang (Nested Quantifiers)

Kuantor dapat disarangkan untuk membuat pernyataan yang lebih kompleks. **Urutan kuantor sangat penting!**

| Kalimat FOL | Arti |
|-------------|------|
| ∀x ∀y Suka(x,y) | Semua orang menyukai semua orang |
| ∃x ∃y Suka(x,y) | Ada seseorang yang menyukai seseorang |
| ∀x ∃y Suka(x,y) | Setiap orang menyukai setidaknya satu orang |
| ∃x ∀y Suka(x,y) | Ada seseorang yang menyukai semua orang |
| ∀y ∃x Suka(x,y) | Setiap orang disukai oleh setidaknya satu orang |

> **Penting:** ∀x ∃y **tidak sama dengan** ∃y ∀x ketika predikat yang sama digunakan. Pada ∀x ∃y, y bisa berbeda untuk setiap x. Pada ∃y ∀x, y yang sama berlaku untuk semua x.

#### Solved Problem 6 ⭐⭐

**Soal:** Terjemahkan dan bandingkan dua kalimat berikut:
- (a) "Setiap batalion memiliki setidaknya satu komandan"
- (b) "Ada satu komandan yang memimpin semua batalion"

**Penyelesaian:**

*Step 1:* Tentukan predikat
- `Batalion(x)` — x adalah batalion
- `Komandan(y)` — y adalah komandan
- `Memimpin(y, x)` — y memimpin x

*Step 2:* Representasikan kalimat (a)

"Setiap batalion memiliki setidaknya satu komandan"
- Untuk setiap batalion, ada (setidaknya satu) komandan yang memimpinnya.

$$\forall x \, [\text{Batalion}(x) \Rightarrow \exists y \, [\text{Komandan}(y) \wedge \text{Memimpin}(y, x)]]$$

*Step 3:* Representasikan kalimat (b)

"Ada satu komandan yang memimpin semua batalion"
- Ada satu y (komandan) sedemikian sehingga untuk semua x (batalion), y memimpin x.

$$\exists y \, [\text{Komandan}(y) \wedge \forall x \, [\text{Batalion}(x) \Rightarrow \text{Memimpin}(y, x)]]$$

*Step 4:* Bandingkan

| Aspek | Kalimat (a) | Kalimat (b) |
|-------|-------------|-------------|
| Kuantor luar | ∀x (setiap batalion) | ∃y (ada satu komandan) |
| Kuantor dalam | ∃y (ada komandan) | ∀x (semua batalion) |
| Arti | Komandan bisa berbeda per batalion | Satu komandan untuk semua |
| Kalimat (b) ⇒ (a)? | Ya | — |
| Kalimat (a) ⇒ (b)? | — | Tidak selalu |

**Jawaban:** (a) ∀x [Batalion(x) ⇒ ∃y [Komandan(y) ∧ Memimpin(y, x)]], (b) ∃y [Komandan(y) ∧ ∀x [Batalion(x) ⇒ Memimpin(y, x)]]. Kalimat (b) lebih kuat karena menyatakan satu individu yang sama memimpin semua batalion, sedangkan (a) mengizinkan komandan berbeda untuk setiap batalion.

---

### 3.4 Hubungan Antar Kuantor

Kuantor universal dan eksistensial saling terhubung melalui negasi:

$$\forall x \, P(x) \equiv \neg \exists x \, \neg P(x)$$

$$\exists x \, P(x) \equiv \neg \forall x \, \neg P(x)$$

| Kalimat | Ekuivalen | Arti |
|---------|-----------|------|
| ∀x Suka(x, Nasi) | ¬∃x ¬Suka(x, Nasi) | Tidak ada yang tidak suka nasi |
| ∃x Berani(x) | ¬∀x ¬Berani(x) | Tidak benar bahwa semua tidak berani |
| ¬∀x Lulus(x) | ∃x ¬Lulus(x) | Ada yang tidak lulus |
| ¬∃x Sempurna(x) | ∀x ¬Sempurna(x) | Semua tidak sempurna |

#### Solved Problem 7 ⭐

**Soal:** Nyatakan negasi dari "Semua radar berfungsi normal" dalam FOL, lalu sederhanakan!

**Penyelesaian:**

*Step 1:* Kalimat asli
$$\forall x \, [\text{Radar}(x) \Rightarrow \text{Normal}(x)]$$

*Step 2:* Negasi
$$\neg \forall x \, [\text{Radar}(x) \Rightarrow \text{Normal}(x)]$$

*Step 3:* Sederhanakan menggunakan equivalensi
$$\exists x \, \neg [\text{Radar}(x) \Rightarrow \text{Normal}(x)]$$

*Step 4:* Ingat bahwa ¬(P ⇒ Q) ≡ P ∧ ¬Q
$$\exists x \, [\text{Radar}(x) \wedge \neg \text{Normal}(x)]$$

**Jawaban:** ∃x [Radar(x) ∧ ¬Normal(x)] — "Ada radar yang tidak berfungsi normal"

---

## 4. Semantik FOL

### 4.1 Interpretasi

> **Interpretasi** dalam FOL menentukan makna dari simbol-simbol dalam suatu domain tertentu. Interpretasi terdiri dari domain objek, pemetaan konstanta ke objek, pemetaan predikat ke relasi, dan pemetaan fungsi ke fungsi atas domain.

**Komponen interpretasi:**

| Komponen | Deskripsi | Contoh |
|----------|-----------|--------|
| **Domain (D)** | Himpunan objek | {Adi, Budi, Citra, F-16A, F-16B} |
| **Pemetaan konstanta** | Konstanta → objek di D | Adi → individu Adi |
| **Pemetaan predikat** | Predikat → relasi di D | Pilot → {Adi, Budi} |
| **Pemetaan fungsi** | Fungsi → fungsi di D | pesawatDari → {Adi→F-16A, Budi→F-16B} |

### 4.2 Model

> **Model** dalam FOL adalah sebuah interpretasi yang memenuhi (membuat benar) semua kalimat dalam knowledge base.

#### Solved Problem 8 ⭐⭐

**Soal:** Diberikan knowledge base berikut:
1. Pilot(Adi)
2. Pilot(Budi)
3. ∀x [Pilot(x) ⇒ Terlatih(x)]

Tentukan apakah Terlatih(Adi) dan Terlatih(Citra) dapat disimpulkan!

**Penyelesaian:**

*Step 1:* Dari KB kita tahu: Pilot(Adi) = true, Pilot(Budi) = true

*Step 2:* Terapkan kalimat 3 dengan substitusi x = Adi:
- Pilot(Adi) ⇒ Terlatih(Adi)
- Pilot(Adi) = true
- Maka Terlatih(Adi) = **true** ✅

*Step 3:* Terapkan kalimat 3 dengan substitusi x = Citra:
- Pilot(Citra) ⇒ Terlatih(Citra)
- Pilot(Citra) tidak ada di KB (tidak diketahui)
- Implikasi P ⇒ Q bernilai true jika P = false
- Kita **tidak dapat menyimpulkan** Terlatih(Citra) bernilai true

**Jawaban:** Terlatih(Adi) **dapat** disimpulkan (true). Terlatih(Citra) **tidak dapat** disimpulkan karena tidak ada informasi bahwa Citra adalah pilot. Dalam closed-world assumption, Pilot(Citra) dianggap false, sehingga implikasi terpenuhi secara vakum, tetapi kita tetap tidak tahu apakah Citra terlatih.

---

## 5. Representasi Pengetahuan dalam FOL

### 5.1 Domain Militer

Berikut contoh bagaimana merepresentasikan pengetahuan domain militer dalam FOL:

**Konstanta:** `Adi`, `Budi`, `Skuadron11`, `Madiun`, `F16`, `SukhoinSu30`

**Predikat:**
| Predikat | Arity | Arti |
|----------|-------|------|
| `Pilot(x)` | 1 | x adalah pilot |
| `Perwira(x)` | 1 | x adalah perwira |
| `Pesawat(x)` | 1 | x adalah pesawat |
| `Menerbangkan(x, y)` | 2 | x menerbangkan y |
| `DiSkuadron(x, s)` | 2 | x berada di skuadron s |
| `LebihCepatDari(x, y)` | 2 | x lebih cepat dari y |
| `Pangkat(x, p)` | 2 | x memiliki pangkat p |

**Fungsi:**
| Fungsi | Arity | Arti |
|--------|-------|------|
| `komandanDari(x)` | 1 | komandan dari x |
| `markasSkuadron(s)` | 1 | markas dari skuadron s |

**Knowledge Base contoh:**

```
1. Pilot(Adi)
2. Perwira(Adi)
3. Pangkat(Adi, Kapten)
4. DiSkuadron(Adi, Skuadron11)
5. Menerbangkan(Adi, F16)
6. ∀x [Pilot(x) ⇒ Terlatih(x)]
7. ∀x [Perwira(x) ⇒ ∃y [Memimpin(x, y)]]
8. ∀x ∀y [(Pilot(x) ∧ Menerbangkan(x, y)) ⇒ Pesawat(y)]
```

#### Solved Problem 9 ⭐⭐

**Soal:** Representasikan pengetahuan berikut dalam FOL:
1. "Setiap perwira yang memiliki pangkat Kolonel memimpin setidaknya satu batalion"
2. "Tidak ada tentara yang menjadi anggota dua angkatan sekaligus"
3. "Adi adalah komandan Budi jika dan hanya jika Budi melapor kepada Adi"

**Penyelesaian:**

*Step 1:* Kalimat 1 — "Setiap perwira yang memiliki pangkat Kolonel memimpin setidaknya satu batalion"

$$\forall x \, [(\text{Perwira}(x) \wedge \text{Pangkat}(x, \text{Kolonel})) \Rightarrow \exists y \, [\text{Batalion}(y) \wedge \text{Memimpin}(x, y)]]$$

*Step 2:* Kalimat 2 — "Tidak ada tentara yang menjadi anggota dua angkatan sekaligus"

$$\neg \exists x \, \exists a_1 \, \exists a_2 \, [\text{Tentara}(x) \wedge \text{Anggota}(x, a_1) \wedge \text{Anggota}(x, a_2) \wedge \text{Angkatan}(a_1) \wedge \text{Angkatan}(a_2) \wedge \neg(a_1 = a_2)]$$

Atau equivalen:

$$\forall x \, \forall a_1 \, \forall a_2 \, [(\text{Tentara}(x) \wedge \text{Anggota}(x, a_1) \wedge \text{Anggota}(x, a_2) \wedge \text{Angkatan}(a_1) \wedge \text{Angkatan}(a_2)) \Rightarrow (a_1 = a_2)]$$

*Step 3:* Kalimat 3 — "Adi adalah komandan Budi jika dan hanya jika Budi melapor kepada Adi"

$$\text{Komandan}(\text{Adi}, \text{Budi}) \Leftrightarrow \text{MelaporKe}(\text{Budi}, \text{Adi})$$

**Jawaban:** Tiga kalimat FOL di atas merepresentasikan pengetahuan yang diminta secara formal dan presisi.

---

### 5.2 Pola Representasi Umum

Berikut beberapa pola yang sering digunakan dalam merepresentasikan pengetahuan:

| Pola | Template FOL | Contoh |
|------|-------------|--------|
| Semua X adalah Y | ∀x [X(x) ⇒ Y(x)] | Semua pilot terlatih |
| Ada X yang Y | ∃x [X(x) ∧ Y(x)] | Ada drone yang rusak |
| Tidak ada X yang Y | ¬∃x [X(x) ∧ Y(x)] atau ∀x [X(x) ⇒ ¬Y(x)] | Tidak ada pilot yang pengecut |
| Hanya X yang Y | ∀x [Y(x) ⇒ X(x)] | Hanya perwira yang boleh memimpin |
| Jika X maka Y | ∀x [X(x) ⇒ Y(x)] | Jika tentara, maka disiplin |
| X jika dan hanya jika Y | ∀x [X(x) ⇔ Y(x)] | Lulus iff nilai ≥ 60 |

#### Solved Problem 10 ⭐⭐

**Soal:** Representasikan aturan berikut dalam FOL: "Hanya pesawat yang memiliki izin terbang yang boleh memasuki zona militer"

**Penyelesaian:**

*Step 1:* Analisis kata "hanya"
- "Hanya X boleh Y" berarti "Jika Y maka X"
- "Hanya pesawat yang punya izin yang boleh masuk" = "Jika masuk, maka punya izin"

*Step 2:* Tentukan predikat
- `Pesawat(x)` — x adalah pesawat
- `IzinTerbang(x)` — x memiliki izin terbang
- `MasukZonaMiliter(x)` — x memasuki zona militer

*Step 3:* Bangun kalimat FOL

$$\forall x \, [\text{MasukZonaMiliter}(x) \Rightarrow (\text{Pesawat}(x) \wedge \text{IzinTerbang}(x))]$$

**Jawaban:** ∀x [MasukZonaMiliter(x) ⇒ (Pesawat(x) ∧ IzinTerbang(x))]

Catatan: Pola "hanya X yang Y" diterjemahkan menjadi "Y ⇒ X" (implikasi dibalik dari pola "semua X adalah Y").

---

## 6. Unifikasi

### 6.1 Konsep Unifikasi

> **Unifikasi** adalah proses menemukan substitusi variabel yang membuat dua ekspresi logika menjadi identik.

> **Substitusi** (θ) adalah pemetaan variabel ke term. Dituliskan sebagai: θ = {x/A, y/B} yang berarti "ganti x dengan A dan y dengan B".

**Contoh:**
- Unifikasi `Pilot(x)` dengan `Pilot(Adi)`: θ = {x/Adi} ✅
- Unifikasi `Suka(x, y)` dengan `Suka(Adi, Budi)`: θ = {x/Adi, y/Budi} ✅
- Unifikasi `Pilot(Adi)` dengan `Pilot(Budi)`: **GAGAL** ❌ (konstanta berbeda)

![Proses Unifikasi](images/p10-02-unification-process.png)

*Gambar 10.2: Proses unifikasi dua ekspresi FOL*

### 6.2 Aturan Unifikasi

| Kondisi | Hasil | Contoh |
|---------|-------|--------|
| Variabel dengan term apapun | Berhasil | Unify(x, Adi) = {x/Adi} |
| Konstanta dengan konstanta sama | Berhasil | Unify(Adi, Adi) = {} |
| Konstanta dengan konstanta beda | Gagal | Unify(Adi, Budi) = FAIL |
| Fungsi sama, argumen cocok | Berhasil | Unify(f(x), f(Adi)) = {x/Adi} |
| Fungsi berbeda | Gagal | Unify(f(x), g(x)) = FAIL |
| Variabel muncul di term yang akan di-unify | Gagal (occur check) | Unify(x, f(x)) = FAIL |

> **Occur Check:** Unifikasi x dengan term yang mengandung x akan gagal. Misalnya, unifikasi x dengan f(x) gagal karena akan menghasilkan substitusi tak terhingga.

### 6.3 Most General Unifier (MGU)

> **Most General Unifier (MGU)** adalah substitusi paling umum yang membuat dua ekspresi identik. MGU memberikan substitusi seminimal mungkin.

**Contoh:**
- Unifikasi `Suka(x, y)` dengan `Suka(Adi, z)`:
  - θ₁ = {x/Adi, y/z} → MGU ✅ (paling umum)
  - θ₂ = {x/Adi, y/Budi, z/Budi} → Juga valid, tetapi **bukan** MGU (lebih spesifik)

#### Solved Problem 11 ⭐⭐

**Soal:** Temukan MGU untuk pasangan ekspresi berikut:
1. `Menembak(x, y)` dan `Menembak(DroneA, TargetB)`
2. `Atasan(x, ayahDari(x))` dan `Atasan(Adi, y)`
3. `Patroli(x, Natuna)` dan `Patroli(y, z)`

**Penyelesaian:**

*Pasangan 1:* `Menembak(x, y)` dan `Menembak(DroneA, TargetB)`

- Predikat sama: Menembak ✅
- Unifikasi argumen 1: x dengan DroneA → {x/DroneA}
- Unifikasi argumen 2: y dengan TargetB → {y/TargetB}
- **MGU = {x/DroneA, y/TargetB}** ✅

*Pasangan 2:* `Atasan(x, ayahDari(x))` dan `Atasan(Adi, y)`

- Predikat sama: Atasan ✅
- Unifikasi argumen 1: x dengan Adi → {x/Adi}
- Terapkan substitusi ke argumen 2: ayahDari(x) menjadi ayahDari(Adi)
- Unifikasi argumen 2: ayahDari(Adi) dengan y → {y/ayahDari(Adi)}
- **MGU = {x/Adi, y/ayahDari(Adi)}** ✅

*Pasangan 3:* `Patroli(x, Natuna)` dan `Patroli(y, z)`

- Predikat sama: Patroli ✅
- Unifikasi argumen 1: x dengan y → {x/y} (atau {y/x})
- Unifikasi argumen 2: Natuna dengan z → {z/Natuna}
- **MGU = {x/y, z/Natuna}** ✅

**Jawaban:** (1) {x/DroneA, y/TargetB}, (2) {x/Adi, y/ayahDari(Adi)}, (3) {x/y, z/Natuna}

---

#### Solved Problem 12 ⭐⭐

**Soal:** Tentukan apakah unifikasi berhasil atau gagal, dan temukan MGU jika berhasil:
1. `P(x, f(y))` dan `P(g(z), f(z))`
2. `Q(x, x)` dan `Q(Adi, Budi)`
3. `R(x, f(x))` dan `R(y, y)`

**Penyelesaian:**

*Pasangan 1:* `P(x, f(y))` dan `P(g(z), f(z))`

- Unifikasi argumen 1: x dengan g(z) → {x/g(z)}
- Unifikasi argumen 2: f(y) dengan f(z)
  - Fungsi sama (f), unifikasi argumen: y dengan z → {y/z}
- **MGU = {x/g(z), y/z}** ✅ Berhasil

*Pasangan 2:* `Q(x, x)` dan `Q(Adi, Budi)`

- Unifikasi argumen 1: x dengan Adi → {x/Adi}
- Terapkan substitusi: Q(Adi, Adi) dan Q(Adi, Budi)
- Unifikasi argumen 2: Adi dengan Budi → **GAGAL** ❌

*Pasangan 3:* `R(x, f(x))` dan `R(y, y)`

- Unifikasi argumen 1: x dengan y → {x/y}
- Terapkan substitusi: R(y, f(y)) dan R(y, y)
- Unifikasi argumen 2: f(y) dengan y → **GAGAL** (occur check: y muncul di f(y)) ❌

**Jawaban:** (1) Berhasil, MGU = {x/g(z), y/z}. (2) Gagal karena x tidak bisa menjadi Adi dan Budi sekaligus. (3) Gagal karena occur check — y tidak bisa di-unify dengan f(y).

---

### 6.4 Algoritma Unifikasi

**Pseudocode algoritma unifikasi:**

```python
def unify(x, y, theta={}):
    if theta is FAILURE:
        return FAILURE
    elif x == y:
        return theta
    elif is_variable(x):
        return unify_var(x, y, theta)
    elif is_variable(y):
        return unify_var(y, x, theta)
    elif is_compound(x) and is_compound(y):
        return unify(args(x), args(y), 
                     unify(op(x), op(y), theta))
    elif is_list(x) and is_list(y):
        return unify(rest(x), rest(y), 
                     unify(first(x), first(y), theta))
    else:
        return FAILURE

def unify_var(var, x, theta):
    if var in theta:
        return unify(theta[var], x, theta)
    elif x in theta:
        return unify(var, theta[x], theta)
    elif occur_check(var, x):
        return FAILURE
    else:
        return theta + {var/x}
```

#### Solved Problem 13 ⭐⭐⭐

**Soal:** Trace algoritma unifikasi untuk: `Bertemu(x, istriDari(y))` dan `Bertemu(ayahDari(Adi), istriDari(ayahDari(Adi)))`

**Penyelesaian:**

*Step 1:* Panggil unify(Bertemu(x, istriDari(y)), Bertemu(ayahDari(Adi), istriDari(ayahDari(Adi))), {})

*Step 2:* Keduanya compound, operator sama (Bertemu). Unifikasi argumen:
- Unifikasi argumen pertama: unify(x, ayahDari(Adi), {})
  - x adalah variabel, x tidak di theta
  - Occur check: x tidak muncul di ayahDari(Adi) ✅
  - θ = {x/ayahDari(Adi)}

*Step 3:* Unifikasi argumen kedua: unify(istriDari(y), istriDari(ayahDari(Adi)), {x/ayahDari(Adi)})
  - Keduanya compound, operator sama (istriDari)
  - Unifikasi argumen: unify(y, ayahDari(Adi), {x/ayahDari(Adi)})
    - y adalah variabel, y tidak di theta
    - Occur check: y tidak muncul di ayahDari(Adi) ✅
    - θ = {x/ayahDari(Adi), y/ayahDari(Adi)}

*Step 4:* Verifikasi

Terapkan θ ke ekspresi 1:
- Bertemu(ayahDari(Adi), istriDari(ayahDari(Adi))) ✅ Sama!

**Jawaban:** MGU = {x/ayahDari(Adi), y/ayahDari(Adi)}. Setelah substitusi, kedua ekspresi menjadi identik: `Bertemu(ayahDari(Adi), istriDari(ayahDari(Adi)))`.

---

## 7. Forward Chaining

### 7.1 Konsep Forward Chaining

> **Forward Chaining** (data-driven reasoning) adalah metode inferensi yang dimulai dari **fakta yang diketahui** dan menerapkan aturan secara berulang untuk menghasilkan fakta baru, sampai query terjawab atau tidak ada fakta baru.

![Forward Chaining](images/p10-03-forward-chaining.png)

*Gambar 10.3: Proses forward chaining dari fakta ke kesimpulan*

**Algoritma Forward Chaining:**

```
function FORWARD-CHAINING(KB, query):
    repeat:
        new_facts = {}
        for each rule (conditions ⇒ conclusion) in KB:
            for each substitution θ such that 
                conditions match known facts with θ:
                new_fact = SUBST(θ, conclusion)
                if new_fact is not in KB:
                    add new_fact to KB and new_facts
                    if new_fact matches query:
                        return θ
    until new_facts is empty
    return FAILURE
```

### 7.2 Contoh Forward Chaining

#### Solved Problem 14 ⭐⭐

**Soal:** Diberikan knowledge base:

**Fakta:**
1. Pilot(Adi)
2. Perwira(Adi)
3. Berpengalaman(Adi)

**Aturan:**
4. ∀x [Pilot(x) ⇒ Terlatih(x)]
5. ∀x [(Perwira(x) ∧ Terlatih(x)) ⇒ BolehMemimpin(x)]
6. ∀x [(BolehMemimpin(x) ∧ Berpengalaman(x)) ⇒ KandidatKomandan(x)]

**Query:** KandidatKomandan(Adi)?

Gunakan forward chaining untuk menjawab query!

**Penyelesaian:**

*Iterasi 1:*
- Cek aturan 4 dengan θ = {x/Adi}: Pilot(Adi) ✅
  - Hasilkan fakta baru: **Terlatih(Adi)**
- Cek aturan 5: Perwira(Adi) ✅, Terlatih(Adi) ✅ (baru saja diturunkan)
  - Hasilkan fakta baru: **BolehMemimpin(Adi)**
- Cek aturan 6: BolehMemimpin(Adi) ✅, Berpengalaman(Adi) ✅
  - Hasilkan fakta baru: **KandidatKomandan(Adi)** 🎯

*Trace:*

| Langkah | Aturan | Substitusi | Fakta Baru |
|---------|--------|------------|------------|
| 1 | Aturan 4 | {x/Adi} | Terlatih(Adi) |
| 2 | Aturan 5 | {x/Adi} | BolehMemimpin(Adi) |
| 3 | Aturan 6 | {x/Adi} | KandidatKomandan(Adi) ← Query! |

**Jawaban:** Ya, **KandidatKomandan(Adi)** dapat disimpulkan melalui forward chaining dalam 3 langkah inferensi.

---

#### Solved Problem 15 ⭐⭐⭐

**Soal:** Diberikan knowledge base tentang sistem keamanan cyber:

**Fakta:**
1. ServerWeb(S1)
2. TerhubungInternet(S1)
3. MenjalankanApache(S1)
4. VersiLama(S1)
5. ServerDB(S2)
6. TerhubungKe(S1, S2)

**Aturan:**
7. ∀x [(ServerWeb(x) ∧ TerhubungInternet(x)) ⇒ DapatDiserang(x)]
8. ∀x [(DapatDiserang(x) ∧ VersiLama(x)) ⇒ Rentan(x)]
9. ∀x ∀y [(Rentan(x) ∧ TerhubungKe(x, y)) ⇒ TerancamLateral(y)]
10. ∀x [(TerancamLateral(x) ∧ ServerDB(x)) ⇒ DataTerancam(x)]

**Query:** DataTerancam(S2)?

Lakukan forward chaining lengkap!

**Penyelesaian:**

*Iterasi 1:*
- Aturan 7 dengan {x/S1}: ServerWeb(S1) ✅ ∧ TerhubungInternet(S1) ✅
  - Fakta baru: **DapatDiserang(S1)**

*Iterasi 2:*
- Aturan 8 dengan {x/S1}: DapatDiserang(S1) ✅ ∧ VersiLama(S1) ✅
  - Fakta baru: **Rentan(S1)**

*Iterasi 3:*
- Aturan 9 dengan {x/S1, y/S2}: Rentan(S1) ✅ ∧ TerhubungKe(S1, S2) ✅
  - Fakta baru: **TerancamLateral(S2)**

*Iterasi 4:*
- Aturan 10 dengan {x/S2}: TerancamLateral(S2) ✅ ∧ ServerDB(S2) ✅
  - Fakta baru: **DataTerancam(S2)** 🎯

| Langkah | Aturan | Substitusi | Fakta Baru |
|---------|--------|------------|------------|
| 1 | Aturan 7 | {x/S1} | DapatDiserang(S1) |
| 2 | Aturan 8 | {x/S1} | Rentan(S1) |
| 3 | Aturan 9 | {x/S1, y/S2} | TerancamLateral(S2) |
| 4 | Aturan 10 | {x/S2} | DataTerancam(S2) ← Query! |

**Jawaban:** Ya, **DataTerancam(S2)** dapat disimpulkan. Chain of reasoning: Server web S1 yang terhubung internet dan versi lama rentan terhadap serangan, dan koneksinya ke database S2 membuat data di S2 terancam melalui lateral movement.

---

## 8. Backward Chaining

### 8.1 Konsep Backward Chaining

> **Backward Chaining** (goal-driven reasoning) adalah metode inferensi yang dimulai dari **query (goal)** dan bekerja mundur, mencari fakta dan aturan yang dapat membuktikan query tersebut.

![Backward Chaining](images/p10-04-backward-chaining.png)

*Gambar 10.4: Proses backward chaining dari goal ke fakta*

**Algoritma Backward Chaining:**

```
function BACKWARD-CHAINING(KB, goal):
    if goal is a known fact in KB:
        return SUCCESS
    for each rule (conditions ⇒ conclusion) in KB:
        if conclusion unifies with goal via θ:
            sub_goals = SUBST(θ, conditions)
            if all sub_goals can be proven by 
               BACKWARD-CHAINING(KB, sub_goal):
                return SUCCESS
    return FAILURE
```

### 8.2 Perbandingan Forward dan Backward Chaining

| Aspek | Forward Chaining | Backward Chaining |
|-------|------------------|-------------------|
| Arah | Fakta → Kesimpulan | Goal → Fakta |
| Nama lain | Data-driven | Goal-driven |
| Mulai dari | Fakta yang diketahui | Query yang ditanyakan |
| Strategi | Bottom-up | Top-down |
| Cocok untuk | Banyak query, sedikit fakta awal | Satu query spesifik |
| Kelemahan | Bisa menghasilkan fakta yang tidak relevan | Bisa gagal jika banyak dead ends |
| Analogi | "Apa yang bisa saya simpulkan?" | "Bagaimana cara membuktikan X?" |

#### Solved Problem 16 ⭐⭐

**Soal:** Menggunakan KB yang sama dari Solved Problem 14, lakukan backward chaining untuk query KandidatKomandan(Adi).

**Fakta:** Pilot(Adi), Perwira(Adi), Berpengalaman(Adi)
**Aturan 4-6:** (sama seperti sebelumnya)

**Penyelesaian:**

*Step 1:* Goal: KandidatKomandan(Adi)
- Cari aturan yang conclusion-nya cocok → Aturan 6: BolehMemimpin(x) ∧ Berpengalaman(x) ⇒ KandidatKomandan(x)
- Unifikasi: θ = {x/Adi}
- Sub-goals: BolehMemimpin(Adi) **DAN** Berpengalaman(Adi)

*Step 2:* Sub-goal 1: BolehMemimpin(Adi)
- Bukan fakta di KB
- Cari aturan → Aturan 5: Perwira(x) ∧ Terlatih(x) ⇒ BolehMemimpin(x)
- θ = {x/Adi}
- Sub-goals: Perwira(Adi) **DAN** Terlatih(Adi)

*Step 3:* Sub-goal 1a: Perwira(Adi)
- Ada di KB sebagai fakta → **TERBUKTI** ✅

*Step 4:* Sub-goal 1b: Terlatih(Adi)
- Bukan fakta di KB
- Cari aturan → Aturan 4: Pilot(x) ⇒ Terlatih(x)
- θ = {x/Adi}
- Sub-goal: Pilot(Adi)

*Step 5:* Sub-goal 1b-i: Pilot(Adi)
- Ada di KB sebagai fakta → **TERBUKTI** ✅
- Maka Terlatih(Adi) **TERBUKTI** ✅
- Maka BolehMemimpin(Adi) **TERBUKTI** ✅

*Step 6:* Sub-goal 2: Berpengalaman(Adi)
- Ada di KB sebagai fakta → **TERBUKTI** ✅

*Step 7:* Semua sub-goals terbukti → **KandidatKomandan(Adi) TERBUKTI** ✅

**Jawaban:** KandidatKomandan(Adi) terbukti melalui backward chaining. Proof tree menunjukkan dekomposisi goal menjadi sub-goal yang akhirnya terpenuhi oleh fakta di KB.

---

#### Solved Problem 17 ⭐⭐⭐

**Soal:** Diberikan knowledge base:

**Fakta:**
1. Tentara(Adi)
2. Tentara(Budi)
3. Pangkat(Adi, Sersan)
4. Pangkat(Budi, Kopral)
5. Misi(Alpha)
6. TingkatBahaya(Alpha, Tinggi)

**Aturan:**
7. ∀x ∀m [(Tentara(x) ∧ Pangkat(x, Sersan) ∧ Misi(m) ∧ TingkatBahaya(m, Tinggi)) ⇒ BolehMemimpin(x, m)]
8. ∀x ∀m [(BolehMemimpin(x, m) ∧ Tentara(x)) ⇒ PemimpinMisi(x, m)]
9. ∀x ∀y ∀m [(PemimpinMisi(x, m) ∧ Tentara(y) ∧ ¬(x = y)) ⇒ AngotaTim(y, m)]

**Query:** AnggotaTim(Budi, Alpha)?

Lakukan backward chaining dan tunjukkan proof tree!

**Penyelesaian:**

*Step 1:* Goal: AnggotaTim(Budi, Alpha)
- Aturan 9: PemimpinMisi(x, m) ∧ Tentara(y) ∧ ¬(x = y) ⇒ AnggotaTim(y, m)
- Unifikasi AnggotaTim(y, m) dengan AnggotaTim(Budi, Alpha): θ = {y/Budi, m/Alpha}
- Sub-goals: PemimpinMisi(x, Alpha) ∧ Tentara(Budi) ∧ ¬(x = Budi)

*Step 2:* Sub-goal: Tentara(Budi) → Fakta 2 ✅

*Step 3:* Sub-goal: PemimpinMisi(x, Alpha)
- Aturan 8: BolehMemimpin(x, m) ∧ Tentara(x) ⇒ PemimpinMisi(x, m)
- θ = {m/Alpha}
- Sub-goals: BolehMemimpin(x, Alpha) ∧ Tentara(x)

*Step 4:* Sub-goal: BolehMemimpin(x, Alpha)
- Aturan 7: Tentara(x) ∧ Pangkat(x, Sersan) ∧ Misi(Alpha) ∧ TingkatBahaya(Alpha, Tinggi)
- Coba x = Adi:
  - Tentara(Adi) ✅ (Fakta 1)
  - Pangkat(Adi, Sersan) ✅ (Fakta 3)
  - Misi(Alpha) ✅ (Fakta 5)
  - TingkatBahaya(Alpha, Tinggi) ✅ (Fakta 6)
  - θ = {x/Adi} → BolehMemimpin(Adi, Alpha) ✅

*Step 5:* Kembali ke Step 3: Tentara(Adi) ✅ → PemimpinMisi(Adi, Alpha) ✅

*Step 6:* Kembali ke Step 1: ¬(Adi = Budi) ✅ (karena konstanta berbeda)

*Step 7:* Semua sub-goals terbukti → **AnggotaTim(Budi, Alpha) TERBUKTI** ✅

**Proof Tree:**

```
AnggotaTim(Budi, Alpha)
├── PemimpinMisi(Adi, Alpha)
│   ├── BolehMemimpin(Adi, Alpha)
│   │   ├── Tentara(Adi) ✅ [Fakta 1]
│   │   ├── Pangkat(Adi, Sersan) ✅ [Fakta 3]
│   │   ├── Misi(Alpha) ✅ [Fakta 5]
│   │   └── TingkatBahaya(Alpha, Tinggi) ✅ [Fakta 6]
│   └── Tentara(Adi) ✅ [Fakta 1]
├── Tentara(Budi) ✅ [Fakta 2]
└── ¬(Adi = Budi) ✅ [Unique Name Assumption]
```

**Jawaban:** AnggotaTim(Budi, Alpha) terbukti benar. Adi sebagai Sersan memimpin misi berbahaya Alpha, dan Budi sebagai tentara lain menjadi anggota tim.

---

## 9. Resolution dalam FOL

### 9.1 Generalized Modus Ponens

> **Generalized Modus Ponens** adalah aturan inferensi untuk logika predikat yang menggabungkan Modus Ponens dengan unifikasi.

$$\frac{p_1', p_2', ..., p_n', \quad (p_1 \wedge p_2 \wedge ... \wedge p_n \Rightarrow q)}{q\theta}$$

dimana $\theta$ adalah substitusi sedemikian sehingga $p_i'\theta = p_i\theta$ untuk semua $i$.

#### Solved Problem 18 ⭐⭐

**Soal:** Diberikan:
- Fakta: Pilot(Adi), DiWilayah(Adi, Timur)
- Aturan: ∀x ∀w [(Pilot(x) ∧ DiWilayah(x, w)) ⇒ BisaTerbang(x, w)]

Terapkan Generalized Modus Ponens!

**Penyelesaian:**

*Step 1:* Identifikasi premis
- p₁' = Pilot(Adi)
- p₂' = DiWilayah(Adi, Timur)
- Aturan: Pilot(x) ∧ DiWilayah(x, w) ⇒ BisaTerbang(x, w)

*Step 2:* Temukan unifier θ
- Unifikasi Pilot(Adi) dengan Pilot(x): θ₁ = {x/Adi}
- Unifikasi DiWilayah(Adi, Timur) dengan DiWilayah(x, w): θ₂ = {x/Adi, w/Timur}
- MGU: θ = {x/Adi, w/Timur}

*Step 3:* Terapkan θ ke conclusion
- BisaTerbang(x, w) dengan θ = BisaTerbang(Adi, Timur)

**Jawaban:** Dari Generalized Modus Ponens, kita menyimpulkan **BisaTerbang(Adi, Timur)** dengan substitusi θ = {x/Adi, w/Timur}.

---

### 9.2 Resolution dalam FOL

> **Resolution** dalam FOL menggabungkan dua klausa yang mengandung literal komplementer (setelah unifikasi) untuk menghasilkan klausa baru (resolvent).

Proses resolution dalam FOL:
1. Konversi semua kalimat ke **Conjunctive Normal Form (CNF)**
2. Negasi query dan tambahkan ke KB
3. Terapkan resolution sampai menemukan klausa kosong (kontradiksi) atau tidak ada resolvent baru

**Langkah konversi ke CNF di FOL:**
1. Eliminasi ⇔ (bikonditional)
2. Eliminasi ⇒ (implikasi)
3. Pindahkan ¬ ke dalam (De Morgan, double negation)
4. Standardisasi variabel (setiap kuantor variabel unik)
5. Skolemisasi (ganti ∃ dengan fungsi Skolem)
6. Hapus ∀
7. Distribusi ∨ atas ∧

#### Solved Problem 19 ⭐⭐⭐

**Soal:** Konversi kalimat berikut ke CNF:
$$\forall x \, [\text{Tentara}(x) \Rightarrow \exists y \, [\text{Senjata}(y) \wedge \text{Membawa}(x, y)]]$$

**Penyelesaian:**

*Step 1:* Eliminasi ⇒
$$\forall x \, [\neg\text{Tentara}(x) \vee \exists y \, [\text{Senjata}(y) \wedge \text{Membawa}(x, y)]]$$

*Step 2:* Skolemisasi — ganti ∃y dengan fungsi Skolem f(x)

Karena y berada dalam scope ∀x, kita ganti y dengan fungsi Skolem yang bergantung pada x:
$$\forall x \, [\neg\text{Tentara}(x) \vee [\text{Senjata}(f(x)) \wedge \text{Membawa}(x, f(x))]]$$

*Step 3:* Hapus ∀
$$\neg\text{Tentara}(x) \vee [\text{Senjata}(f(x)) \wedge \text{Membawa}(x, f(x))]$$

*Step 4:* Distribusi ∨ atas ∧
$$[\neg\text{Tentara}(x) \vee \text{Senjata}(f(x))] \wedge [\neg\text{Tentara}(x) \vee \text{Membawa}(x, f(x))]$$

*Step 5:* Dua klausa CNF:
- Klausa 1: ¬Tentara(x) ∨ Senjata(f(x))
- Klausa 2: ¬Tentara(x) ∨ Membawa(x, f(x))

**Jawaban:** Hasil CNF terdiri dari dua klausa. Fungsi Skolem f(x) merepresentasikan "senjata yang dibawa oleh tentara x" — setiap tentara memiliki senjata masing-masing yang bergantung pada identitas tentara tersebut.

---

## 10. Aplikasi FOL

### 10.1 Expert Systems

> **Expert System** (sistem pakar) adalah program komputer yang menggunakan knowledge base dan inference engine untuk meniru kemampuan seorang ahli dalam domain tertentu.

**Komponen Expert System:**

| Komponen | Fungsi | Contoh |
|----------|--------|--------|
| **Knowledge Base** | Menyimpan fakta dan aturan | Aturan diagnosis kerusakan radar |
| **Inference Engine** | Forward/backward chaining | Menyimpulkan jenis kerusakan |
| **User Interface** | Interaksi dengan pengguna | Input gejala, output diagnosis |
| **Explanation Facility** | Menjelaskan reasoning | "Radar rusak karena..." |

**Contoh Expert System militer:**
- Diagnosis kerusakan peralatan militer
- Rekomendasi taktis berdasarkan situasi medan
- Identifikasi ancaman berdasarkan sinyal radar

#### Solved Problem 20 ⭐⭐

**Soal:** Rancang knowledge base sederhana (dalam FOL) untuk expert system diagnosis kerusakan komunikasi radio militer!

**Penyelesaian:**

*Step 1:* Identifikasi predikat

| Predikat | Arti |
|----------|------|
| Gejala(radio, gejala) | Radio menunjukkan gejala tertentu |
| Kerusakan(radio, jenis) | Radio mengalami kerusakan jenis tertentu |
| Tindakan(radio, aksi) | Tindakan yang harus dilakukan |

*Step 2:* Tulis aturan diagnosis dalam FOL

```
Aturan 1: ∀r [Gejala(r, TidakAdaSuara) ∧ Gejala(r, LampuMati) 
           ⇒ Kerusakan(r, CatuDaya)]

Aturan 2: ∀r [Gejala(r, SuaraPutus) ∧ Gejala(r, SinyalLemah)
           ⇒ Kerusakan(r, Antena)]

Aturan 3: ∀r [Gejala(r, Noise) ∧ Gejala(r, FrekuensiBergeser)
           ⇒ Kerusakan(r, Osilator)]

Aturan 4: ∀r [Kerusakan(r, CatuDaya) 
           ⇒ Tindakan(r, GantiBaterai)]

Aturan 5: ∀r [Kerusakan(r, Antena) 
           ⇒ Tindakan(r, PeriksaKoneksiAntena)]

Aturan 6: ∀r [Kerusakan(r, Osilator) 
           ⇒ Tindakan(r, KirimKeBengkel)]
```

*Step 3:* Contoh penggunaan

**Input fakta:** Gejala(Radio5, SuaraPutus) ∧ Gejala(Radio5, SinyalLemah)

**Forward chaining:**
- Aturan 2 cocok → Kerusakan(Radio5, Antena)
- Aturan 5 cocok → Tindakan(Radio5, PeriksaKoneksiAntena)

**Jawaban:** KB di atas dapat melakukan diagnosis sederhana kerusakan radio militer berdasarkan gejala yang dilaporkan, menggunakan forward chaining untuk menyimpulkan jenis kerusakan dan tindakan yang diperlukan.

---

### 10.2 Knowledge Graphs

> **Knowledge Graph** adalah representasi pengetahuan berbasis graf yang menggunakan triple (subjek, predikat, objek) untuk merepresentasikan hubungan antar entitas. Ini sangat berkaitan dengan FOL karena setiap triple merepresentasikan kalimat atomik FOL.

**Hubungan Knowledge Graph dengan FOL:**

| Knowledge Graph Triple | FOL Equivalent |
|----------------------|----------------|
| (Adi, tipePesawat, F16) | TipePesawat(Adi, F16) |
| (F16, buatanNegara, AS) | BuatanNegara(F16, AS) |
| (Adi, berpangkat, Kapten) | Pangkat(Adi, Kapten) |

**Contoh aplikasi:**
- Wikidata, Google Knowledge Graph
- Knowledge graph intelijen militer
- Ontologi peralatan militer

#### Solved Problem 21 ⭐

**Soal:** Diberikan knowledge graph triple berikut, terjemahkan ke FOL:
- (KRI_Nanggala, jenisKapal, KapalSelam)
- (KRI_Nanggala, homeBase, Surabaya)
- (KRI_Nanggala, dilengkapi, Torpedo)
- (KapalSelam, subClassOf, KapalPerang)

**Penyelesaian:**

*Step 1:* Terjemahkan setiap triple

1. JenisKapal(KRI_Nanggala, KapalSelam)
2. HomeBase(KRI_Nanggala, Surabaya)
3. Dilengkapi(KRI_Nanggala, Torpedo)
4. ∀x [KapalSelam(x) ⇒ KapalPerang(x)]

*Step 2:* Triple 4 menggunakan subClassOf yang berarti relasi "is-a" universal

**Jawaban:** Empat kalimat FOL di atas merepresentasikan knowledge graph, dengan triple ke-4 menggunakan kuantor universal untuk merepresentasikan relasi subclass.

---

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Sebuah sistem intelijen militer menggunakan knowledge base FOL. Diberikan:

**Fakta:**
1. Negara(Xlandia)
2. MemilikSenjata(Xlandia, RudalBalistik)
3. MengembangkanNuklir(Xlandia)
4. Bertetangga(Indonesia, Xlandia)

**Aturan:**
5. ∀n [(Negara(n) ∧ MemilikSenjata(n, RudalBalistik) ∧ MengembangkanNuklir(n)) ⇒ AncamanNuklir(n)]
6. ∀n1 ∀n2 [(AncamanNuklir(n1) ∧ Bertetangga(n2, n1)) ⇒ PerluPeningkatanPertahanan(n2)]
7. ∀n [PerluPeningkatanPertahanan(n) ⇒ RekomendasiSistemPertahananRudal(n)]

Gunakan **kedua metode** (forward chaining dan backward chaining) untuk membuktikan RekomendasiSistemPertahananRudal(Indonesia). Bandingkan kedua proses!

**Penyelesaian:**

**Forward Chaining:**

| Langkah | Aturan | Substitusi | Fakta Baru |
|---------|--------|------------|------------|
| 1 | Aturan 5 | {n/Xlandia} | AncamanNuklir(Xlandia) |
| 2 | Aturan 6 | {n1/Xlandia, n2/Indonesia} | PerluPeningkatanPertahanan(Indonesia) |
| 3 | Aturan 7 | {n/Indonesia} | RekomendasiSistemPertahananRudal(Indonesia) ✅ |

**Backward Chaining:**

```
Goal: RekomendasiSistemPertahananRudal(Indonesia)
├── [Aturan 7, θ={n/Indonesia}]
├── Sub-goal: PerluPeningkatanPertahanan(Indonesia)
│   ├── [Aturan 6, θ={n2/Indonesia}]
│   ├── Sub-goal: AncamanNuklir(n1)
│   │   ├── [Aturan 5, θ={n/n1}]
│   │   ├── Sub-goal: Negara(n1) → coba Xlandia ✅
│   │   ├── Sub-goal: MemilikSenjata(Xlandia, RudalBalistik) ✅
│   │   └── Sub-goal: MengembangkanNuklir(Xlandia) ✅
│   │   → AncamanNuklir(Xlandia) ✅
│   └── Sub-goal: Bertetangga(Indonesia, Xlandia) ✅
│   → PerluPeningkatanPertahanan(Indonesia) ✅
→ RekomendasiSistemPertahananRudal(Indonesia) ✅
```

**Perbandingan:**

| Aspek | Forward Chaining | Backward Chaining |
|-------|------------------|-------------------|
| Langkah | 3 langkah linear | 7 sub-goals diperiksa |
| Efisiensi di sini | Lebih efisien | Lebih banyak langkah |
| Alasan | KB kecil, semua fakta relevan | Perlu decompose tiap level |
| Kapan lebih baik | Jika banyak query | Jika hanya satu query spesifik |

**Jawaban:** Kedua metode berhasil membuktikan RekomendasiSistemPertahananRudal(Indonesia). Dalam kasus ini forward chaining lebih efisien karena KB relatif kecil dan semua fakta relevan. Namun pada KB besar dengan banyak fakta irrelevan, backward chaining bisa lebih efisien karena hanya fokus pada fakta yang dibutuhkan untuk membuktikan goal.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Representasikan "Tidak ada pesawat tanpa pilot yang boleh memasuki wilayah udara sipil" dalam FOL!

**Jawaban:** ∀x [(Pesawat(x) ∧ ¬AdaPilot(x)) ⇒ ¬BolehMasuk(x, WilayahUdaraSipil)]

### Problem S2 ⭐
**Soal:** Temukan MGU untuk `Mengawasi(x, y)` dan `Mengawasi(Radar1, KapalAsing)`

**Jawaban:** θ = {x/Radar1, y/KapalAsing}

### Problem S3 ⭐⭐
**Soal:** Jelaskan mengapa ∀x [Manusia(x) ∧ Mortal(x)] adalah representasi yang salah untuk "Semua manusia bersifat mortal" dan berikan representasi yang benar!

**Jawaban:** ∀x [Manusia(x) ∧ Mortal(x)] menyatakan bahwa SEMUA objek di dunia adalah manusia DAN mortal, yang jelas salah (meja bukan manusia). Representasi benar: ∀x [Manusia(x) ⇒ Mortal(x)] — "Jika x adalah manusia, maka x mortal."

### Problem S4 ⭐⭐
**Soal:** Diberikan fakta Drone(D1), Drone(D2), Aktif(D1), dan aturan ∀x [Drone(x) ∧ Aktif(x) ⇒ Berpatroli(x)]. Gunakan forward chaining untuk menentukan drone mana yang berpatroli!

**Jawaban:** Forward chaining dengan {x/D1}: Drone(D1) ✅ ∧ Aktif(D1) ✅ → Berpatroli(D1). Untuk D2: Drone(D2) ✅ tetapi Aktif(D2) tidak ada di KB → tidak bisa simpulkan Berpatroli(D2). Hanya **D1** yang berpatroli.

### Problem S5 ⭐⭐⭐
**Soal:** Konversi ke CNF: ∀x [∃y [Teman(x, y)] ⇒ ¬Sendirian(x)]

**Jawaban:**
1. Eliminasi ⇒: ∀x [¬∃y [Teman(x, y)] ∨ ¬Sendirian(x)]
2. Push ¬: ∀x [∀y [¬Teman(x, y)] ∨ ¬Sendirian(x)]
3. Hapus ∀: ¬Teman(x, y) ∨ ¬Sendirian(x)
4. Sudah dalam bentuk CNF: satu klausa: {¬Teman(x, y), ¬Sendirian(x)}

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Keterbatasan Proposisional** | Tidak bisa merepresentasikan objek, properti, relasi, dan generalisasi |
| **FOL** | Perluasan logika proposisional dengan term, predikat, fungsi, dan kuantor |
| **Konstanta** | Merujuk objek spesifik: Adi, DroneAlpha |
| **Variabel** | Placeholder untuk objek: x, y, z |
| **Predikat** | Properti/relasi: Pilot(x), LebihCepat(x,y) |
| **Fungsi** | Pemetaan objek ke objek: komandanDari(x) |
| **Kuantor Universal (∀)** | "Untuk semua": ∀x [P(x) ⇒ Q(x)] |
| **Kuantor Eksistensial (∃)** | "Ada": ∃x [P(x) ∧ Q(x)] |
| **Unifikasi** | Menemukan substitusi agar dua ekspresi identik |
| **MGU** | Most General Unifier — substitusi paling umum |
| **Forward Chaining** | Inferensi maju: fakta → aturan → fakta baru |
| **Backward Chaining** | Inferensi mundur: goal → sub-goals → fakta |
| **Skolemisasi** | Mengganti ∃ dengan fungsi Skolem untuk konversi CNF |
| **Expert Systems** | Sistem pakar menggunakan KB + inference engine |
| **Knowledge Graphs** | Representasi pengetahuan berbasis triple (s, p, o) |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 8-9**.
2. Poole, D.L. & Mackworth, A.K. (2023). *Artificial Intelligence: Foundations of Computational Agents* (3rd Ed.). Cambridge University Press. **Chapter 5**.
3. Ertel, W. (2017). *Introduction to Artificial Intelligence* (2nd Ed.). Springer. **Chapter 7**.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
