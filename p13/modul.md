# Modul 13: Pembelajaran Mesin - Supervised Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 13  
**Topik:** Pembelajaran Mesin - Supervised Learning  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:

1. Menjelaskan tiga paradigma utama pembelajaran mesin: supervised, unsupervised, dan reinforcement learning
2. Mengidentifikasi komponen-komponen supervised learning: training set, test set, features, dan labels
3. Menghitung entropy dan information gain untuk membangun decision tree
4. Mengimplementasikan algoritma ID3 untuk klasifikasi data
5. Menjelaskan konsep overfitting dan teknik pruning pada decision tree
6. Menerapkan Naive Bayes classifier untuk klasifikasi sederhana
7. Menjelaskan konsep regresi linear dan metode least squares
8. Mengevaluasi model menggunakan metrik accuracy, precision, recall, dan F1-score
9. Menerapkan teknik cross-validation untuk validasi model

---

## 1. Paradigma Pembelajaran Mesin

### 1.1 Definisi Pembelajaran Mesin

> **Pembelajaran Mesin (Machine Learning)** adalah cabang kecerdasan artifisial yang memungkinkan sistem komputer untuk belajar dan meningkatkan kinerjanya dari pengalaman (data) tanpa diprogram secara eksplisit untuk setiap tugas.

Definisi formal dari Tom Mitchell (1997):

> Sebuah program komputer dikatakan **belajar** dari pengalaman **E** terhadap kelas tugas **T** dengan ukuran kinerja **P**, jika kinerjanya pada tugas T yang diukur oleh P meningkat seiring dengan pengalaman E.

| Komponen | Simbol | Contoh (Deteksi Ancaman Radar) |
|----------|--------|-------------------------------|
| Tugas (Task) | T | Mengklasifikasikan sinyal radar sebagai ancaman atau bukan |
| Ukuran Kinerja (Performance) | P | Akurasi klasifikasi pada data uji |
| Pengalaman (Experience) | E | Database sinyal radar historis yang sudah dilabeli |

#### Solved Problem 1 ⭐

**Soal:** Identifikasi komponen T, P, dan E untuk sistem deteksi email spam!

**Penyelesaian:**

*Step 1:* Identifikasi Task (T)
- T = Mengklasifikasikan email masuk sebagai "spam" atau "bukan spam"

*Step 2:* Identifikasi Performance (P)
- P = Persentase email yang diklasifikasikan dengan benar (akurasi)

*Step 3:* Identifikasi Experience (E)
- E = Kumpulan email yang telah dilabeli oleh pengguna sebagai spam atau bukan spam

**Jawaban:** T = klasifikasi email sebagai spam/bukan spam, P = akurasi klasifikasi, E = database email berlabel.

---

### 1.2 Tiga Paradigma Pembelajaran Mesin

![Tiga Paradigma Machine Learning](images/p13-01-tiga-paradigma-ml.png)

*Gambar 13.1: Tiga paradigma utama dalam pembelajaran mesin*

#### 1.2.1 Supervised Learning (Pembelajaran Terawasi)

> **Supervised Learning** adalah paradigma ML di mana model belajar dari data yang memiliki **label** (jawaban yang benar), kemudian menggunakan pengetahuan tersebut untuk memprediksi label data baru.

**Komponen utama:**

| Komponen | Deskripsi | Contoh |
|----------|-----------|--------|
| **Training Set** | Data berlabel untuk melatih model | 1000 citra satelit dengan label "kendaraan militer" / "sipil" |
| **Test Set** | Data berlabel untuk menguji model | 200 citra satelit yang belum pernah dilihat model |
| **Features (Fitur)** | Atribut input yang mendeskripsikan data | Ukuran objek, bentuk, warna, lokasi |
| **Labels (Target)** | Output yang ingin diprediksi | "kendaraan militer" atau "sipil" |

**Dua jenis tugas supervised learning:**
- **Klasifikasi**: Label berupa kategori diskret (contoh: spam/bukan spam, ancaman/aman)
- **Regresi**: Label berupa nilai kontinu (contoh: prediksi suhu, estimasi jarak)

#### 1.2.2 Unsupervised Learning (Pembelajaran Tak Terawasi)

> **Unsupervised Learning** adalah paradigma ML di mana model belajar dari data **tanpa label**, mencari pola atau struktur tersembunyi dalam data.

Contoh: Mengelompokkan sinyal komunikasi yang dicegat berdasarkan pola frekuensi tanpa mengetahui asal sumbernya.

**Catatan:** Unsupervised learning akan dibahas lebih mendalam pada **Pertemuan 14**.

#### 1.2.3 Reinforcement Learning (Pembelajaran Penguatan)

> **Reinforcement Learning** adalah paradigma ML di mana agen belajar melalui interaksi dengan lingkungan, menerima **reward** atau **penalty** berdasarkan tindakannya.

Contoh: Drone militer yang belajar manuver evasif melalui simulasi berulang, mendapat reward saat berhasil menghindari rudal.

**Catatan:** Reinforcement learning akan dibahas lebih mendalam pada **Pertemuan 14**.

#### Solved Problem 2 ⭐

**Soal:** Klasifikasikan setiap skenario berikut ke dalam paradigma ML yang sesuai: (a) Sistem yang belajar mengenali wajah dari foto berlabel, (b) Sistem yang mengelompokkan dokumen berita tanpa kategori, (c) Robot yang belajar berjalan melalui trial-and-error!

**Penyelesaian:**

*Step 1:* Analisis setiap skenario berdasarkan ketersediaan label dan metode belajar

| Skenario | Label? | Metode Belajar | Paradigma |
|----------|--------|----------------|-----------|
| (a) Pengenalan wajah dari foto berlabel | Ya (nama orang) | Belajar dari contoh berlabel | **Supervised** |
| (b) Pengelompokan dokumen berita | Tidak | Mencari pola/cluster | **Unsupervised** |
| (c) Robot belajar berjalan | Reward/penalty | Trial-and-error | **Reinforcement** |

**Jawaban:** (a) Supervised Learning, (b) Unsupervised Learning, (c) Reinforcement Learning.

---

#### Solved Problem 3 ⭐

**Soal:** Dalam konteks sistem pertahanan udara, berikan contoh tugas klasifikasi dan tugas regresi!

**Penyelesaian:**

*Step 1:* Identifikasi tugas klasifikasi (output diskret)
- **Klasifikasi**: Menentukan apakah objek radar adalah pesawat militer, pesawat sipil, drone, atau burung
- Output: kategori dari beberapa kelas

*Step 2:* Identifikasi tugas regresi (output kontinu)
- **Regresi**: Memprediksi waktu kedatangan objek ke zona pertahanan berdasarkan kecepatan dan arah
- Output: nilai kontinu (menit)

**Jawaban:** Klasifikasi: mengidentifikasi jenis objek radar (militer/sipil/drone/burung). Regresi: memprediksi waktu kedatangan objek ke zona pertahanan (dalam menit).

---

## 2. Decision Tree (Pohon Keputusan)

### 2.1 Konsep Decision Tree

> **Decision Tree** adalah model supervised learning yang menggunakan struktur pohon untuk membuat keputusan. Setiap **node internal** merepresentasikan pengujian pada suatu fitur, setiap **cabang** merepresentasikan hasil pengujian, dan setiap **node daun (leaf)** merepresentasikan label kelas atau nilai prediksi.

![Struktur Decision Tree](images/p13-02-struktur-decision-tree.png)

