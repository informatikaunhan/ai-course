# Modul 12: Jaringan Bayesian

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 12  
**Topik:** Jaringan Bayesian  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan motivasi penggunaan jaringan Bayesian sebagai representasi compact distribusi probabilitas gabungan
2. Membangun jaringan Bayesian dari deskripsi masalah, termasuk topologi DAG dan tabel CPT
3. Menghitung distribusi probabilitas gabungan dari struktur jaringan Bayesian
4. Mengidentifikasi conditional independence dari struktur graf jaringan Bayesian
5. Menerapkan teknik d-separation untuk menentukan independensi antar variabel
6. Melakukan inferensi eksak menggunakan metode enumeration dan variable elimination
7. Menjelaskan konsep dasar approximate inference pada jaringan Bayesian

---

## 1. Motivasi Jaringan Bayesian

### 1.1 Keterbatasan Full Joint Distribution

Pada Pertemuan 11, kita telah mempelajari bahwa penalaran probabilistik memerlukan distribusi probabilitas gabungan (full joint distribution) untuk menghitung probabilitas apapun. Namun, pendekatan ini memiliki masalah skalabilitas yang serius.

> **Full Joint Distribution** adalah tabel yang mencantumkan probabilitas untuk setiap kombinasi nilai dari semua variabel acak dalam domain.

Untuk domain dengan $n$ variabel Boolean, full joint distribution memerlukan $2^n - 1$ parameter independen. Jika kita memiliki 30 variabel Boolean, kita memerlukan lebih dari **satu miliar** entri dalam tabel.

| Jumlah Variabel Boolean | Jumlah Parameter | Ukuran Tabel |
|:------------------------:|:----------------:|:------------:|
| 5 | 31 | Kecil |
| 10 | 1.023 | Manageable |
| 20 | 1.048.575 | Besar |
| 30 | 1.073.741.823 | Tidak Praktis |
| 100 | ~$1.27 \times 10^{30}$ | Mustahil |

Masalah ini disebut **curse of dimensionality** dalam konteks probabilitas.

### 1.2 Ide Dasar Jaringan Bayesian

> **Jaringan Bayesian** (Bayesian Network/Bayes Net) adalah representasi grafis compact dari distribusi probabilitas gabungan yang mengeksploitasi **conditional independence** antar variabel.

Ide kunci: Dalam banyak domain nyata, sebagian besar variabel hanya bergantung secara langsung pada sejumlah kecil variabel lain. Jaringan Bayesian memanfaatkan struktur ketergantungan ini untuk merepresentasikan distribusi gabungan secara efisien.

**Keuntungan jaringan Bayesian:**
1. **Representasi compact**: Jauh lebih sedikit parameter dibanding full joint distribution
2. **Intuitif**: Struktur graf menunjukkan hubungan kausal antar variabel
3. **Modular**: Setiap variabel dispesifikasikan secara lokal
4. **Inferensi efisien**: Algoritma eksak dan aproksimasi tersedia

#### Solved Problem 1 ⭐

**Soal:** Sebuah sistem pertahanan udara memiliki 20 variabel Boolean (status radar, cuaca, jenis ancaman, dll.). Berapa jumlah parameter yang diperlukan untuk full joint distribution? Jika rata-rata setiap variabel hanya bergantung pada 3 variabel lain, berapa estimasi parameter dalam jaringan Bayesian?

**Penyelesaian:**

*Step 1:* Hitung parameter full joint distribution
$$2^{20} - 1 = 1.048.575 \text{ parameter}$$

*Step 2:* Hitung estimasi parameter jaringan Bayesian
- Setiap variabel Boolean dengan 3 parent memerlukan $2^3 = 8$ parameter untuk CPT-nya
- Total: $20 \times 2^3 = 20 \times 8 = 160$ parameter

*Step 3:* Bandingkan

| Representasi | Parameter | Rasio |
|:------------:|:---------:|:-----:|
| Full Joint | 1.048.575 | 100% |
| Bayesian Network | 160 | 0.015% |

**Jawaban:** Full joint distribution memerlukan 1.048.575 parameter, sedangkan jaringan Bayesian hanya memerlukan sekitar 160 parameter — pengurangan lebih dari 6.500 kali lipat. Ini menunjukkan keunggulan representasi compact jaringan Bayesian.

---

## 2. Struktur Jaringan Bayesian

### 2.1 Komponen Jaringan Bayesian

> **Jaringan Bayesian** terdiri dari dua komponen utama:
> 1. **Directed Acyclic Graph (DAG)**: Graf berarah tanpa siklus yang menunjukkan hubungan ketergantungan antar variabel
> 2. **Conditional Probability Tables (CPT)**: Tabel probabilitas bersyarat untuk setiap node, diberikan parent-nya

![Komponen Jaringan Bayesian](images/p12-01-bayesian-network-components.png)

*Gambar 12.1: Dua komponen utama jaringan Bayesian — DAG dan CPT*

**Terminologi penting:**

| Istilah | Definisi |
|---------|----------|
| **Node** | Variabel acak dalam jaringan |
| **Edge** | Panah berarah yang menghubungkan dua node |
| **Parent** | Node yang memiliki edge keluar menuju node lain |
| **Child** | Node yang menerima edge dari node lain |
| **Root node** | Node tanpa parent |
| **Leaf node** | Node tanpa child |
| **Descendant** | Node yang dapat dicapai dengan mengikuti arah panah |
| **Non-descendant** | Node yang bukan descendant |

#### Solved Problem 2 ⭐

**Soal:** Dalam jaringan Bayesian dengan node A → B → C → D dan A → D, identifikasi parent, child, root, leaf, dan descendant dari setiap node!

**Penyelesaian:**

*Step 1:* Gambarkan struktur graf
- A → B, A → D
- B → C
- C → D

*Step 2:* Identifikasi relasi

| Node | Parent | Child | Root? | Leaf? | Descendant |
|:----:|:------:|:-----:|:-----:|:-----:|:----------:|
| A | — | B, D | Ya | Tidak | B, C, D |
| B | A | C | Tidak | Tidak | C, D |
| C | B | D | Tidak | Tidak | D |
| D | A, C | — | Tidak | Ya | — |

**Jawaban:** Node A adalah root (tanpa parent), D adalah leaf (tanpa child). D memiliki dua parent yaitu A dan C.

---

### 2.2 Directed Acyclic Graph (DAG)

> **DAG** adalah graf berarah yang tidak mengandung siklus — tidak ada jalan yang dapat kembali ke node awal dengan mengikuti arah panah.

Properti penting DAG dalam jaringan Bayesian:
- Setiap edge mewakili **ketergantungan langsung** (biasanya kausal)
- Arah panah umumnya menunjukkan **arah kausal** (sebab → akibat)
- Tidak boleh ada siklus (siklus menunjukkan kausalitas melingkar yang tidak valid)

#### Solved Problem 3 ⭐

**Soal:** Tentukan apakah graf berikut valid sebagai jaringan Bayesian:
- Graf 1: A → B → C → A
- Graf 2: A → B, A → C, B → D, C → D

**Penyelesaian:**

*Step 1:* Periksa Graf 1
- A → B → C → A membentuk siklus (dari A kembali ke A)
- **Tidak valid** karena melanggar properti acyclic

*Step 2:* Periksa Graf 2
- A → B → D (jalur 1)
- A → C → D (jalur 2)
- Tidak ada siklus — semua jalur mengarah "ke bawah"
- **Valid** sebagai DAG

**Jawaban:** Graf 1 tidak valid (mengandung siklus), Graf 2 valid sebagai jaringan Bayesian.

---

### 2.3 Conditional Probability Table (CPT)

> **CPT** untuk node $X$ dengan parent $Pa(X)$ berisi nilai $P(X | Pa(X))$ untuk setiap kombinasi nilai parent.

Jumlah parameter dalam CPT:
- Node tanpa parent (root): 1 parameter untuk Boolean ($P(X = true)$, karena $P(X = false) = 1 - P(X = true)$)
- Node dengan $k$ parent Boolean: $2^k$ baris, tetapi hanya $2^k$ parameter independen (karena setiap baris harus berjumlah 1, maka parameter independen = $2^k$ untuk variabel Boolean)