*Gambar 13.2: Struktur dasar decision tree untuk klasifikasi ancaman*

**Komponen Decision Tree:**

| Komponen | Deskripsi | Dalam Contoh Radar |
|----------|-----------|-------------------|
| **Root Node** | Node paling atas, pengujian pertama | "Kecepatan > 800 km/j?" |
| **Internal Node** | Node keputusan dengan pengujian fitur | "Transponder Aktif?" |
| **Branch** | Cabang berdasarkan hasil pengujian | "Ya" / "Tidak" |
| **Leaf Node** | Node akhir dengan prediksi kelas | "ANCAMAN" / "AMAN" |

**Kelebihan Decision Tree:**
- Mudah diinterpretasi dan divisualisasi
- Tidak memerlukan normalisasi data
- Dapat menangani data numerik dan kategorikal
- Proses keputusan transparan (explainable AI)

#### Solved Problem 4 ⭐

**Soal:** Diberikan decision tree berikut untuk menentukan apakah cuaca cocok untuk operasi penerbangan militer:

```
[Cuaca Cerah?]
├── Ya → [Angin > 30 knot?]
│         ├── Ya → TIDAK TERBANG
│         └── Tidak → TERBANG
└── Tidak → [Hujan Deras?]
            ├── Ya → TIDAK TERBANG
            └── Tidak → [Jarak Pandang > 5km?]
                        ├── Ya → TERBANG
                        └── Tidak → TIDAK TERBANG
```

Tentukan keputusan untuk kondisi: Cuaca berawan, tidak hujan deras, jarak pandang 3 km!

**Penyelesaian:**

*Step 1:* Mulai dari root node: Cuaca Cerah? → **Tidak** (berawan)

*Step 2:* Ikuti cabang "Tidak" → Hujan Deras? → **Tidak**

*Step 3:* Ikuti cabang "Tidak" → Jarak Pandang > 5km? → **Tidak** (3 km)

*Step 4:* Ikuti cabang "Tidak" → **TIDAK TERBANG**

**Jawaban:** Keputusan adalah **TIDAK TERBANG** karena meskipun tidak hujan, jarak pandang 3 km kurang dari threshold 5 km.

---

### 2.2 Entropy dan Information Gain

#### 2.2.1 Entropy

> **Entropy** adalah ukuran ketidakpastian (impurity) dalam suatu himpunan data. Entropy bernilai 0 jika semua data memiliki kelas yang sama (murni), dan bernilai maksimum jika data terbagi rata di semua kelas.

**Rumus Entropy untuk klasifikasi biner:**

$$H(S) = -p_+ \log_2(p_+) - p_- \log_2(p_-)$$

dimana:
- $p_+$ = proporsi contoh positif
- $p_-$ = proporsi contoh negatif
- $\log_2(0)$ didefinisikan sebagai 0

**Rumus Entropy untuk multi-kelas:**

$$H(S) = -\sum_{i=1}^{c} p_i \log_2(p_i)$$

dimana $c$ = jumlah kelas dan $p_i$ = proporsi kelas ke-$i$.

![Grafik Entropy](images/p13-03-grafik-entropy.png)

*Gambar 13.3: Grafik entropy untuk klasifikasi biner*

**Nilai-nilai penting entropy:**

| Kondisi | $p_+$ | $p_-$ | Entropy $H(S)$ | Interpretasi |
|---------|--------|--------|----------------|-------------|
| Semua positif | 1.0 | 0.0 | 0 | Murni (tidak ada ketidakpastian) |
| Setengah-setengah | 0.5 | 0.5 | 1.0 | Ketidakpastian maksimum |
| Semua negatif | 0.0 | 1.0 | 0 | Murni (tidak ada ketidakpastian) |
| 75%-25% | 0.75 | 0.25 | 0.811 | Cukup pasti |

#### Solved Problem 5 ⭐

**Soal:** Hitung entropy dari himpunan data pelatihan berikut yang berisi 14 sampel sinyal radar: 9 dilabeli "Ancaman" dan 5 dilabeli "Aman"!

**Penyelesaian:**

*Step 1:* Hitung proporsi setiap kelas
- $p_{ancaman} = 9/14 = 0.643$
- $p_{aman} = 5/14 = 0.357$

*Step 2:* Terapkan rumus entropy
$$H(S) = -p_{ancaman} \log_2(p_{ancaman}) - p_{aman} \log_2(p_{aman})$$
$$H(S) = -(0.643) \log_2(0.643) - (0.357) \log_2(0.357)$$
$$H(S) = -(0.643)(-0.638) - (0.357)(-1.486)$$
$$H(S) = 0.410 + 0.531$$
$$H(S) = 0.940$$

**Jawaban:** Entropy himpunan data adalah **H(S) = 0.940**, mendekati 1.0 yang menunjukkan ketidakpastian tinggi (data tidak terlalu didominasi satu kelas).

---

#### Solved Problem 6 ⭐

**Soal:** Hitung entropy dari himpunan data dengan 3 kelas: 10 "Pesawat Tempur", 5 "Drone", dan 5 "Pesawat Sipil" dari total 20 sampel!

**Penyelesaian:**

*Step 1:* Hitung proporsi setiap kelas
- $p_{tempur} = 10/20 = 0.5$
- $p_{drone} = 5/20 = 0.25$
- $p_{sipil} = 5/20 = 0.25$

*Step 2:* Terapkan rumus entropy multi-kelas
$$H(S) = -\sum_{i=1}^{3} p_i \log_2(p_i)$$
$$H(S) = -(0.5)\log_2(0.5) - (0.25)\log_2(0.25) - (0.25)\log_2(0.25)$$
$$H(S) = -(0.5)(-1) - (0.25)(-2) - (0.25)(-2)$$
$$H(S) = 0.5 + 0.5 + 0.5$$
$$H(S) = 1.5$$

**Jawaban:** Entropy adalah **H(S) = 1.5 bit**. Nilai maksimum entropy untuk 3 kelas adalah $\log_2(3) \approx 1.585$, sehingga data ini memiliki ketidakpastian yang cukup tinggi.

---

#### 2.2.2 Information Gain

> **Information Gain** mengukur seberapa banyak ketidakpastian berkurang setelah mempartisi data berdasarkan suatu atribut. Atribut dengan information gain tertinggi dipilih sebagai node keputusan.

**Rumus Information Gain:**

$$IG(S, A) = H(S) - \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(S_v)$$

dimana:
- $H(S)$ = entropy himpunan awal
- $Values(A)$ = semua nilai yang mungkin dari atribut $A$
- $S_v$ = subset dari $S$ di mana atribut $A$ bernilai $v$
- $|S_v|/|S|$ = proporsi data yang memiliki nilai $v$ pada atribut $A$

#### Solved Problem 7 ⭐⭐

**Soal:** Diberikan dataset pelatihan untuk klasifikasi ancaman radar:

| No | Kecepatan | Ketinggian | Transponder | Kelas |
|----|-----------|------------|-------------|-------|
| 1 | Tinggi | Tinggi | Tidak | Ancaman |
| 2 | Tinggi | Tinggi | Ya | Aman |
| 3 | Rendah | Rendah | Tidak | Ancaman |
| 4 | Rendah | Tinggi | Ya | Aman |
| 5 | Tinggi | Rendah | Tidak | Ancaman |
| 6 | Rendah | Tinggi | Ya | Aman |
| 7 | Tinggi | Rendah | Tidak | Ancaman |
| 8 | Rendah | Rendah | Ya | Aman |
| 9 | Tinggi | Tinggi | Tidak | Ancaman |
| 10 | Rendah | Tinggi | Ya | Aman |

Hitung information gain untuk atribut "Transponder"!

**Penyelesaian:**

*Step 1:* Hitung entropy keseluruhan
- Ancaman: 5, Aman: 5 → $p_+ = 0.5$, $p_- = 0.5$
$$H(S) = -0.5\log_2(0.5) - 0.5\log_2(0.5) = 0.5 + 0.5 = 1.0$$

*Step 2:* Partisi berdasarkan atribut "Transponder"

**Transponder = Ya** (sampel 2, 4, 6, 8, 10): 5 data, semua "Aman"
$$H(S_{Ya}) = -1.0\log_2(1.0) - 0\log_2(0) = 0$$

**Transponder = Tidak** (sampel 1, 3, 5, 7, 9): 5 data, semua "Ancaman"
$$H(S_{Tidak}) = -1.0\log_2(1.0) - 0\log_2(0) = 0$$

*Step 3:* Hitung weighted average entropy setelah split
$$H_{split} = \frac{5}{10} \times 0 + \frac{5}{10} \times 0 = 0$$

*Step 4:* Hitung information gain
$$IG(S, Transponder) = H(S) - H_{split} = 1.0 - 0 = 1.0$$

**Jawaban:** Information gain atribut "Transponder" adalah **IG = 1.0** (maksimum), artinya atribut ini **sempurna** memisahkan kedua kelas. Transponder seharusnya menjadi root node.

---

#### Solved Problem 8 ⭐⭐

**Soal:** Dengan dataset yang sama pada Solved Problem 7, hitung information gain untuk atribut "Kecepatan"!

**Penyelesaian:**

*Step 1:* Entropy keseluruhan (sudah dihitung): $H(S) = 1.0$

*Step 2:* Partisi berdasarkan atribut "Kecepatan"

**Kecepatan = Tinggi** (sampel 1, 2, 5, 7, 9): 5 data
- Ancaman: 4 (sampel 1, 5, 7, 9), Aman: 1 (sampel 2)
$$H(S_{Tinggi}) = -\frac{4}{5}\log_2\frac{4}{5} - \frac{1}{5}\log_2\frac{1}{5}$$
$$= -(0.8)(-0.322) - (0.2)(-2.322)$$
$$= 0.258 + 0.464 = 0.722$$

**Kecepatan = Rendah** (sampel 3, 4, 6, 8, 10): 5 data
- Ancaman: 1 (sampel 3), Aman: 4 (sampel 4, 6, 8, 10)
$$H(S_{Rendah}) = -\frac{1}{5}\log_2\frac{1}{5} - \frac{4}{5}\log_2\frac{4}{5}$$
$$= 0.464 + 0.258 = 0.722$$

*Step 3:* Hitung weighted average entropy
$$H_{split} = \frac{5}{10} \times 0.722 + \frac{5}{10} \times 0.722 = 0.722$$

*Step 4:* Hitung information gain
$$IG(S, Kecepatan) = 1.0 - 0.722 = 0.278$$

**Jawaban:** Information gain atribut "Kecepatan" adalah **IG = 0.278**, lebih rendah dari "Transponder" (1.0). Maka "Transponder" lebih informatif sebagai node keputusan.

---

### 2.3 Algoritma ID3

> **Algoritma ID3 (Iterative Dichotomiser 3)** adalah algoritma untuk membangun decision tree dengan memilih atribut yang memiliki **information gain tertinggi** pada setiap langkah secara rekursif.

**Pseudocode ID3:**

```
function ID3(S, Attributes):
    if semua data di S memiliki kelas sama:
        return Leaf(kelas tersebut)
    if Attributes kosong:
        return Leaf(kelas mayoritas di S)
    
    A* = atribut dengan information gain tertinggi
    tree = Decision Node(A*)
    
    for setiap nilai v dari A*:
        Sv = subset S dimana A* = v
        if Sv kosong:
            tambahkan Leaf(kelas mayoritas S) ke tree
        else:
            tambahkan ID3(Sv, Attributes - {A*}) ke tree
    
    return tree
```

#### Solved Problem 9 ⭐⭐

**Soal:** Bangun decision tree menggunakan ID3 untuk dataset berikut (klasifikasi apakah patroli perlu ditingkatkan):

| No | Musim | Ancaman Intel | Perbatasan | Tingkatkan? |
|----|-------|---------------|------------|-------------|
| 1 | Kemarau | Tinggi | Darat | Ya |
| 2 | Hujan | Tinggi | Darat | Ya |
| 3 | Kemarau | Rendah | Laut | Tidak |
| 4 | Hujan | Rendah | Darat | Tidak |
| 5 | Kemarau | Tinggi | Laut | Ya |
| 6 | Hujan | Rendah | Laut | Tidak |

**Penyelesaian:**

*Step 1:* Hitung entropy keseluruhan
- Ya: 3, Tidak: 3 → $H(S) = 1.0$

*Step 2:* Hitung IG untuk setiap atribut

**Atribut "Ancaman Intel":**
- Tinggi (1,2,5): 3 data, Ya=3 → $H = 0$
- Rendah (3,4,6): 3 data, Tidak=3 → $H = 0$
- $IG = 1.0 - 0 = \mathbf{1.0}$

**Atribut "Musim":**
- Kemarau (1,3,5): Ya=2, Tidak=1 → $H = 0.918$
- Hujan (2,4,6): Ya=1, Tidak=2 → $H = 0.918$
- $IG = 1.0 - 0.918 = 0.082$

**Atribut "Perbatasan":**
- Darat (1,2,4): Ya=2, Tidak=1 → $H = 0.918$
- Laut (3,5,6): Ya=1, Tidak=2 → $H = 0.918$
- $IG = 1.0 - 0.918 = 0.082$

*Step 3:* Pilih atribut dengan IG tertinggi → **"Ancaman Intel" (IG = 1.0)**

*Step 4:* Bangun tree

Karena "Ancaman Intel = Tinggi" → semua Ya, dan "Ancaman Intel = Rendah" → semua Tidak:

```
[Ancaman Intel?]
├── Tinggi → Ya (Tingkatkan Patroli)
└── Rendah → Tidak (Patroli Normal)
```

**Jawaban:** Decision tree hanya memerlukan satu atribut: "Ancaman Intel". Jika tingkat ancaman intelijen tinggi, tingkatkan patroli; jika rendah, patroli normal.

---

#### Solved Problem 10 ⭐⭐⭐

**Soal:** Diberikan dataset yang lebih kompleks untuk klasifikasi persetujuan terbang drone:

| No | Cuaca | Angin | Misi | Jarak | Izin? |
|----|-------|-------|------|-------|-------|
| 1 | Cerah | Lemah | Pengintaian | Dekat | Ya |
| 2 | Cerah | Kuat | Pengintaian | Jauh | Tidak |
| 3 | Berawan | Lemah | Pengintaian | Dekat | Ya |
| 4 | Hujan | Lemah | Logistik | Dekat | Tidak |
| 5 | Cerah | Lemah | Logistik | Jauh | Ya |
| 6 | Berawan | Kuat | Pengintaian | Dekat | Tidak |
| 7 | Berawan | Lemah | Logistik | Dekat | Ya |
| 8 | Hujan | Kuat | Pengintaian | Jauh | Tidak |