#### Solved Problem 4 ⭐

**Soal:** Sebuah node "DeteksiRadar" memiliki dua parent Boolean: "PesawatAda" dan "RadarAktif". Berapa jumlah parameter independen dalam CPT untuk DeteksiRadar? Buat contoh CPT-nya!

**Penyelesaian:**

*Step 1:* Hitung jumlah parameter
- Dua parent Boolean = $2^2 = 4$ kombinasi parent
- Setiap kombinasi memerlukan 1 parameter independen (karena DeteksiRadar Boolean)
- Total: **4 parameter independen**

*Step 2:* Buat contoh CPT

| PesawatAda | RadarAktif | P(DeteksiRadar = T) | P(DeteksiRadar = F) |
|:----------:|:----------:|:-------------------:|:-------------------:|
| T | T | 0.95 | 0.05 |
| T | F | 0.00 | 1.00 |
| F | T | 0.10 | 0.90 |
| F | F | 0.00 | 1.00 |

**Jawaban:** CPT memiliki 4 parameter independen. Tabel menunjukkan bahwa deteksi paling tinggi (0.95) ketika pesawat ada DAN radar aktif, dengan false positive 0.10 ketika radar aktif tapi tidak ada pesawat.

---

### 2.4 Contoh Klasik: Alarm Network

Contoh klasik dari Russell & Norvig mengilustrasikan jaringan Bayesian sederhana:

**Skenario:** Anda memiliki alarm pencuri di rumah. Alarm bisa dipicu oleh pencuri (Burglary) atau gempa (Earthquake). Jika alarm berbunyi, tetangga John dan Mary mungkin menelepon Anda.

![Alarm Network](images/p12-02-alarm-network.png)

*Gambar 12.2: Jaringan Bayesian Alarm Network — contoh klasik dari AIMA*

**CPT untuk Alarm Network:**

**Root nodes:**

| | P(Burglary) |
|---|:-----------:|
| | 0.001 |

| | P(Earthquake) |
|---|:-------------:|
| | 0.002 |

**Alarm (parent: Burglary, Earthquake):**

| Burglary | Earthquake | P(Alarm = T) |
|:--------:|:----------:|:------------:|
| T | T | 0.95 |
| T | F | 0.94 |
| F | T | 0.29 |
| F | F | 0.001 |

**JohnCalls (parent: Alarm):**

| Alarm | P(JohnCalls = T) |
|:-----:|:----------------:|
| T | 0.90 |
| F | 0.05 |

**MaryCalls (parent: Alarm):**

| Alarm | P(MaryCalls = T) |
|:-----:|:----------------:|
| T | 0.70 |
| F | 0.01 |

#### Solved Problem 5 ⭐

**Soal:** Berapa total parameter independen dalam Alarm Network? Bandingkan dengan full joint distribution!

**Penyelesaian:**

*Step 1:* Hitung parameter per node
- Burglary: 1 parameter (root Boolean)
- Earthquake: 1 parameter (root Boolean)
- Alarm: $2^2 = 4$ parameter (2 parent Boolean)
- JohnCalls: $2^1 = 2$ parameter (1 parent Boolean)
- MaryCalls: $2^1 = 2$ parameter (1 parent Boolean)

*Step 2:* Total parameter jaringan Bayesian
$$1 + 1 + 4 + 2 + 2 = 10 \text{ parameter}$$

*Step 3:* Bandingkan dengan full joint distribution
- 5 variabel Boolean: $2^5 - 1 = 31$ parameter

| Representasi | Parameter |
|:------------:|:---------:|
| Full Joint | 31 |
| Bayesian Network | 10 |

**Jawaban:** Alarm Network memerlukan 10 parameter, dibanding 31 untuk full joint distribution — pengurangan sekitar 68%.

---

## 3. Semantik Jaringan Bayesian

### 3.1 Representasi Joint Distribution

> Jaringan Bayesian merepresentasikan full joint distribution melalui **chain rule** berdasarkan struktur graf:
>
> $$P(x_1, x_2, ..., x_n) = \prod_{i=1}^{n} P(x_i | Parents(X_i))$$

Ini berarti probabilitas gabungan dapat dihitung sebagai **produk dari semua CPT** dengan nilai yang sesuai.

**Contoh untuk Alarm Network:**

$$P(b, e, a, j, m) = P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot P(m|a)$$

dimana huruf kecil menunjukkan nilai spesifik dari variabel.

#### Solved Problem 6 ⭐⭐

**Soal:** Hitung $P(b, \neg e, a, j, m)$ menggunakan Alarm Network — yaitu probabilitas terjadi pencurian, tidak ada gempa, alarm berbunyi, John menelepon, dan Mary menelepon!

**Penyelesaian:**

*Step 1:* Tulis dekomposisi chain rule
$$P(b, \neg e, a, j, m) = P(b) \cdot P(\neg e) \cdot P(a|b, \neg e) \cdot P(j|a) \cdot P(m|a)$$

*Step 2:* Substitusi nilai dari CPT
- $P(b) = 0.001$
- $P(\neg e) = 1 - 0.002 = 0.998$
- $P(a|b, \neg e) = 0.94$
- $P(j|a) = 0.90$
- $P(m|a) = 0.70$

*Step 3:* Hitung produk
$$P(b, \neg e, a, j, m) = 0.001 \times 0.998 \times 0.94 \times 0.90 \times 0.70$$
$$= 0.001 \times 0.998 \times 0.94 \times 0.63$$
$$= 0.001 \times 0.998 \times 0.5922$$
$$= 0.001 \times 0.59102$$
$$\approx 0.000591$$

**Jawaban:** $P(b, \neg e, a, j, m) \approx 0.000591$ atau sekitar 0.059%.

#### Solved Problem 7 ⭐⭐

**Soal:** Verifikasi bahwa semua entri dalam full joint distribution dari Alarm Network berjumlah 1. Hitunglah $P(b, e, a, j, m)$ dan $P(b, e, a, j, \neg m)$ kemudian jelaskan hubungannya!

**Penyelesaian:**

*Step 1:* Hitung $P(b, e, a, j, m)$
$$= P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot P(m|a)$$
$$= 0.001 \times 0.002 \times 0.95 \times 0.90 \times 0.70$$
$$= 0.001 \times 0.002 \times 0.5985$$
$$= 0.000001197$$

*Step 2:* Hitung $P(b, e, a, j, \neg m)$
$$= P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot P(\neg m|a)$$
$$= 0.001 \times 0.002 \times 0.95 \times 0.90 \times 0.30$$
$$= 0.001 \times 0.002 \times 0.2565$$
$$= 0.000000513$$

*Step 3:* Jelaskan hubungan
$$P(b, e, a, j, m) + P(b, e, a, j, \neg m) = P(b, e, a, j)$$
$$= 0.000001197 + 0.000000513 = 0.00000171$$

Ini sesuai karena Mary menelepon atau tidak menelepon, sehingga:
$$P(b, e, a, j) = P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot [P(m|a) + P(\neg m|a)]$$
$$= 0.001 \times 0.002 \times 0.95 \times 0.90 \times 1.0 = 0.00000171$$

**Jawaban:** Kedua entri berjumlah $P(b, e, a, j) = 0.00000171$. Ini menunjukkan bahwa distribusi dari jaringan Bayesian memenuhi sifat probabilitas yang valid ($P(m|a) + P(\neg m|a) = 1$).

---

### 3.2 Konstruksi Jaringan Bayesian

Untuk membangun jaringan Bayesian, ikuti langkah-langkah berikut:

> **Prosedur Konstruksi Jaringan Bayesian:**
> 1. Tentukan variabel-variabel yang relevan
> 2. Tentukan urutan variabel (idealnya urutan kausal: sebab sebelum akibat)
> 3. Untuk setiap variabel $X_i$ (sesuai urutan):
>    - Pilih parent dari variabel-variabel sebelumnya sehingga $P(X_i | Parents(X_i))$ valid
>    - Tambahkan edge dari setiap parent ke $X_i$
>    - Isi CPT: $P(X_i | Parents(X_i))$