Hitung information gain untuk atribut "Cuaca" dan "Angin", kemudian tentukan root node!

**Penyelesaian:**

*Step 1:* Entropy keseluruhan
- Izin Ya: 4 (no. 1,3,5,7), Izin Tidak: 4 (no. 2,4,6,8)
$$H(S) = -\frac{4}{8}\log_2\frac{4}{8} - \frac{4}{8}\log_2\frac{4}{8} = 1.0$$

*Step 2:* IG untuk "Cuaca"

**Cerah** (1,2,5): Ya=2, Tidak=1
$$H(S_{cerah}) = -\frac{2}{3}\log_2\frac{2}{3} - \frac{1}{3}\log_2\frac{1}{3} = 0.918$$

**Berawan** (3,6,7): Ya=2, Tidak=1
$$H(S_{berawan}) = 0.918$$

**Hujan** (4,8): Ya=0, Tidak=2
$$H(S_{hujan}) = 0$$

$$H_{split} = \frac{3}{8}(0.918) + \frac{3}{8}(0.918) + \frac{2}{8}(0) = 0.689$$

$$IG(S, Cuaca) = 1.0 - 0.689 = 0.311$$

*Step 3:* IG untuk "Angin"

**Lemah** (1,3,4,5,7): Ya=4, Tidak=1
$$H(S_{lemah}) = -\frac{4}{5}\log_2\frac{4}{5} - \frac{1}{5}\log_2\frac{1}{5} = 0.722$$

**Kuat** (2,6,8): Ya=0, Tidak=3
$$H(S_{kuat}) = 0$$

$$H_{split} = \frac{5}{8}(0.722) + \frac{3}{8}(0) = 0.451$$

$$IG(S, Angin) = 1.0 - 0.451 = 0.549$$

*Step 4:* Bandingkan dan tentukan root node

| Atribut | Information Gain |
|---------|-----------------|
| Cuaca | 0.311 |
| **Angin** | **0.549** |

**Jawaban:** Atribut **"Angin"** memiliki information gain tertinggi (0.549) dan dipilih sebagai root node. Jika Angin = Kuat, maka Izin = Tidak (semua 3 sampel adalah Tidak). Jika Angin = Lemah, perlu dilanjutkan dengan atribut lain (4 Ya, 1 Tidak).

---

### 2.4 Overfitting dan Pruning

#### 2.4.1 Overfitting

> **Overfitting** terjadi ketika model terlalu menyesuaikan diri dengan data pelatihan (termasuk noise), sehingga performanya sangat baik pada data pelatihan tetapi buruk pada data baru (test data).

![Overfitting vs Underfitting](images/p13-04-overfitting-underfitting.png)

*Gambar 13.4: Ilustrasi underfitting, good fit, dan overfitting*

**Tanda-tanda overfitting pada decision tree:**
- Pohon terlalu dalam/kompleks
- Akurasi training sangat tinggi (mendekati 100%) tetapi akurasi test rendah
- Node daun hanya memiliki sedikit sampel

#### 2.4.2 Pruning (Pemangkasan)

> **Pruning** adalah teknik untuk mengurangi ukuran decision tree dengan menghapus bagian-bagian yang tidak memberikan kontribusi signifikan, mengurangi overfitting.

**Dua jenis pruning:**

| Jenis | Deskripsi | Kapan Dilakukan |
|-------|-----------|-----------------|
| **Pre-pruning (Early Stopping)** | Menghentikan pertumbuhan pohon sebelum sempurna | Saat membangun pohon |
| **Post-pruning** | Membangun pohon penuh, lalu memangkas subtree | Setelah pohon selesai dibangun |

**Kriteria pre-pruning:**
- Batas kedalaman maksimum (max depth)
- Jumlah minimum sampel di node daun
- Threshold minimum information gain

#### Solved Problem 11 ⭐

**Soal:** Sebuah decision tree memiliki akurasi 99% pada training set tetapi hanya 65% pada test set. Apa yang terjadi dan bagaimana mengatasinya?

**Penyelesaian:**

*Step 1:* Identifikasi masalah
- Gap besar antara akurasi training (99%) dan test (65%)
- Ini adalah tanda jelas **overfitting**

*Step 2:* Analisis penyebab
- Pohon terlalu dalam, menghafal noise dalam data training
- Model terlalu kompleks untuk jumlah data yang tersedia

*Step 3:* Solusi
1. **Pre-pruning**: Batasi kedalaman pohon, minimum sampel per leaf
2. **Post-pruning**: Pangkas subtree yang tidak meningkatkan akurasi validasi
3. **Tambah data training**: Lebih banyak data mengurangi overfitting
4. **Cross-validation**: Gunakan untuk mendeteksi overfitting lebih awal

**Jawaban:** Model mengalami **overfitting**. Solusi: terapkan pruning (batasi kedalaman pohon atau pangkas subtree), tambah data training, atau gunakan cross-validation.

---

### 2.5 Algoritma C4.5 (Pengenalan)

> **C4.5** adalah pengembangan dari ID3 yang menggunakan **Gain Ratio** sebagai pengganti information gain untuk mengatasi bias terhadap atribut dengan banyak nilai.

**Rumus Gain Ratio:**

$$GainRatio(S, A) = \frac{IG(S, A)}{SplitInfo(S, A)}$$

$$SplitInfo(S, A) = -\sum_{v \in Values(A)} \frac{|S_v|}{|S|} \log_2 \frac{|S_v|}{|S|}$$

#### Solved Problem 12 ⭐⭐

**Soal:** Mengapa information gain standar (ID3) dapat bias terhadap atribut dengan banyak nilai? Berikan contoh!

**Penyelesaian:**

*Step 1:* Jelaskan masalah

Jika suatu atribut memiliki banyak nilai unik (misalnya ID sampel), maka setiap partisi hanya berisi satu data dengan entropy 0.

*Step 2:* Contoh

Bayangkan atribut "ID_Radar" dengan nilai unik untuk setiap sampel (R001, R002, ..., R100):
- Setiap partisi berisi tepat 1 data
- Entropy setiap partisi = 0
- $IG(S, ID\_Radar) = H(S) - 0 = H(S)$ → **information gain maksimum!**

Padahal atribut ini tidak berguna untuk prediksi data baru karena setiap ID unik.

*Step 3:* Solusi C4.5

$$SplitInfo(S, ID\_Radar) = -\sum_{i=1}^{100} \frac{1}{100}\log_2\frac{1}{100} = \log_2(100) = 6.644$$

$$GainRatio = \frac{H(S)}{6.644} \approx \frac{1.0}{6.644} = 0.150$$

Gain Ratio yang rendah menunjukkan bahwa meskipun IG tinggi, atribut ini tidak informatif.

**Jawaban:** IG bias terhadap atribut dengan banyak nilai karena lebih banyak partisi cenderung menghasilkan entropy rendah. Contoh: atribut ID dengan nilai unik per sampel mendapat IG maksimum padahal tidak berguna. Gain Ratio mengoreksi ini dengan membagi IG dengan SplitInfo.

---

## 3. Naive Bayes Classifier

### 3.1 Konsep Naive Bayes

> **Naive Bayes Classifier** adalah algoritma klasifikasi probabilistik berdasarkan **Teorema Bayes** dengan asumsi **independensi** antar fitur (asumsi "naive").

**Teorema Bayes** (telah dipelajari pada Pertemuan 11):

$$P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}$$

Untuk klasifikasi, kita memilih kelas dengan probabilitas posterior tertinggi:

$$\hat{C} = \arg\max_C P(C|X) = \arg\max_C P(X|C) \cdot P(C)$$

Dengan asumsi naive independence:

$$P(X|C) = P(x_1|C) \cdot P(x_2|C) \cdot ... \cdot P(x_n|C) = \prod_{i=1}^{n} P(x_i|C)$$

#### Solved Problem 13 ⭐⭐

**Soal:** Diberikan data training untuk klasifikasi email masuk pada sistem komunikasi militer:

| No | Panjang | Lampiran | Pengirim | Kelas |
|----|---------|----------|----------|-------|
| 1 | Pendek | Ya | Internal | Aman |
| 2 | Panjang | Ya | Eksternal | Spam |
| 3 | Pendek | Tidak | Internal | Aman |
| 4 | Panjang | Ya | Eksternal | Spam |
| 5 | Pendek | Ya | Internal | Aman |
| 6 | Panjang | Tidak | Internal | Aman |
| 7 | Pendek | Ya | Eksternal | Spam |
| 8 | Panjang | Ya | Internal | Aman |

Klasifikasikan email baru: Panjang = Pendek, Lampiran = Ya, Pengirim = Eksternal.

**Penyelesaian:**

*Step 1:* Hitung prior probability
- $P(Aman) = 5/8 = 0.625$
- $P(Spam) = 3/8 = 0.375$

*Step 2:* Hitung likelihood untuk kelas "Aman"
- $P(Pendek|Aman) = 3/5 = 0.600$
- $P(Lampiran=Ya|Aman) = 3/5 = 0.600$
- $P(Eksternal|Aman) = 0/5 = 0.000$

*Step 3:* Hitung likelihood untuk kelas "Spam"
- $P(Pendek|Spam) = 1/3 = 0.333$
- $P(Lampiran=Ya|Spam) = 3/3 = 1.000$
- $P(Eksternal|Spam) = 3/3 = 1.000$

*Step 4:* Hitung posterior (tidak perlu normalisasi untuk perbandingan)

$$P(Aman|X) \propto 0.625 \times 0.600 \times 0.600 \times 0.000 = 0$$

$$P(Spam|X) \propto 0.375 \times 0.333 \times 1.000 \times 1.000 = 0.125$$

*Step 5:* Pilih kelas dengan probabilitas tertinggi
$$P(Spam|X) = 0.125 > P(Aman|X) = 0$$

**Jawaban:** Email diklasifikasikan sebagai **Spam**. Catatan: $P(Eksternal|Aman) = 0$ menyebabkan seluruh probabilitas kelas Aman menjadi 0. Dalam praktik, digunakan **Laplace smoothing** untuk menghindari probabilitas nol.

---

### 3.2 Laplace Smoothing

> **Laplace Smoothing** (additive smoothing) menambahkan konstanta kecil $\alpha$ (biasanya 1) ke setiap hitungan untuk menghindari probabilitas nol.

$$P(x_i|C) = \frac{count(x_i, C) + \alpha}{count(C) + \alpha \cdot |V_i|}$$

dimana $|V_i|$ = jumlah nilai unik atribut ke-$i$.

#### Solved Problem 14 ⭐⭐

**Soal:** Ulangi Solved Problem 13 menggunakan Laplace smoothing ($\alpha = 1$)!

**Penyelesaian:**

*Step 1:* Hitung likelihood dengan Laplace smoothing

**Kelas "Aman" (total 5):**
- $P(Pendek|Aman) = (3+1)/(5+2) = 4/7 = 0.571$
  - (|V| = 2 karena Panjang memiliki 2 nilai: Pendek, Panjang)
- $P(Lampiran=Ya|Aman) = (3+1)/(5+2) = 4/7 = 0.571$
- $P(Eksternal|Aman) = (0+1)/(5+2) = 1/7 = 0.143$

**Kelas "Spam" (total 3):**
- $P(Pendek|Spam) = (1+1)/(3+2) = 2/5 = 0.400$
- $P(Lampiran=Ya|Spam) = (3+1)/(3+2) = 4/5 = 0.800$
- $P(Eksternal|Spam) = (3+1)/(3+2) = 4/5 = 0.800$

*Step 2:* Hitung posterior
$$P(Aman|X) \propto 0.625 \times 0.571 \times 0.571 \times 0.143 = 0.029$$
$$P(Spam|X) \propto 0.375 \times 0.400 \times 0.800 \times 0.800 = 0.096$$

*Step 3:* Normalisasi
$$P(Aman|X) = \frac{0.029}{0.029 + 0.096} = 0.232$$
$$P(Spam|X) = \frac{0.096}{0.029 + 0.096} = 0.768$$

**Jawaban:** Dengan Laplace smoothing, P(Spam|X) = **0.768** dan P(Aman|X) = 0.232. Email tetap diklasifikasikan sebagai Spam, tetapi sekarang kelas Aman memiliki probabilitas non-zero.

---

#### Solved Problem 15 ⭐

**Soal:** Sebutkan kelebihan dan kekurangan Naive Bayes dibandingkan Decision Tree!

**Penyelesaian:**

| Aspek | Naive Bayes | Decision Tree |
|-------|-------------|---------------|
| **Kelebihan** | Cepat dan efisien untuk data besar | Mudah diinterpretasi |
| | Bekerja baik meski data sedikit | Tidak perlu asumsi distribusi |
| | Robust terhadap fitur irrelevan | Menangani interaksi fitur |
| **Kekurangan** | Asumsi independensi sering tidak realistis | Rentan overfitting |
| | Tidak menangkap interaksi antar fitur | Lambat untuk data sangat besar |
| | Kinerja turun jika fitur berkorelasi | Decision boundary yang rigid |

**Jawaban:** Naive Bayes unggul dalam kecepatan dan efisiensi data, tetapi asumsi independensinya sering tidak realistis. Decision Tree lebih mudah diinterpretasi dan menangkap interaksi fitur, tetapi rentan overfitting.

---

## 4. Regresi Linear

### 4.1 Konsep Regresi Linear

> **Regresi Linear** adalah metode supervised learning untuk memprediksi nilai kontinu (output numerik) berdasarkan hubungan linear antara fitur input dan output.

**Model Regresi Linear Sederhana (satu fitur):**

$$\hat{y} = w_0 + w_1 x$$

dimana:
- $\hat{y}$ = nilai prediksi
- $w_0$ = intercept (bias)
- $w_1$ = slope (bobot fitur)
- $x$ = fitur input

**Model Regresi Linear Multiple (banyak fitur):**

$$\hat{y} = w_0 + w_1 x_1 + w_2 x_2 + ... + w_n x_n$$

### 4.2 Metode Least Squares

> **Metode Least Squares** mencari parameter $w_0$ dan $w_1$ yang meminimalkan **jumlah kuadrat error** (Sum of Squared Errors/SSE) antara nilai aktual dan prediksi.

**Cost Function (SSE):**

$$SSE = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 = \sum_{i=1}^{n} (y_i - w_0 - w_1 x_i)^2$$

**Solusi analitik (closed-form):**

$$w_1 = \frac{n\sum x_i y_i - \sum x_i \sum y_i}{n\sum x_i^2 - (\sum x_i)^2}$$

$$w_0 = \bar{y} - w_1 \bar{x}$$

#### Solved Problem 16 ⭐