**Prinsip penting:** Urutan variabel yang **sesuai kausal** (sebab sebelum akibat) menghasilkan jaringan yang **lebih compact** (lebih sedikit edge).

#### Solved Problem 8 ⭐⭐

**Soal:** Bangun jaringan Bayesian untuk skenario berikut: Sistem radar TNI mendeteksi objek di udara. Faktor-faktor yang relevan:
- Cuaca buruk dapat menyebabkan false alarm pada radar
- Pesawat musuh dapat memasuki wilayah udara
- Radar mendeteksi objek (dipengaruhi cuaca dan keberadaan pesawat)
- Operator membunyikan sirene (berdasarkan deteksi radar)
- Interceptor scramble (berdasarkan sirene)

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- $C$: CuacaBuruk (Boolean)
- $P$: PesawatMusuh (Boolean)
- $R$: RadarDeteksi (Boolean)
- $S$: Sirene (Boolean)
- $I$: InterceptorScramble (Boolean)

*Step 2:* Tentukan urutan kausal
Sebab → Akibat: Cuaca dan PesawatMusuh → RadarDeteksi → Sirene → InterceptorScramble

*Step 3:* Tentukan parent untuk setiap variabel
- CuacaBuruk: tidak ada parent (root)
- PesawatMusuh: tidak ada parent (root)
- RadarDeteksi: parent = {CuacaBuruk, PesawatMusuh}
- Sirene: parent = {RadarDeteksi}
- InterceptorScramble: parent = {Sirene}

*Step 4:* Tentukan CPT (contoh nilai)

| Variabel | CPT |
|----------|-----|
| $P(C = T)$ | 0.15 |
| $P(P = T)$ | 0.005 |

| CuacaBuruk | PesawatMusuh | P(RadarDeteksi = T) |
|:----------:|:------------:|:-------------------:|
| T | T | 0.85 |
| T | F | 0.20 |
| F | T | 0.95 |
| F | F | 0.01 |

| RadarDeteksi | P(Sirene = T) |
|:------------:|:-------------:|
| T | 0.90 |
| F | 0.02 |

| Sirene | P(InterceptorScramble = T) |
|:------:|:--------------------------:|
| T | 0.95 |
| F | 0.01 |

**Jawaban:** Jaringan memiliki struktur: $C \rightarrow R \leftarrow P$, $R \rightarrow S \rightarrow I$. Total parameter: $1 + 1 + 4 + 2 + 2 = 10$ parameter. Struktur ini menunjukkan bahwa cuaca buruk dan pesawat musuh secara independen mempengaruhi deteksi radar, yang kemudian secara kausal memicu sirene dan scramble interceptor.

---

### 3.3 Pengaruh Urutan Variabel

Urutan variabel saat membangun jaringan Bayesian mempengaruhi jumlah edge dan parameter.

#### Solved Problem 9 ⭐⭐

**Soal:** Diberikan tiga variabel: Hujan (H), Tabrakan (T), dan Macet (M). Hubungan kausal: Hujan → Macet, Tabrakan → Macet. Bandingkan jaringan yang dihasilkan dari urutan (H, T, M) vs (M, H, T)!

**Penyelesaian:**

*Step 1:* Urutan kausal (H, T, M)
- H: tidak ada parent → $P(H)$
- T: independen dari H → tidak ada parent → $P(T)$
- M: bergantung pada H dan T → parent = {H, T} → $P(M|H,T)$

Struktur: $H \rightarrow M \leftarrow T$ (3 node, 2 edge, 1+1+4=6 parameter)

*Step 2:* Urutan terbalik (M, H, T)
- M: tidak ada variabel sebelumnya → $P(M)$
- H: bergantung pada M (Macet bisa karena hujan) → parent = {M} → $P(H|M)$
- T: bergantung pada M dan H → parent = {M, H} → $P(T|M,H)$

Struktur: $M \rightarrow H$, $M \rightarrow T$, $H \rightarrow T$ (3 node, 3 edge, 1+2+4=7 parameter)

*Step 3:* Bandingkan

| Urutan | Edge | Parameter |
|:------:|:----:|:---------:|
| Kausal (H, T, M) | 2 | 6 |
| Terbalik (M, H, T) | 3 | 7 |

**Jawaban:** Urutan kausal menghasilkan jaringan lebih compact (2 edge, 6 parameter) dibanding urutan terbalik (3 edge, 7 parameter). Ini menunjukkan pentingnya mengikuti urutan kausal dalam konstruksi jaringan Bayesian.

---

## 4. Conditional Independence dalam Jaringan Bayesian

### 4.1 Asumsi Independensi Lokal

> **Asumsi Independensi Lokal (Local Markov Property):** Setiap node dalam jaringan Bayesian bersifat **conditionally independent** dari semua non-descendant-nya, diberikan parent-nya.

Secara formal:
$$X_i \perp NonDescendants(X_i) \mid Parents(X_i)$$

Ini berarti: setelah kita mengetahui nilai parent dari suatu node, informasi tentang non-descendant tidak mengubah distribusi probabilitas node tersebut.

#### Solved Problem 10 ⭐

**Soal:** Dalam Alarm Network (Burglary → Alarm ← Earthquake, Alarm → JohnCalls, Alarm → MaryCalls), tentukan conditional independence berikut berdasarkan Local Markov Property:
(a) Apakah JohnCalls independen dari Earthquake diberikan Alarm?
(b) Apakah JohnCalls independen dari MaryCalls diberikan Alarm?

**Penyelesaian:**

*Step 1:* Analisis (a)
- JohnCalls memiliki parent = {Alarm}
- Earthquake bukan descendant dari JohnCalls
- Berdasarkan Local Markov Property: **JohnCalls ⊥ Earthquake | Alarm** ✅

*Step 2:* Analisis (b)
- JohnCalls memiliki parent = {Alarm}
- MaryCalls bukan descendant dari JohnCalls
- Berdasarkan Local Markov Property: **JohnCalls ⊥ MaryCalls | Alarm** ✅

**Jawaban:** Ya untuk keduanya. Jika kita sudah mengetahui apakah alarm berbunyi atau tidak, mengetahui apakah ada gempa atau apakah Mary menelepon tidak mengubah probabilitas John menelepon.

---

### 4.2 Tiga Pola Koneksi Fundamental

Ada tiga pola koneksi dasar dalam jaringan Bayesian yang menentukan aliran informasi:

![Tiga Pola Koneksi](images/p12-03-three-connection-patterns.png)

*Gambar 12.3: Tiga pola koneksi fundamental dalam jaringan Bayesian*

#### Pola 1: Rantai (Chain) — A → B → C

| Kondisi | A dan C independen? |
|---------|:-------------------:|
| B **tidak** diobservasi | ❌ Dependen |
| B **diobservasi** | ✅ Independen |

**Contoh:** Pesawat Musuh → Deteksi Radar → Sirene. Jika kita sudah tahu radar mendeteksi, mengetahui ada pesawat musuh tidak menambah informasi tentang sirene.

#### Pola 2: Penyebab Bersama (Common Cause/Fork) — A ← B → C

| Kondisi | A dan C independen? |
|---------|:-------------------:|
| B **tidak** diobservasi | ❌ Dependen |
| B **diobservasi** | ✅ Independen |

**Contoh:** Macet ← Hujan → Banjir. Jika kita sudah tahu hujan atau tidak, informasi tentang macet tidak mengubah probabilitas banjir.

#### Pola 3: Efek Bersama (Common Effect/Collider/V-structure) — A → B ← C

| Kondisi | A dan C independen? |
|---------|:-------------------:|
| B **tidak** diobservasi | ✅ Independen |
| B **diobservasi** | ❌ Dependen |

**Contoh:** Pencurian → Alarm ← Gempa. Tanpa informasi tentang alarm, pencurian dan gempa independen. Namun jika alarm berbunyi, mengetahui ada gempa membuat pencurian lebih tidak mungkin ("explaining away").

> **Explaining Away:** Fenomena di mana mengetahui satu penyebab dari suatu efek yang diamati **mengurangi** probabilitas penyebab lain. Ini unik pada V-structure.

#### Solved Problem 11 ⭐⭐

**Soal:** Dalam sistem pertahanan udara, diberikan jaringan: JammingMusuh → RadarGagal ← KerusakanHardware. Alarm berbunyi jika radar gagal. Jelaskan fenomena "explaining away" dalam konteks ini!

**Penyelesaian:**

*Step 1:* Identifikasi pola
- JammingMusuh → RadarGagal ← KerusakanHardware
- Ini adalah pola **V-structure** (common effect)

*Step 2:* Analisis tanpa observasi pada RadarGagal
- Tanpa informasi tentang apakah radar gagal, JammingMusuh dan KerusakanHardware independen
- $P(\text{Jamming} | \text{Kerusakan}) = P(\text{Jamming})$

*Step 3:* Analisis dengan RadarGagal = True
- Jika kita tahu radar gagal, ada dua kemungkinan penyebab: jamming atau kerusakan
- Jika kemudian kita mengetahui ada kerusakan hardware, maka:
$$P(\text{Jamming} | \text{RadarGagal}, \text{Kerusakan}) < P(\text{Jamming} | \text{RadarGagal})$$

*Step 4:* Jelaskan explaining away

Ketika radar gagal dan kita mengetahui hardware rusak, kerusakan sudah **menjelaskan** (explain away) kegagalan radar. Sehingga probabilitas bahwa kegagalan disebabkan jamming musuh **berkurang**.

**Jawaban:** Jika radar gagal, awalnya ada dua kemungkinan penyebab (jamming atau kerusakan hardware). Jika kemudian ditemukan bahwa hardware memang rusak, maka kegagalan radar sudah "terjelaskan" oleh kerusakan, sehingga probabilitas bahwa musuh melakukan jamming menurun. Ini adalah fenomena explaining away.

#### Solved Problem 12 ⭐

**Soal:** Identifikasi pola koneksi untuk setiap triple berikut dan tentukan apakah node ujung independen atau dependen:
(a) Hujan → Banjir → Evakuasi (Banjir tidak diobservasi)
(b) Sensor1 ← Target → Sensor2 (Target diobservasi)
(c) Jamming → AlarmRadar ← Kerusakan (AlarmRadar diobservasi)

**Penyelesaian:**

| Triple | Pola | Observasi | A dan C |
|:------:|:----:|:---------:|:-------:|
| (a) Hujan → Banjir → Evakuasi | Chain | B tidak diobservasi | **Dependen** |
| (b) Sensor1 ← Target → Sensor2 | Common Cause | B diobservasi | **Independen** |
| (c) Jamming → AlarmRadar ← Kerusakan | V-structure | B diobservasi | **Dependen** |

**Jawaban:** (a) Dependen — informasi mengalir melalui chain. (b) Independen — jika target diketahui, kedua sensor independen. (c) Dependen — observasi pada common effect mengaktifkan dependensi (explaining away).

---

## 5. D-Separation

### 5.1 Definisi D-Separation

> **D-Separation (Directional Separation)** adalah kriteria grafis untuk menentukan apakah dua set variabel bersifat conditionally independent diberikan set variabel ketiga dalam jaringan Bayesian.

Secara formal:
> Variabel $X$ dan $Y$ bersifat **d-separated** oleh set variabel $Z$ jika **setiap undirected path** antara $X$ dan $Y$ **terblokir** oleh $Z$.

Sebuah path terblokir oleh $Z$ jika memenuhi salah satu kondisi berikut pada suatu node $N$ di path:

| Pola di Node N | Kondisi Terblokir |
|:---------------:|:-----------------:|
| Chain: → N → | N ∈ Z (N diobservasi) |
| Fork: ← N → | N ∈ Z (N diobservasi) |
| Collider: → N ← | N ∉ Z DAN tidak ada descendant N di Z |

> **Aturan penting untuk collider:** Path melalui collider terblokir KECUALI collider (atau descendant-nya) berada dalam set conditioning $Z$.

#### Solved Problem 13 ⭐⭐

**Soal:** Diberikan jaringan Bayesian:
- A → C
- B → C
- C → D
- C → E

Tentukan apakah pasangan variabel berikut d-separated:
(a) A dan B diberikan {} (tanpa observasi)
(b) A dan B diberikan {C}
(c) D dan E diberikan {C}
(d) A dan E diberikan {}

**Penyelesaian:**

*Step 1:* Analisis (a) — A dan B | {}
- Path: A → C ← B
- Node C adalah collider
- C tidak di {} dan tidak ada descendant C di {}
- Path **terblokir**
- **A ⊥ B | {}** ✅ (d-separated)

*Step 2:* Analisis (b) — A dan B | {C}
- Path: A → C ← B
- Node C adalah collider
- C ∈ {C} → path menjadi **aktif**
- **A ⊥̸ B | {C}** ❌ (tidak d-separated, explaining away!)

*Step 3:* Analisis (c) — D dan E | {C}
- Path: D ← C → E
- Node C adalah common cause (fork)
- C ∈ {C} → path **terblokir**
- **D ⊥ E | {C}** ✅ (d-separated)

*Step 4:* Analisis (d) — A dan E | {}
- Path: A → C → E
- Node C adalah chain node
- C tidak di {} → path **aktif**
- **A ⊥̸ E | {}** ❌ (tidak d-separated)

**Jawaban:** (a) D-separated ✅, (b) Tidak d-separated ❌, (c) D-separated ✅, (d) Tidak d-separated ❌.

#### Solved Problem 14 ⭐⭐⭐

**Soal:** Diberikan jaringan Bayesian kompleks untuk sistem Command and Control:

- IntelMusuh (I) → AncamanUdara (A)
- Cuaca (C) → AncamanUdara (A)
- AncamanUdara (A) → DeteksiRadar (D)
- AncamanUdara (A) → PerintahKomandan (P)
- DeteksiRadar (D) → SistemAlarm (S)
- PerintahKomandan (P) → ScrambleJet (J)
- SistemAlarm (S) → ScrambleJet (J)

Tentukan:
(a) Apakah IntelMusuh dan Cuaca d-separated diberikan {AncamanUdara}?
(b) Apakah DeteksiRadar dan PerintahKomandan d-separated diberikan {AncamanUdara}?
(c) Apakah IntelMusuh dan ScrambleJet d-separated diberikan {AncamanUdara, SistemAlarm}?

**Penyelesaian:**

*Step 1:* Analisis (a) — I dan C | {A}
- Path: I → A ← C
- A adalah collider, A ∈ {A} → path **aktif**
- **I ⊥̸ C | {A}** ❌ (explaining away: jika ancaman tinggi dan cuaca baik, maka intelijen musuh lebih mungkin benar)

*Step 2:* Analisis (b) — D dan P | {A}
- Path: D ← A → P
- A adalah common cause (fork), A ∈ {A} → path **terblokir**
- **D ⊥ P | {A}** ✅ (jika kita tahu level ancaman, deteksi radar dan perintah komandan independen)

*Step 3:* Analisis (c) — I dan J | {A, S}
- Path 1: I → A → D → S → J — A ∈ {A}, chain di A, **terblokir** ✅
- Path 2: I → A → P → J — A ∈ {A}, chain di A, **terblokir** ✅
- Semua path terblokir
- **I ⊥ J | {A, S}** ✅

**Jawaban:** (a) Tidak d-separated — explaining away terjadi saat observasi pada common effect AncamanUdara. (b) D-separated — DeteksiRadar dan PerintahKomandan independen jika kita sudah mengetahui level AncamanUdara. (c) D-separated — semua path dari IntelMusuh ke ScrambleJet terblokir.

---

### 5.2 Markov Blanket

> **Markov Blanket** dari sebuah node $X$ adalah set minimal node yang membuat $X$ conditionally independent dari semua node lain dalam jaringan. Markov Blanket terdiri dari:
> 1. **Parent** dari $X$
> 2. **Children** dari $X$
> 3. **Co-parent** dari children $X$ (parent lain dari children X)