**Soal:** Data berikut menunjukkan hubungan antara jumlah jam latihan simulasi dan skor akurasi menembak prajurit:

| Jam Latihan (x) | Skor Akurasi (y) |
|-----------------|-----------------|
| 2 | 50 |
| 4 | 60 |
| 6 | 75 |
| 8 | 80 |
| 10 | 90 |

Cari persamaan regresi linear dan prediksi skor untuk 7 jam latihan!

**Penyelesaian:**

*Step 1:* Hitung komponen yang diperlukan

| $x_i$ | $y_i$ | $x_i y_i$ | $x_i^2$ |
|--------|--------|------------|----------|
| 2 | 50 | 100 | 4 |
| 4 | 60 | 240 | 16 |
| 6 | 75 | 450 | 36 |
| 8 | 80 | 640 | 64 |
| 10 | 90 | 900 | 100 |
| **Σ=30** | **Σ=355** | **Σ=2330** | **Σ=220** |

$n = 5$, $\bar{x} = 30/5 = 6$, $\bar{y} = 355/5 = 71$

*Step 2:* Hitung $w_1$
$$w_1 = \frac{5(2330) - (30)(355)}{5(220) - (30)^2} = \frac{11650 - 10650}{1100 - 900} = \frac{1000}{200} = 5.0$$

*Step 3:* Hitung $w_0$
$$w_0 = 71 - 5.0 \times 6 = 71 - 30 = 41$$

*Step 4:* Persamaan regresi
$$\hat{y} = 41 + 5x$$

*Step 5:* Prediksi untuk x = 7
$$\hat{y} = 41 + 5(7) = 41 + 35 = 76$$

**Jawaban:** Persamaan regresi: $\hat{y} = 41 + 5x$. Prediksi skor untuk 7 jam latihan adalah **76 poin**. Setiap tambahan 1 jam latihan meningkatkan skor rata-rata 5 poin.

---

### 4.3 Gradient Descent (Pengenalan)

> **Gradient Descent** adalah metode optimisasi iteratif untuk meminimalkan cost function dengan mengupdate parameter secara bertahap mengikuti arah negatif gradient.

**Aturan update:**

$$w_j := w_j - \alpha \frac{\partial}{\partial w_j} J(w)$$

dimana $\alpha$ = **learning rate** (laju pembelajaran).

![Ilustrasi Gradient Descent](images/p13-05-gradient-descent.png)

*Gambar 13.5: Ilustrasi gradient descent menuruni cost function*

#### Solved Problem 17 ⭐⭐

**Soal:** Jelaskan apa yang terjadi jika learning rate ($\alpha$) terlalu besar atau terlalu kecil pada gradient descent!

**Penyelesaian:**

| Learning Rate | Dampak | Masalah |
|---------------|--------|---------|
| **Terlalu kecil** | Langkah update sangat kecil | Konvergensi sangat lambat, memerlukan banyak iterasi |
| **Tepat** | Langkah proporsional dengan gradient | Konvergensi cepat dan stabil ke minimum |
| **Terlalu besar** | Langkah update terlalu besar | Divergensi (melompat-lompat, tidak konvergen) |

*Step 1:* $\alpha$ terlalu kecil → Parameter berubah sangat sedikit setiap iterasi → Memerlukan ribuan/jutaan iterasi → Tidak praktis

*Step 2:* $\alpha$ terlalu besar → Parameter berubah drastis → Melewati minimum → Bisa divergen (cost meningkat alih-alih menurun)

**Jawaban:** Learning rate terlalu kecil menyebabkan konvergensi sangat lambat, sedangkan terlalu besar menyebabkan divergensi. Pemilihan learning rate yang tepat sangat penting dan biasanya dilakukan secara eksperimental atau dengan teknik adaptive learning rate.

---

## 5. Evaluasi Model

### 5.1 Confusion Matrix

> **Confusion Matrix** adalah tabel yang menampilkan perbandingan antara prediksi model dengan kelas aktual, menjadi dasar perhitungan berbagai metrik evaluasi.

![Confusion Matrix](images/p13-06-confusion-matrix.png)

*Gambar 13.6: Struktur confusion matrix*

| | Aktual Positif | Aktual Negatif |
|------|---------------|----------------|
| **Prediksi Positif** | TP (True Positive) | FP (False Positive) |
| **Prediksi Negatif** | FN (False Negative) | TN (True Negative) |

**Dalam konteks deteksi ancaman militer:**

| Komponen | Deskripsi | Contoh |
|----------|-----------|--------|
| **TP** | Benar mendeteksi ancaman | Rudal terdeteksi sebagai ancaman |
| **FP** | Alarm palsu | Burung terdeteksi sebagai ancaman |
| **FN** | Ancaman terlewat | Drone musuh tidak terdeteksi |
| **TN** | Benar menolak non-ancaman | Pesawat sipil diidentifikasi sebagai aman |

### 5.2 Metrik Evaluasi

#### 5.2.1 Accuracy (Akurasi)

$$Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$$

#### 5.2.2 Precision (Presisi)

$$Precision = \frac{TP}{TP + FP}$$

> **Precision** mengukur: dari semua yang diprediksi positif, berapa proporsi yang benar-benar positif? (Seberapa terpercaya prediksi positif?)

#### 5.2.3 Recall (Sensitivitas)

$$Recall = \frac{TP}{TP + FN}$$

> **Recall** mengukur: dari semua yang aktual positif, berapa proporsi yang berhasil terdeteksi? (Seberapa lengkap deteksi?)

#### 5.2.4 F1-Score

$$F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$

> **F1-Score** adalah rata-rata harmonik dari precision dan recall, memberikan keseimbangan antara keduanya.

#### Solved Problem 18 ⭐⭐

**Soal:** Sistem deteksi intrusi pada jaringan militer menghasilkan confusion matrix berikut:

| | Aktual: Serangan | Aktual: Normal |
|---|---|---|
| **Prediksi: Serangan** | 85 | 15 |
| **Prediksi: Normal** | 10 | 190 |

Hitung accuracy, precision, recall, dan F1-score!

**Penyelesaian:**

*Step 1:* Identifikasi komponen
- TP = 85 (serangan terdeteksi dengan benar)
- FP = 15 (alarm palsu)
- FN = 10 (serangan terlewat)
- TN = 190 (traffic normal diidentifikasi benar)

*Step 2:* Hitung accuracy
$$Accuracy = \frac{85 + 190}{85 + 190 + 15 + 10} = \frac{275}{300} = 0.917 = 91.7\%$$

*Step 3:* Hitung precision
$$Precision = \frac{85}{85 + 15} = \frac{85}{100} = 0.850 = 85.0\%$$

*Step 4:* Hitung recall
$$Recall = \frac{85}{85 + 10} = \frac{85}{95} = 0.895 = 89.5\%$$

*Step 5:* Hitung F1-score
$$F1 = 2 \times \frac{0.850 \times 0.895}{0.850 + 0.895} = 2 \times \frac{0.761}{1.745} = 2 \times 0.436 = 0.872 = 87.2\%$$

**Jawaban:** Accuracy = 91.7%, Precision = 85.0%, Recall = 89.5%, F1-Score = 87.2%. Recall yang lebih tinggi dari precision menunjukkan sistem lebih baik dalam menangkap serangan (sedikit terlewat) meskipun ada beberapa alarm palsu.

---

#### Solved Problem 19 ⭐⭐⭐

**Soal:** Dalam konteks pertahanan, jelaskan mengapa recall lebih penting daripada precision untuk sistem deteksi rudal? Berikan analisis kuantitatif dengan contoh!