#### Solved Problem 15 ⭐

**Soal:** Dalam Alarm Network, tentukan Markov Blanket dari node Alarm!

**Penyelesaian:**

*Step 1:* Identifikasi parent dari Alarm
- Parents: {Burglary, Earthquake}

*Step 2:* Identifikasi children dari Alarm
- Children: {JohnCalls, MaryCalls}

*Step 3:* Identifikasi co-parent dari children
- JohnCalls parent: {Alarm} — tidak ada co-parent selain Alarm
- MaryCalls parent: {Alarm} — tidak ada co-parent selain Alarm

*Step 4:* Gabungkan

$$MB(Alarm) = \{Burglary, Earthquake, JohnCalls, MaryCalls\}$$

**Jawaban:** Markov Blanket dari Alarm adalah {Burglary, Earthquake, JohnCalls, MaryCalls} — yaitu seluruh node lain dalam jaringan kecil ini. Dengan mengetahui nilai keempat node ini, Alarm independen dari variabel lain.

---

## 6. Inferensi pada Jaringan Bayesian

### 6.1 Jenis-Jenis Query Inferensi

> **Inferensi** pada jaringan Bayesian adalah proses menghitung probabilitas variabel tertentu diberikan observasi (evidence) pada variabel lain.

Jenis query umum:

| Jenis Query | Notasi | Deskripsi |
|-------------|--------|-----------|
| **Posterior probability** | $P(X \mid e)$ | Probabilitas X diberikan evidence e |
| **Most probable explanation** | $\arg\max_x P(x \mid e)$ | Nilai X yang paling mungkin |
| **Joint probability** | $P(X, Y \mid e)$ | Distribusi gabungan X dan Y diberikan e |

**Contoh query pada Alarm Network:**
- $P(Burglary \mid JohnCalls = true, MaryCalls = true)$ — Berapa probabilitas pencurian jika John dan Mary menelepon?

### 6.2 Inferensi dengan Enumeration

> **Inference by Enumeration** menghitung posterior probability dengan menjumlahkan (marginalisasi) semua variabel yang tidak relevan (hidden variables) dari joint distribution.

$$P(X \mid e) = \alpha \sum_{y} P(X, e, y)$$

dimana:
- $X$ = query variable
- $e$ = evidence variables (diketahui nilainya)
- $y$ = hidden variables (tidak diketahui, perlu dijumlahkan)
- $\alpha$ = konstanta normalisasi sehingga probabilitas berjumlah 1

#### Solved Problem 16 ⭐⭐⭐

**Soal:** Gunakan Alarm Network untuk menghitung $P(Burglary \mid JohnCalls = true, MaryCalls = true)$!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- Query: Burglary (B)
- Evidence: JohnCalls = true (j), MaryCalls = true (m)
- Hidden: Earthquake (E), Alarm (A)

*Step 2:* Tulis rumus

$$P(B \mid j, m) = \alpha \sum_{e} \sum_{a} P(B, e, a, j, m)$$
$$= \alpha \sum_{e} \sum_{a} P(B) \cdot P(e) \cdot P(a|B,e) \cdot P(j|a) \cdot P(m|a)$$

*Step 3:* Hitung untuk B = true

$$P(b, j, m) = \sum_{e} \sum_{a} P(b) \cdot P(e) \cdot P(a|b,e) \cdot P(j|a) \cdot P(m|a)$$

Enumerasi 4 kombinasi (e, a):

| e | a | $P(b)$ | $P(e)$ | $P(a\|b,e)$ | $P(j\|a)$ | $P(m\|a)$ | Produk |
|:-:|:-:|:------:|:------:|:----------:|:--------:|:--------:|:------:|
| T | T | 0.001 | 0.002 | 0.95 | 0.90 | 0.70 | 0.001×0.002×0.95×0.90×0.70 = 1.197×10⁻⁶ |
| T | F | 0.001 | 0.002 | 0.05 | 0.05 | 0.01 | 0.001×0.002×0.05×0.05×0.01 = 5.0×10⁻¹¹ |
| F | T | 0.001 | 0.998 | 0.94 | 0.90 | 0.70 | 0.001×0.998×0.94×0.90×0.70 = 5.909×10⁻⁴ |
| F | F | 0.001 | 0.998 | 0.06 | 0.05 | 0.01 | 0.001×0.998×0.06×0.05×0.01 = 2.994×10⁻⁸ |

$$P(b, j, m) = 1.197 \times 10^{-6} + 5.0 \times 10^{-11} + 5.909 \times 10^{-4} + 2.994 \times 10^{-8}$$
$$\approx 5.922 \times 10^{-4}$$

*Step 4:* Hitung untuk B = false

| e | a | $P(\neg b)$ | $P(e)$ | $P(a\|\neg b,e)$ | $P(j\|a)$ | $P(m\|a)$ | Produk |
|:-:|:-:|:-----------:|:------:|:----------------:|:--------:|:--------:|:------:|
| T | T | 0.999 | 0.002 | 0.29 | 0.90 | 0.70 | 0.999×0.002×0.29×0.90×0.70 = 3.653×10⁻⁴ |
| T | F | 0.999 | 0.002 | 0.71 | 0.05 | 0.01 | 0.999×0.002×0.71×0.05×0.01 = 7.093×10⁻⁷ |
| F | T | 0.999 | 0.998 | 0.001 | 0.90 | 0.70 | 0.999×0.998×0.001×0.90×0.70 = 6.281×10⁻⁴ |
| F | F | 0.999 | 0.998 | 0.999 | 0.05 | 0.01 | 0.999×0.998×0.999×0.05×0.01 = 4.985×10⁻⁴ |

$$P(\neg b, j, m) = 3.653 \times 10^{-4} + 7.093 \times 10^{-7} + 6.281 \times 10^{-4} + 4.985 \times 10^{-4}$$
$$\approx 1.492 \times 10^{-3}$$

*Step 5:* Normalisasi

$$\alpha = \frac{1}{P(b, j, m) + P(\neg b, j, m)} = \frac{1}{5.922 \times 10^{-4} + 1.492 \times 10^{-3}} = \frac{1}{2.084 \times 10^{-3}}$$

$$P(B=true \mid j, m) = \alpha \times 5.922 \times 10^{-4} = \frac{5.922 \times 10^{-4}}{2.084 \times 10^{-3}} \approx 0.284$$

$$P(B=false \mid j, m) = \alpha \times 1.492 \times 10^{-3} = \frac{1.492 \times 10^{-3}}{2.084 \times 10^{-3}} \approx 0.716$$

**Jawaban:** $P(Burglary = true \mid JohnCalls, MaryCalls) \approx 0.284$ (28.4%). Meskipun kedua tetangga menelepon, probabilitas pencurian "hanya" 28.4% karena probabilitas prior pencurian sangat rendah (0.001) dan ada kemungkinan penyebab lain (gempa, false alarm).

---

### 6.3 Variable Elimination

Inference by enumeration tidak efisien karena menghitung ulang sub-ekspresi yang sama berkali-kali. **Variable Elimination** mengatasi ini dengan:

> **Variable Elimination** adalah algoritma inferensi eksak yang menghitung posterior probability dengan mengeliminasi (menjumlahkan) variabel tersembunyi satu per satu, menyimpan hasil antara sebagai **faktor**.

**Konsep Faktor:**
> **Faktor** adalah tabel yang merepresentasikan fungsi dari satu atau lebih variabel. Faktor dapat berupa CPT, evidence, atau hasil operasi antar faktor.

**Operasi pada faktor:**
1. **Pointwise product**: Mengalikan dua faktor
2. **Summing out (marginalisasi)**: Menjumlahkan faktor terhadap suatu variabel

#### Solved Problem 17 ⭐⭐

**Soal:** Diberikan jaringan sederhana A → B → C dengan:
- P(A=T) = 0.3
- P(B=T|A=T) = 0.8, P(B=T|A=F) = 0.4
- P(C=T|B=T) = 0.9, P(C=T|B=F) = 0.2

Gunakan Variable Elimination untuk menghitung P(A | C=T)!

**Penyelesaian:**

*Step 1:* Identifikasi faktor awal
- $f_1(A) = P(A)$
- $f_2(A, B) = P(B|A)$
- $f_3(B, C) = P(C|B)$

Query: P(A | C=T), Hidden: B

*Step 2:* Masukkan evidence C=T ke $f_3$

$f_3'(B) = f_3(B, C=T)$:

| B | $f_3'(B)$ |
|:-:|:---------:|
| T | 0.9 |
| F | 0.2 |

*Step 3:* Eliminasi B — kalikan $f_2$ dan $f_3'$, lalu jumlahkan atas B

$f_4(A, B) = f_2(A, B) \times f_3'(B)$:

| A | B | $f_2(A,B)$ | $f_3'(B)$ | $f_4(A,B)$ |
|:-:|:-:|:----------:|:---------:|:-----------:|
| T | T | 0.8 | 0.9 | 0.72 |
| T | F | 0.2 | 0.2 | 0.04 |
| F | T | 0.4 | 0.9 | 0.36 |
| F | F | 0.6 | 0.2 | 0.12 |

$f_5(A) = \sum_B f_4(A, B)$:

| A | $f_5(A)$ |
|:-:|:--------:|
| T | 0.72 + 0.04 = 0.76 |
| F | 0.36 + 0.12 = 0.48 |

*Step 4:* Kalikan dengan $f_1$ dan normalisasi

$f_6(A) = f_1(A) \times f_5(A)$:

| A | $f_1(A)$ | $f_5(A)$ | $f_6(A)$ |
|:-:|:--------:|:--------:|:--------:|
| T | 0.3 | 0.76 | 0.228 |
| F | 0.7 | 0.48 | 0.336 |

Normalisasi: $\alpha = 1/(0.228 + 0.336) = 1/0.564$

$$P(A=T | C=T) = 0.228/0.564 \approx 0.404$$
$$P(A=F | C=T) = 0.336/0.564 \approx 0.596$$

**Jawaban:** $P(A=T | C=T) \approx 0.404$. Mengetahui C=true meningkatkan probabilitas A=true dari 0.3 (prior) menjadi 0.404 (posterior).

#### Solved Problem 18 ⭐⭐⭐

**Soal:** Sistem deteksi intrusi jaringan militer memiliki jaringan Bayesian berikut:
- SeranganSiber (S): P(S=T) = 0.02
- AnomaliBandwidth (B): P(B=T|S=T) = 0.90, P(B=T|S=F) = 0.05
- PortScanDeteksi (P): P(P=T|S=T) = 0.85, P(P=T|S=F) = 0.03
- AlertSistem (A): P(A=T|B=T,P=T) = 0.99, P(A=T|B=T,P=F) = 0.80, P(A=T|B=F,P=T) = 0.75, P(A=T|B=F,P=F) = 0.01

Struktur: S → B, S → P, B → A ← P

Diberikan AlertSistem = true, hitung P(SeranganSiber = true | AlertSistem = true)!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- Query: S, Evidence: A=T, Hidden: B, P

*Step 2:* Faktor awal
- $f_1(S) = P(S)$
- $f_2(S,B) = P(B|S)$
- $f_3(S,P) = P(P|S)$
- $f_4(B,P,A) = P(A|B,P)$

*Step 3:* Masukkan evidence A=T

$f_4'(B,P) = P(A=T|B,P)$:

| B | P | $f_4'(B,P)$ |
|:-:|:-:|:-----------:|
| T | T | 0.99 |
| T | F | 0.80 |
| F | T | 0.75 |
| F | F | 0.01 |

*Step 4:* Eliminasi B — kalikan $f_2$ dan $f_4'$, jumlahkan atas B

$f_5(S, B, P) = f_2(S,B) \times f_4'(B,P)$, lalu $f_6(S,P) = \sum_B f_5$

Untuk S=T:

| B | P | $f_2(T,B)$ | $f_4'(B,P)$ | Produk |
|:-:|:-:|:----------:|:-----------:|:------:|
| T | T | 0.90 | 0.99 | 0.891 |
| T | F | 0.90 | 0.80 | 0.720 |
| F | T | 0.10 | 0.75 | 0.075 |
| F | F | 0.10 | 0.01 | 0.001 |

$f_6(S=T, P=T) = 0.891 + 0.075 = 0.966$
$f_6(S=T, P=F) = 0.720 + 0.001 = 0.721$

Untuk S=F:

| B | P | $f_2(F,B)$ | $f_4'(B,P)$ | Produk |
|:-:|:-:|:----------:|:-----------:|:------:|
| T | T | 0.05 | 0.99 | 0.0495 |
| T | F | 0.05 | 0.80 | 0.040 |
| F | T | 0.95 | 0.75 | 0.7125 |
| F | F | 0.95 | 0.01 | 0.0095 |

$f_6(S=F, P=T) = 0.0495 + 0.7125 = 0.762$
$f_6(S=F, P=F) = 0.040 + 0.0095 = 0.0495$

*Step 5:* Eliminasi P — kalikan $f_3$ dan $f_6$, jumlahkan atas P

$f_7(S) = \sum_P f_3(S,P) \times f_6(S,P)$

Untuk S=T:
$$f_7(T) = P(P=T|S=T) \times f_6(T,T) + P(P=F|S=T) \times f_6(T,F)$$
$$= 0.85 \times 0.966 + 0.15 \times 0.721 = 0.8211 + 0.1082 = 0.9293$$

Untuk S=F:
$$f_7(F) = P(P=T|S=F) \times f_6(F,T) + P(P=F|S=F) \times f_6(F,F)$$
$$= 0.03 \times 0.762 + 0.97 \times 0.0495 = 0.02286 + 0.04802 = 0.07088$$

*Step 6:* Kalikan dengan prior dan normalisasi

$f_8(S) = f_1(S) \times f_7(S)$:

| S | $f_1(S)$ | $f_7(S)$ | $f_8(S)$ |
|:-:|:--------:|:--------:|:--------:|
| T | 0.02 | 0.9293 | 0.01859 |
| F | 0.98 | 0.07088 | 0.06946 |

$$P(S=T|A=T) = \frac{0.01859}{0.01859 + 0.06946} = \frac{0.01859}{0.08805} \approx 0.211$$

**Jawaban:** $P(\text{SeranganSiber}=true | \text{AlertSistem}=true) \approx 0.211$ (21.1%). Alert pada sistem meningkatkan probabilitas serangan siber dari 2% (prior) menjadi 21.1% (posterior). Meskipun angka ini signifikan, mayoritas alert masih bukan serangan nyata (78.9%), yang menunjukkan pentingnya evidence tambahan sebelum mengambil tindakan.

---

### 6.4 Kompleksitas Inferensi

| Metode | Kompleksitas Waktu | Keterangan |
|--------|:------------------:|------------|
| Enumeration | $O(n \cdot 2^n)$ | Eksponensial dalam jumlah variabel |
| Variable Elimination | $O(n \cdot 2^w)$ | $w$ = lebar pohon (treewidth) |
| Inferensi Eksak (umum) | NP-hard | Pada jaringan umum |

> **Treewidth** adalah ukuran seberapa "mirip pohon" suatu jaringan. Jaringan dengan treewidth rendah memungkinkan inferensi yang lebih efisien.

#### Solved Problem 19 ⭐

**Soal:** Mengapa inferensi pada jaringan Bayesian berbentuk pohon (tree-structured) lebih efisien? Berapa treewidth-nya?

**Penyelesaian:**

*Step 1:* Definisikan tree-structured network
- Setiap node memiliki paling banyak 1 parent
- Tidak ada node dengan 2+ parent

*Step 2:* Analisis treewidth
- Treewidth dari tree-structured network = 1
- Ini berarti kompleksitas Variable Elimination = $O(n \cdot 2^1) = O(n)$

*Step 3:* Bandingkan