**Penyelesaian:**

*Step 1:* Analisis konsekuensi error

| Tipe Error | Deskripsi | Konsekuensi |
|------------|-----------|-------------|
| **FP (Alarm Palsu)** | Objek bukan rudal terdeteksi sebagai rudal | Biaya: mobilisasi pertahanan yang tidak perlu, pemborosan resource |
| **FN (Terlewat)** | Rudal nyata tidak terdeteksi | Biaya: **kehilangan nyawa, kerusakan infrastruktur kritis** |

*Step 2:* Justifikasi prioritas recall

Dalam deteksi rudal, **FN jauh lebih berbahaya** daripada FP:
- FN = rudal lolos → korban jiwa, kerusakan masif → **tidak dapat diperbaiki**
- FP = alarm palsu → biaya operasional → **dapat ditoleransi**

*Step 3:* Contoh kuantitatif

**Sistem A** (Precision tinggi): Precision=99%, Recall=80%
- Dari 100 rudal nyata: 80 terdeteksi, **20 lolos** → 20 kemungkinan strike

**Sistem B** (Recall tinggi): Precision=80%, Recall=99%
- Dari 100 rudal nyata: 99 terdeteksi, **1 lolos** → 1 kemungkinan strike
- Trade-off: lebih banyak alarm palsu, tapi hampir semua rudal terdeteksi

*Step 4:* Analisis F1 vs weighted metric

Untuk kasus ini, **weighted metric** lebih tepat:
$$Cost = w_{FN} \times FN + w_{FP} \times FP$$

Jika $w_{FN} = 100$ (nyawa) dan $w_{FP} = 1$ (biaya operasional):
- Sistem A: $100 \times 20 + 1 \times 1 = 2001$
- Sistem B: $100 \times 1 + 1 \times 25 = 125$ → **jauh lebih baik**

**Jawaban:** Recall lebih penting karena FN (rudal terlewat) memiliki konsekuensi fatal yang tidak dapat diperbaiki, sedangkan FP (alarm palsu) hanya menyebabkan biaya operasional. Sistem B (recall 99%) jauh lebih aman meskipun precision lebih rendah.

---

### 5.3 Kapan Menggunakan Metrik Mana?

#### Solved Problem 20 ⭐

**Soal:** Tentukan metrik evaluasi yang paling penting untuk setiap skenario berikut:

| Skenario | Metrik Utama | Alasan |
|----------|--------------|--------|
| (a) Deteksi rudal musuh | ? | ? |
| (b) Filter spam email komandan | ? | ? |
| (c) Klasifikasi foto satelit umum | ? | ? |

**Penyelesaian:**

**(a) Deteksi rudal musuh → Recall**
- FN sangat berbahaya (rudal terlewat → korban)
- FP dapat ditoleransi (alarm palsu → mobilisasi pertahanan)
- Prioritas: **jangan lewatkan ancaman apapun**

**(b) Filter spam email komandan → Precision**
- FP sangat berbahaya (email penting terfilter sebagai spam → informasi penting hilang)
- FN dapat ditoleransi (spam masuk ke inbox → hanya mengganggu)
- Prioritas: **jangan buang email yang benar-benar penting**

**(c) Klasifikasi foto satelit umum → F1-Score atau Accuracy**
- FP dan FN memiliki biaya yang relatif seimbang
- Keseimbangan antara precision dan recall diperlukan
- Prioritas: **performa keseluruhan yang seimbang**

**Jawaban:** (a) Recall - ancaman tidak boleh terlewat, (b) Precision - email penting tidak boleh dibuang, (c) F1-Score - keseimbangan diperlukan.

---

## 6. Cross-Validation

### 6.1 Konsep Cross-Validation

> **Cross-Validation** adalah teknik evaluasi model yang membagi data menjadi beberapa bagian (folds) secara bergiliran untuk training dan testing, memberikan estimasi performa model yang lebih reliable dibanding single train-test split.

**Mengapa perlu cross-validation?**
- Single split bisa memberikan estimasi yang bias
- Semua data digunakan baik untuk training maupun testing
- Mendeteksi overfitting lebih baik

### 6.2 K-Fold Cross-Validation

> **K-Fold Cross-Validation** membagi data menjadi **k** bagian (folds) yang sama besar. Model dilatih pada k-1 fold dan diuji pada 1 fold yang tersisa, diulang k kali.

![K-Fold Cross-Validation](images/p13-07-k-fold-cv.png)

*Gambar 13.7: Ilustrasi 5-fold cross-validation*

**Prosedur K-Fold CV:**
1. Bagi dataset menjadi $k$ fold yang sama besar
2. Untuk iterasi $i = 1, 2, ..., k$:
   - Gunakan fold ke-$i$ sebagai test set
   - Gunakan sisa $(k-1)$ fold sebagai training set
   - Latih model dan hitung akurasi pada fold ke-$i$
3. Hitung rata-rata akurasi dari semua $k$ iterasi

**Rata-rata performa:**

$$Accuracy_{CV} = \frac{1}{k} \sum_{i=1}^{k} Accuracy_i$$

#### Solved Problem 21 ⭐⭐⭐

**Soal:** Sebuah model klasifikasi ancaman cyber dievaluasi menggunakan 5-fold cross-validation. Hasil akurasi setiap fold:

| Fold | Akurasi |
|------|---------|
| 1 | 88% |
| 2 | 92% |
| 3 | 85% |
| 4 | 91% |
| 5 | 89% |

(a) Hitung rata-rata akurasi, (b) Hitung standard deviasi, (c) Apakah model ini stabil? Jelaskan!

**Penyelesaian:**

*Step 1:* Hitung rata-rata akurasi
$$\bar{x} = \frac{88 + 92 + 85 + 91 + 89}{5} = \frac{445}{5} = 89.0\%$$

*Step 2:* Hitung standard deviasi

| Fold | $x_i$ | $x_i - \bar{x}$ | $(x_i - \bar{x})^2$ |
|------|--------|-----------------|---------------------|
| 1 | 88 | -1.0 | 1.0 |
| 2 | 92 | 3.0 | 9.0 |
| 3 | 85 | -4.0 | 16.0 |
| 4 | 91 | 2.0 | 4.0 |
| 5 | 89 | 0.0 | 0.0 |
| | | **Σ** | **30.0** |

$$\sigma = \sqrt{\frac{\sum(x_i - \bar{x})^2}{k-1}} = \sqrt{\frac{30.0}{4}} = \sqrt{7.5} = 2.74\%$$

*Step 3:* Analisis stabilitas

- Rata-rata: 89.0% ± 2.74%
- Range: 85% - 92% (rentang 7%)
- CV (Coefficient of Variation) = 2.74/89.0 = 3.08%

Model cukup stabil karena standard deviasi relatif kecil (< 5%). Namun fold 3 (85%) sedikit lebih rendah, mungkin fold tersebut berisi data yang lebih sulit.

**Jawaban:** (a) Rata-rata akurasi = **89.0%**, (b) Standard deviasi = **2.74%**, (c) Model **cukup stabil** (CV < 5%), meskipun ada variasi antar fold yang menunjukkan model sensitif terhadap komposisi data.

---

### 6.3 Stratified K-Fold Cross-Validation

> **Stratified K-Fold** memastikan setiap fold memiliki proporsi kelas yang sama dengan dataset keseluruhan, penting untuk dataset yang tidak seimbang (imbalanced).