| Struktur | Treewidth | Kompleksitas VE |
|----------|:---------:|:---------------:|
| Tree | 1 | O(n) - Linear |
| Singly-connected | 1 | O(n) - Linear |
| Multiply-connected | > 1 | Bisa eksponensial |

**Jawaban:** Jaringan pohon memiliki treewidth = 1, sehingga Variable Elimination berjalan dalam waktu **linear** $O(n)$. Ini karena setiap langkah eliminasi hanya melibatkan faktor dengan 2 variabel, tanpa membuat faktor besar.

---

## 7. Membangun Jaringan Bayesian dari Domain

### 7.1 Panduan Konstruksi

Membangun jaringan Bayesian untuk domain nyata memerlukan:

1. **Identifikasi variabel relevan** — apa saja yang ingin dimodelkan?
2. **Tentukan hubungan kausal** — variabel mana yang secara kausal mempengaruhi variabel lain?
3. **Buat topologi (DAG)** — gambar graf dengan arah kausal
4. **Tentukan CPT** — dari data, ahli domain, atau literatur
5. **Validasi** — apakah independensi yang tersirat masuk akal?

#### Solved Problem 20 ⭐⭐

**Soal:** Seorang analis intelijen ingin membangun jaringan Bayesian untuk menilai kemungkinan serangan teroris di fasilitas militer. Variabel yang relevan:
- Chatter di media sosial meningkat
- Pergerakan mencurigakan terdeteksi
- Level ancaman meningkat
- Keamanan ditingkatkan
- Serangan terjadi

Bangun jaringan Bayesian dengan topologi kausal yang tepat!

**Penyelesaian:**

*Step 1:* Identifikasi variabel
- $C$: ChatterMeningkat (Boolean)
- $P$: PergerakanMencurigakan (Boolean)
- $L$: LevelAncaman (Boolean — tinggi atau rendah)
- $K$: KeamananDitingkatkan (Boolean)
- $S$: SeranganTerjadi (Boolean)

*Step 2:* Tentukan hubungan kausal
- Chatter dan pergerakan mencurigakan adalah **indikator** level ancaman
- Level ancaman mempengaruhi keputusan meningkatkan keamanan
- Level ancaman dan keamanan mempengaruhi kemungkinan serangan

*Step 3:* Buat topologi

Hubungan kausal:
- Chatter bisa disebabkan oleh level ancaman tinggi: $L \rightarrow C$
- Pergerakan mencurigakan disebabkan oleh level ancaman: $L \rightarrow P$
- Level ancaman meningkatkan keamanan: $L \rightarrow K$
- Level ancaman dan keamanan mempengaruhi serangan: $L \rightarrow S$, $K \rightarrow S$

*Step 4:* Validasi independensi
- C ⊥ P | L ✅ (jika kita tahu level ancaman, chatter dan pergerakan independen)
- C ⊥ K | L ✅ (masuk akal)
- K tidak independen dari S (keamanan mempengaruhi keberhasilan serangan)

**Jawaban:** Topologi: L → C, L → P, L → K, L → S, K → S. Level ancaman adalah "root cause" yang mempengaruhi semua indikator dan keputusan. Serangan dipengaruhi oleh level ancaman dan tingkat keamanan. Total parameter: 1 + 2 + 2 + 2 + 4 = 11.

#### Solved Problem 21 ⭐⭐⭐

**Soal:** TNI AL sedang mengembangkan sistem untuk menilai ancaman kapal selam asing. Variabel-variabel yang relevan:

1. Aktivitas sonar asing terdeteksi (SonarAsing)
2. Anomali magnetik terdeteksi (AnomaliFM)
3. Adanya kapal selam asing (KapalSelamAda)
4. Kondisi laut (KondisiLaut — mempengaruhi kualitas deteksi)
5. Alert level dinaikkan (AlertLevel)
6. Kapal perang dikirim ke area (KapalPerangDikirim)

Bangun jaringan Bayesian lengkap termasuk contoh CPT!

**Penyelesaian:**

*Step 1:* Identifikasi hubungan kausal
- KapalSelamAda dan KondisiLaut adalah variabel eksogen (root)
- SonarAsing dipengaruhi oleh KapalSelamAda dan KondisiLaut
- AnomaliFM dipengaruhi oleh KapalSelamAda dan KondisiLaut
- AlertLevel dipengaruhi oleh SonarAsing dan AnomaliFM
- KapalPerangDikirim dipengaruhi oleh AlertLevel

*Step 2:* Buat topologi
- KapalSelamAda → SonarAsing
- KondisiLaut → SonarAsing
- KapalSelamAda → AnomaliFM
- KondisiLaut → AnomaliFM
- SonarAsing → AlertLevel
- AnomaliFM → AlertLevel
- AlertLevel → KapalPerangDikirim

*Step 3:* Tentukan CPT

**Root nodes:**
- P(KapalSelamAda = T) = 0.05
- P(KondisiLaut = Buruk) = 0.30

**SonarAsing (parent: KapalSelamAda, KondisiLaut):**

| KapalSelam | KondisiLaut | P(Sonar = T) |
|:----------:|:-----------:|:------------:|
| Ada | Baik | 0.90 |
| Ada | Buruk | 0.60 |
| Tidak | Baik | 0.05 |
| Tidak | Buruk | 0.15 |

**AnomaliFM (parent: KapalSelamAda, KondisiLaut):**

| KapalSelam | KondisiLaut | P(Anomali = T) |
|:----------:|:-----------:|:--------------:|
| Ada | Baik | 0.85 |
| Ada | Buruk | 0.55 |
| Tidak | Baik | 0.03 |
| Tidak | Buruk | 0.10 |

**AlertLevel (parent: SonarAsing, AnomaliFM):**

| Sonar | Anomali | P(Alert = T) |
|:-----:|:-------:|:------------:|
| T | T | 0.95 |
| T | F | 0.60 |
| F | T | 0.55 |
| F | F | 0.02 |

**KapalPerangDikirim (parent: AlertLevel):**

| Alert | P(KapalPerang = T) |
|:-----:|:------------------:|
| T | 0.85 |
| F | 0.05 |

*Step 4:* Hitung total parameter
$$1 + 1 + 4 + 4 + 4 + 2 = 16 \text{ parameter}$$

Bandingkan: Full joint distribution = $2^6 - 1 = 63$ parameter.

**Jawaban:** Jaringan Bayesian untuk sistem deteksi kapal selam memiliki 6 node, 7 edge, dan 16 parameter (vs 63 untuk full joint). Struktur menangkap bahwa deteksi sonar dan anomali magnetik dipengaruhi secara independen oleh keberadaan kapal selam dan kondisi laut, dan bersama-sama menentukan alert level.

---

## 8. Approximate Inference (Pengenalan)

### 8.1 Mengapa Approximate Inference?

Karena inferensi eksak bersifat NP-hard pada jaringan umum, untuk jaringan besar diperlukan metode aproksimasi:

> **Approximate Inference** menggunakan teknik sampling untuk mengestimasi posterior probability, menghasilkan jawaban yang mendekati benar dengan efisiensi komputasi yang lebih baik.

Metode utama:
1. **Prior Sampling** — menghasilkan sampel dari distribusi prior
2. **Rejection Sampling** — membuang sampel yang tidak konsisten dengan evidence
3. **Likelihood Weighting** — memberi bobot pada sampel berdasarkan evidence
4. **Gibbs Sampling** — sampling berurutan dari distribusi bersyarat

### 8.2 Prior Sampling

> **Prior Sampling** menghasilkan sampel dari jaringan Bayesian dengan men-sample setiap variabel sesuai CPT-nya dalam urutan topologis.

**Prosedur:**
1. Urutkan variabel secara topologis
2. Untuk setiap variabel $X_i$: sample nilai dari $P(X_i | parents(X_i))$
3. Hasilnya adalah satu sampel lengkap $(x_1, x_2, ..., x_n)$
4. Ulangi N kali untuk mendapatkan N sampel

#### Solved Problem 22 ⭐