**Contoh:** Jika dataset memiliki 80% kelas "Aman" dan 20% kelas "Ancaman", setiap fold akan memiliki rasio yang sama.

#### Solved Problem 22 ⭐⭐⭐

**Soal:** Dataset klasifikasi sinyal radar terdiri dari 200 sampel: 160 "Normal" dan 40 "Anomali". Jelaskan mengapa K-Fold biasa bisa bermasalah dan bagaimana Stratified K-Fold menyelesaikannya! Ilustrasikan dengan 5-fold!

**Penyelesaian:**

*Step 1:* Masalah dengan K-Fold biasa

Jika data dibagi secara acak ke 5 fold (masing-masing 40 sampel):
- Kemungkinan salah satu fold mendapat 0 sampel "Anomali"
- Model yang dilatih tanpa sampel Anomali tidak belajar mendeteksi anomali
- Model yang diuji pada fold tanpa Anomali mendapat akurasi 100% (menyesatkan)

*Step 2:* Solusi Stratified K-Fold

Setiap fold mempertahankan rasio 80:20:

| Fold | Normal | Anomali | Total | Rasio Anomali |
|------|--------|---------|-------|---------------|
| 1 | 32 | 8 | 40 | 20% |
| 2 | 32 | 8 | 40 | 20% |
| 3 | 32 | 8 | 40 | 20% |
| 4 | 32 | 8 | 40 | 20% |
| 5 | 32 | 8 | 40 | 20% |

*Step 3:* Manfaat
- Setiap fold representatif terhadap distribusi keseluruhan
- Evaluasi lebih reliable terutama untuk kelas minoritas
- Varians antar fold berkurang

**Jawaban:** K-Fold biasa bisa menghasilkan fold tanpa kelas minoritas (Anomali), menyebabkan evaluasi menyesatkan. Stratified K-Fold memastikan proporsi kelas 80:20 (32 Normal, 8 Anomali per fold), sehingga model selalu dilatih dan diuji dengan kedua kelas secara proporsional.

---

## Supplementary Problems

### Problem S1 ⭐
**Soal:** Jelaskan perbedaan antara klasifikasi dan regresi dalam supervised learning! Berikan 2 contoh masing-masing dalam konteks pertahanan!

**Jawaban:**
- **Klasifikasi** menghasilkan output diskret (kategori): (1) Identifikasi Friend-or-Foe (IFF) pada radar, (2) Klasifikasi jenis kapal dari citra satelit
- **Regresi** menghasilkan output kontinu: (1) Prediksi waktu kedatangan kapal di pelabuhan, (2) Estimasi jarak tembak optimal berdasarkan kondisi cuaca

---

### Problem S2 ⭐⭐
**Soal:** Hitung entropy dari dataset dengan distribusi: 30 sampel kelas A, 30 kelas B, 30 kelas C, dan 10 kelas D.

**Jawaban:**
$p_A = 30/100 = 0.3$, $p_B = 0.3$, $p_C = 0.3$, $p_D = 10/100 = 0.1$

$H(S) = -0.3\log_2(0.3) - 0.3\log_2(0.3) - 0.3\log_2(0.3) - 0.1\log_2(0.1)$
$= 3 \times 0.3 \times 1.737 + 0.1 \times 3.322 = 1.563 + 0.332 = 1.895$ bit

---

### Problem S3 ⭐⭐
**Soal:** Sebuah model klasifikasi target menghasilkan: TP=45, FP=5, FN=15, TN=135. Hitung semua metrik evaluasi dan tentukan apakah model layak deploy untuk sistem pertahanan!

**Jawaban:**
- Accuracy = (45+135)/200 = 90%
- Precision = 45/50 = 90%
- Recall = 45/60 = 75%
- F1 = 2×(0.9×0.75)/(0.9+0.75) = 81.8%
- Recall 75% berarti 25% target terlewat → **tidak layak** untuk pertahanan, perlu peningkatan recall.

---

### Problem S4 ⭐⭐⭐
**Soal:** Jelaskan mengapa gradient descent diperlukan meskipun regresi linear memiliki solusi analitik (closed-form)!

**Jawaban:**
Solusi analitik memerlukan inversi matriks berukuran $n \times n$ dengan kompleksitas $O(n^3)$. Untuk dataset besar (jutaan fitur), ini tidak efisien. Gradient descent memiliki kompleksitas $O(n)$ per iterasi dan bisa menggunakan stochastic/mini-batch variant untuk dataset sangat besar.

---

### Problem S5 ⭐⭐⭐
**Soal:** Sebuah model decision tree untuk klasifikasi sinyal memiliki akurasi 98% pada training tetapi 72% pada 5-fold CV. Diagnosis masalah dan rekomendasikan 3 solusi spesifik!

**Jawaban:**
Masalah: **Overfitting parah** (gap 26% antara training dan CV).

Solusi:
1. **Pruning**: Terapkan max_depth=5 dan min_samples_leaf=10
2. **Feature selection**: Kurangi jumlah fitur, gunakan hanya fitur dengan information gain tertinggi
3. **Ensemble methods**: Gunakan Random Forest (banyak decision tree dengan bagging) untuk mengurangi variance

---

## Ringkasan

| Konsep | Deskripsi Singkat |
|--------|-------------------|
| **Machine Learning** | Sistem yang belajar dari data untuk meningkatkan kinerja |
| **Supervised Learning** | Belajar dari data berlabel untuk prediksi |
| **Unsupervised Learning** | Mencari pola dalam data tanpa label |
| **Reinforcement Learning** | Belajar melalui reward/penalty dari lingkungan |
| **Decision Tree** | Model pohon keputusan berbasis pengujian fitur |
| **Entropy** | Ukuran ketidakpastian/impurity: $H = -\sum p_i \log_2 p_i$ |
| **Information Gain** | Penurunan entropy setelah split: $IG = H(S) - \sum \frac{|S_v|}{|S|}H(S_v)$ |
| **ID3** | Algoritma membangun decision tree berdasarkan IG tertinggi |
| **Overfitting** | Model terlalu sesuai data training, buruk pada data baru |
| **Pruning** | Teknik mengurangi ukuran pohon untuk cegah overfitting |
| **Naive Bayes** | Klasifikasi probabilistik dengan asumsi independensi fitur |
| **Regresi Linear** | Prediksi nilai kontinu: $\hat{y} = w_0 + w_1 x$ |
| **Least Squares** | Meminimalkan jumlah kuadrat error |
| **Gradient Descent** | Optimisasi iteratif mengikuti arah negatif gradient |
| **Confusion Matrix** | Tabel TP, FP, FN, TN untuk evaluasi klasifikasi |
| **Accuracy** | $(TP+TN) / Total$ |
| **Precision** | $TP / (TP+FP)$ — keandalan prediksi positif |
| **Recall** | $TP / (TP+FN)$ — kelengkapan deteksi |
| **F1-Score** | Rata-rata harmonik precision dan recall |
| **K-Fold CV** | Evaluasi dengan membagi data ke k fold bergiliran |
| **Stratified K-Fold** | K-Fold dengan proporsi kelas terjaga di setiap fold |

---

## Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th Ed.). Pearson. **Chapter 19**.
2. Mitchell, T. (1997). *Machine Learning*. McGraw-Hill. **Chapter 3**.
3. Bishop, C.M. (2006). *Pattern Recognition and Machine Learning*. Springer. **Chapter 4**.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