**Soal:** Gunakan metode prior sampling pada jaringan sederhana: Hujan (H) → Macet (M) → Terlambat (T), dengan:
- P(H=T) = 0.3
- P(M=T|H=T) = 0.8, P(M=T|H=F) = 0.2
- P(T=T|M=T) = 0.9, P(T=T|M=F) = 0.1

Hasilkan 5 sampel menggunakan angka random berikut: (0.4, 0.3, 0.6), (0.2, 0.5, 0.8), (0.8, 0.1, 0.3), (0.1, 0.9, 0.2), (0.5, 0.7, 0.4)

**Penyelesaian:**

*Step 1:* Untuk setiap set tiga angka random (r₁, r₂, r₃):
- r₁ < P(H) → H=T; else H=F
- r₂ < P(M|H) → M=T; else M=F
- r₃ < P(T|M) → T=T; else T=F

*Step 2:* Hasilkan sampel

**Sampel 1:** (0.4, 0.3, 0.6)
- H: 0.4 > 0.3 → H=F
- M: P(M=T|H=F)=0.2, 0.3 > 0.2 → M=F
- T: P(T=T|M=F)=0.1, 0.6 > 0.1 → T=F
- Hasil: (F, F, F)

**Sampel 2:** (0.2, 0.5, 0.8)
- H: 0.2 < 0.3 → H=T
- M: P(M=T|H=T)=0.8, 0.5 < 0.8 → M=T
- T: P(T=T|M=T)=0.9, 0.8 < 0.9 → T=T
- Hasil: (T, T, T)

**Sampel 3:** (0.8, 0.1, 0.3)
- H: 0.8 > 0.3 → H=F
- M: P(M=T|H=F)=0.2, 0.1 < 0.2 → M=T
- T: P(T=T|M=T)=0.9, 0.3 < 0.9 → T=T
- Hasil: (F, T, T)

**Sampel 4:** (0.1, 0.9, 0.2)
- H: 0.1 < 0.3 → H=T
- M: P(M=T|H=T)=0.8, 0.9 > 0.8 → M=F
- T: P(T=T|M=F)=0.1, 0.2 > 0.1 → T=F
- Hasil: (T, F, F)

**Sampel 5:** (0.5, 0.7, 0.4)
- H: 0.5 > 0.3 → H=F
- M: P(M=T|H=F)=0.2, 0.7 > 0.2 → M=F
- T: P(T=T|M=F)=0.1, 0.4 > 0.1 → T=F
- Hasil: (F, F, F)

*Step 3:* Ringkasan sampel

| # | H | M | T |
|:-:|:-:|:-:|:-:|
| 1 | F | F | F |
| 2 | T | T | T |
| 3 | F | T | T |
| 4 | T | F | F |
| 5 | F | F | F |

*Step 4:* Estimasi probabilitas dari sampel
- $\hat{P}(H=T) = 2/5 = 0.40$ (aktual: 0.30)
- $\hat{P}(T=T) = 2/5 = 0.40$
- $\hat{P}(T=T|H=T) = 1/2 = 0.50$

**Jawaban:** Lima sampel dihasilkan menggunakan prior sampling. Estimasi dari 5 sampel belum sangat akurat (P(H=T)=0.40 vs aktual 0.30) karena jumlah sampel terlalu sedikit. Semakin banyak sampel, estimasi akan konvergen ke distribusi sebenarnya.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Sebuah jaringan Bayesian memiliki 8 node Boolean dimana setiap node memiliki maksimal 2 parent. Berapa jumlah parameter maksimal? Bandingkan dengan full joint distribution!

**Jawaban:** Parameter maksimal per node: $2^2 = 4$ (untuk node dengan 2 parent Boolean). Total maksimal: $8 \times 4 = 32$ parameter. Full joint distribution: $2^8 - 1 = 255$ parameter. Rasio: 32/255 ≈ 12.5%.

---

### Problem S2 ⭐⭐
**Soal:** Diberikan jaringan A → B ← C, A → D, B → D. Tentukan apakah A dan C d-separated diberikan {D}!

**Jawaban:** Path A → B ← C: B adalah collider. D adalah descendant dari B (B → D). D ∈ {D}, dan D adalah descendant dari collider B, sehingga path menjadi **aktif**. A dan C **tidak** d-separated diberikan {D}. Ini adalah kasus di mana observasi pada descendant dari collider juga mengaktifkan path.

---

### Problem S3 ⭐⭐
**Soal:** Jelaskan perbedaan antara inference by enumeration dan variable elimination dalam hal efisiensi komputasi!

**Jawaban:** Enumeration menghitung setiap kombinasi dari awal, sehingga banyak sub-ekspresi dihitung berulang kali — kompleksitas $O(n \cdot 2^n)$. Variable Elimination menghindari pengulangan dengan menyimpan hasil antara sebagai faktor, mengeliminasi variabel satu per satu — kompleksitas $O(n \cdot 2^w)$ dimana $w$ adalah treewidth. Untuk jaringan sparse (treewidth rendah), VE jauh lebih efisien.

---

### Problem S4 ⭐⭐⭐
**Soal:** Dalam konteks pertahanan, jelaskan mengapa approximate inference diperlukan untuk jaringan Bayesian besar pada sistem surveillance real-time!

**Jawaban:** Sistem surveillance real-time seperti C6ISR memiliki ratusan variabel (sensor, target, kondisi lingkungan) yang membentuk jaringan Bayesian besar dengan treewidth tinggi. Inferensi eksak menjadi NP-hard dan tidak dapat diselesaikan dalam waktu yang dibutuhkan untuk keputusan real-time. Approximate inference (seperti particle filtering) dapat memberikan estimasi "cukup baik" dalam waktu yang terbatas, memungkinkan situational awareness yang terus diperbarui meskipun dengan ketidakpastian yang lebih tinggi.

---

### Problem S5 ⭐⭐⭐
**Soal:** Bangun jaringan Bayesian minimal (termasuk CPT) untuk sistem deteksi kebocoran data di jaringan militer dengan variabel: AksesAnomali, WaktuTidakBiasa, VolumeDataBesar, KebocoranData, AlertAdmin!

**Jawaban:** Topologi: AksesAnomali → KebocoranData, WaktuTidakBiasa → KebocoranData, VolumeDataBesar → KebocoranData, KebocoranData → AlertAdmin. Root: AksesAnomali (P=0.03), WaktuTidakBiasa (P=0.15), VolumeDataBesar (P=0.05). KebocoranData CPT: 8 baris (3 parent Boolean). AlertAdmin CPT: 2 baris. Total: 3×1 + 8 + 2 = 13 parameter. Full joint: $2^5 - 1 = 31$ parameter.

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Jaringan Bayesian** | Representasi grafis compact dari distribusi probabilitas gabungan menggunakan DAG dan CPT |
| **DAG** | Graf berarah tanpa siklus yang menunjukkan ketergantungan antar variabel |
| **CPT** | Tabel probabilitas bersyarat setiap node diberikan parent-nya |
| **Chain Rule** | $P(x_1,...,x_n) = \prod_i P(x_i \mid Parents(X_i))$ |
| **Conditional Independence** | Setiap node independen dari non-descendant diberikan parent-nya |
| **Chain** | A → B → C: A ⊥ C \| B |
| **Common Cause** | A ← B → C: A ⊥ C \| B |
| **V-structure (Collider)** | A → B ← C: A ⊥ C; A ⊥̸ C \| B (explaining away) |
| **D-Separation** | Kriteria grafis untuk menentukan conditional independence |
| **Markov Blanket** | Parent + children + co-parent = set minimal untuk independensi |
| **Enumeration** | Inferensi eksak dengan menjumlahkan semua hidden variables |
| **Variable Elimination** | Inferensi eksak yang lebih efisien menggunakan faktor |
| **Approximate Inference** | Metode sampling untuk estimasi probabilitas pada jaringan besar |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 13-14**.
2. Bishop, C.M. (2006). *Pattern Recognition and Machine Learning*. Springer. **Chapter 8**.
3. Koller, D. & Friedman, N. (2009). *Probabilistic Graphical Models*. MIT Press. **Chapter 3-9**.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
