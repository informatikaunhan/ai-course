# Panduan Belajar Mandiri Pertemuan 13: Pembelajaran Mesin - Supervised Learning

**Mata Kuliah:** Kecerdasan Artifisial (AI401)  
**SKS:** 3 SKS (Teori)  
**Pertemuan:** 13  
**Topik:** Pembelajaran Mesin - Supervised Learning  
**Pengampu:** Anindito, S.Kom., S.S., S.H., M.TI., CHFI  
**Estimasi Waktu:** 360 menit (~6 jam)

---

## Tujuan Pembelajaran Mandiri

Setelah menyelesaikan belajar mandiri ini, mahasiswa diharapkan mampu:

1. Membedakan tiga paradigma pembelajaran mesin: supervised, unsupervised, dan reinforcement learning
2. Menghitung entropy dan information gain serta membangun decision tree menggunakan algoritma ID3
3. Menerapkan Naive Bayes classifier untuk klasifikasi data sederhana
4. Menjelaskan konsep regresi linear dan metode least squares
5. Menghitung metrik evaluasi model (accuracy, precision, recall, F1-score) dari confusion matrix
6. Menerapkan teknik k-fold cross-validation untuk validasi model

---

## 1. Review Konsep: Paradigma Machine Learning dan Decision Tree (45 menit)

### Ringkasan Materi

**Definisi Machine Learning (Tom Mitchell, 1997):**

Sebuah program komputer dikatakan *belajar* dari pengalaman **E** terhadap tugas **T** dengan ukuran kinerja **P**, jika kinerjanya pada T yang diukur oleh P meningkat seiring E.

**Tiga Paradigma Utama:**

| Paradigma | Data | Tujuan | Contoh Pertahanan |
|-----------|------|--------|-------------------|
| **Supervised Learning** | Berlabel (input + output) | Prediksi output untuk input baru | Klasifikasi sinyal radar (ancaman/aman) |
| **Unsupervised Learning** | Tanpa label | Menemukan pola tersembunyi | Clustering pola komunikasi musuh |
| **Reinforcement Learning** | Reward/punishment dari lingkungan | Memaksimalkan reward kumulatif | Drone navigasi melalui trial-and-error |

![Tiga Paradigma Machine Learning](images/p13-01-tiga-paradigma-ml.png)

*Gambar 13.1: Perbandingan tiga paradigma pembelajaran mesin*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Tiga paradigma pembelajaran mesin: Supervised, Unsupervised, dan Reinforcement Learning ditampilkan dalam tiga kolom
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Three-column horizontal arrangement with clear separation
COLORS: 
- Primary: #2563eb (blue) for supervised learning column
- Secondary: #10b981 (green) for unsupervised learning column
- Accent: #f59e0b (orange) for reinforcement learning column
- Neutral: #6b7280 (gray) for labels and arrows
- Background: #ffffff (white)
ELEMENTS:
1. Left column "Supervised Learning": Icon of labeled data points (circles and squares with tags), arrow pointing to a model box, then arrow to prediction. Labels: "Data Berlabel", "Model", "Prediksi"
2. Center column "Unsupervised Learning": Icon of mixed unlabeled data points, arrow to model, then arrow showing clusters. Labels: "Data Tanpa Label", "Model", "Pola/Cluster"
3. Right column "Reinforcement Learning": Icon of agent in environment with reward signal loop. Labels: "Agen", "Lingkungan", "Reward"
4. Each column has a header with distinct color
LABELS: All in Indonesian as described above
SIZE: 900x500 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements
</prompt>

**Decision Tree — Konsep Inti:**

Decision tree adalah model klasifikasi berbentuk pohon di mana:
- **Root node**: Atribut pertama yang diuji (Information Gain tertinggi)
- **Internal node**: Pengujian terhadap suatu atribut
- **Branch**: Hasil pengujian (nilai atribut)
- **Leaf node**: Keputusan akhir (label kelas)

**Entropy** mengukur ketidakmurnian (impurity) data:

$$H(S) = -\sum_{c \in C} p(c) \log_2 p(c)$$

- H = 0 → data murni (satu kelas saja)
- H = 1 → data campuran maksimal (50:50 untuk dua kelas)

**Information Gain** mengukur pengurangan entropy setelah split:

$$IG(S, A) = H(S) - H(S|A) = H(S) - \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(S_v)$$

**Algoritma ID3:** Pilih atribut dengan IG tertinggi → split → ulangi rekursif.

![Contoh Decision Tree](images/p13-02-decision-tree-example.png)

*Gambar 13.2: Contoh decision tree untuk klasifikasi ancaman*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Contoh decision tree untuk klasifikasi ancaman militer dengan tiga level
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Top-down tree structure
COLORS: 
- Primary: #2563eb (blue) for internal nodes
- Secondary: #ef4444 (red) for "Ancaman" leaf nodes
- Accent: #22c55e (green) for "Aman" leaf nodes
- Connection: #f59e0b (orange) for branches/arrows
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Root node (blue diamond): "Kecepatan?"
2. Two branches: "Tinggi" (left), "Rendah" (right)
3. Left branch leads to node "Transponder?"
4. Right branch leads to green leaf "AMAN"
5. From "Transponder?": "Tidak Ada" → red leaf "ANCAMAN", "Aktif" → green leaf "AMAN"
6. Each node is a rounded rectangle, leaves are rounded with distinct colors
LABELS: "Kecepatan?", "Transponder?", "Tinggi", "Rendah", "Tidak Ada", "Aktif", "ANCAMAN", "AMAN"
SIZE: 700x500 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements
</prompt>

### 🎬 Video Pembelajaran

| No | Judul Video | Channel | Durasi | Link |
|----|-------------|---------|--------|------|
| 1 | Machine Learning: Supervised, Unsupervised & Reinforcement | IBM Technology | 8:22 | https://www.youtube.com/watch?v=1FZ0A1QCMWc |
| 2 | Decision Tree Classification Clearly Explained | StatQuest | 17:21 | https://www.youtube.com/watch?v=_L39rN6gz7Y |
| 3 | Entropy, Information Gain, and Decision Trees | Normalized Nerd | 15:48 | https://www.youtube.com/watch?v=nodQ2s0CUbI |
| 4 | ID3 Algorithm Step by Step Example | Unfold Data Science | 12:35 | https://www.youtube.com/watch?v=UdTKxGQvYdc |

### ✍️ Latihan Pemahaman

1. **Identifikasi Paradigma:** Untuk setiap skenario berikut, tentukan paradigma ML yang paling sesuai (supervised/unsupervised/RL):
   - (a) Mendeteksi anomali pada lalu lintas jaringan militer tanpa contoh serangan sebelumnya
   - (b) Mengklasifikasikan citra satelit berdasarkan database berlabel
   - (c) Melatih robot EOD (Explosive Ordnance Disposal) melalui simulasi

2. **Hitung Entropy:** Dataset berisi 12 sampel: 8 "Ancaman" dan 4 "Aman". Hitung entropy H(S)!

3. **Information Gain:** Dari dataset soal 2, atribut "Altitude" membagi data menjadi:
   - Altitude = Tinggi: 6 Ancaman, 1 Aman (7 sampel)
   - Altitude = Rendah: 2 Ancaman, 3 Aman (5 sampel)
   
   Hitung Information Gain untuk atribut Altitude!

---

## 2. Review Konsep: Naive Bayes, Regresi Linear, dan Evaluasi Model (45 menit)

### Ringkasan Materi

**Naive Bayes Classifier:**

Berdasarkan Teorema Bayes dengan asumsi *conditional independence* antar fitur:

$$P(C|x_1, x_2, ..., x_n) \propto P(C) \prod_{i=1}^{n} P(x_i|C)$$

- Asumsi "naive": semua fitur independen given kelas
- Sederhana, cepat, dan efektif pada dataset kecil
- **Laplace smoothing** mengatasi probabilitas nol: $P(x_i|C) = \frac{count(x_i, C) + \alpha}{count(C) + \alpha \cdot |V|}$

**Regresi Linear:**

Model: $\hat{y} = w_0 + w_1 x$

Metode Least Squares meminimalkan Sum of Squared Errors:

$$w_1 = \frac{n\sum x_i y_i - \sum x_i \sum y_i}{n\sum x_i^2 - (\sum x_i)^2}, \quad w_0 = \bar{y} - w_1 \bar{x}$$

**Evaluasi Model — Confusion Matrix:**

|  | Prediksi: Positif | Prediksi: Negatif |
|---|:---:|:---:|
| **Aktual: Positif** | TP | FN |
| **Aktual: Negatif** | FP | TN |

**Metrik utama:**

| Metrik | Rumus | Mengukur |
|--------|-------|----------|
| **Accuracy** | (TP+TN) / Total | Ketepatan keseluruhan |
| **Precision** | TP / (TP+FP) | Ketepatan prediksi positif |
| **Recall** | TP / (TP+FN) | Cakupan data positif aktual |
| **F1-Score** | 2·(P·R)/(P+R) | Harmonic mean precision & recall |

**Kapan memilih metrik?**
- **Recall tinggi**: Sistem deteksi rudal (FN = rudal lolos → fatal)
- **Precision tinggi**: Filter konten (FP = konten valid terblokir → gangguan operasi)
- **F1-Score**: Keseimbangan keduanya

**Cross-Validation (K-Fold):**
1. Bagi data menjadi K fold
2. Iterasi K kali: 1 fold test, K−1 fold training
3. Rata-rata akurasi dari K iterasi
4. **Stratified K-Fold**: Menjaga proporsi kelas di setiap fold

![Confusion Matrix dan Metrik](images/p13-05-confusion-matrix.png)

*Gambar 13.3: Confusion matrix dan metrik evaluasi*

**[GEMINI IMAGE PROMPT]**
<prompt>
SUBJECT: Confusion matrix 2x2 dengan rumus metrik evaluasi (Accuracy, Precision, Recall, F1-Score)
STYLE: Clean flat vector illustration, educational computer science diagram, textbook quality, minimal design
LAYOUT: Left side shows 2x2 matrix, right side shows four metric formulas
COLORS: 
- TP/TN: #22c55e (green) background
- FP/FN: #ef4444 (red) background
- Primary: #2563eb (blue) for formulas
- Neutral: #6b7280 (gray) for labels
- Background: #ffffff (white)
ELEMENTS:
1. Left: 2x2 grid labeled "Prediksi Positif/Negatif" (columns) and "Aktual Positif/Negatif" (rows)
2. Cells: TP (green), FP (red), FN (red), TN (green)
3. Right: Four formula boxes:
   - Accuracy = (TP+TN)/(TP+TN+FP+FN)
   - Precision = TP/(TP+FP)
   - Recall = TP/(TP+FN)
   - F1 = 2·(P·R)/(P+R)
LABELS: All in Indonesian
SIZE: 900x500 pixels
FORMAT: PNG, white background
NEGATIVE: No gradients, no 3D effects, no photorealistic elements
</prompt>

### 🎬 Video Pembelajaran

| No | Judul Video | Channel | Durasi | Link |
|----|-------------|---------|--------|------|
| 1 | Naive Bayes Classifier Clearly Explained | StatQuest | 15:12 | https://www.youtube.com/watch?v=O2L2Uv9pdDA |
| 2 | Linear Regression: A Visual Introduction | 3Blue1Brown | 14:48 | https://www.youtube.com/watch?v=PaFPbb66DxQ |
| 3 | Confusion Matrix, Precision, Recall, F1 Explained | Data School | 10:25 | https://www.youtube.com/watch?v=Kdsp6soqA7o |
| 4 | Cross-Validation Clearly Explained | StatQuest | 6:05 | https://www.youtube.com/watch?v=fSytzGwwBVw |

### ✍️ Latihan Pemahaman

4. **Naive Bayes:** Dataset email (15 total: 6 spam, 9 bukan spam). Kata "promo" muncul di 5 spam dan 1 bukan spam. Kata "meeting" muncul di 1 spam dan 7 bukan spam. Klasifikasikan email baru yang mengandung "promo" tapi tidak mengandung "meeting"!

5. **Regresi Linear:** Hitung w₀ dan w₁ untuk data berikut:

   | x | y |
   |---|---|
   | 1 | 3 |
   | 2 | 5 |
   | 3 | 7 |
   | 4 | 9 |

6. **Confusion Matrix:** Sistem deteksi intrusi menghasilkan: TP=35, FP=10, FN=5, TN=150. Hitung Accuracy, Precision, Recall, dan F1-Score!

---

## 3. Eksplorasi Tools & Visualisasi (60 menit)

### 🛠️ Tools yang Direkomendasikan

| No | Tool | Deskripsi | Link |
|----|------|-----------|------|
| 1 | **Teachable Machine (Google)** | Latih model supervised learning di browser tanpa coding | https://teachablemachine.withgoogle.com/ |
| 2 | **Decision Tree Visualizer** | Visualisasi interaktif pembangunan decision tree step-by-step | http://www.r2d3.us/visual-intro-to-machine-learning-part-1/ |
| 3 | **MLPlayground** | Eksperimen berbagai algoritma ML secara visual | https://ml-playground.com/ |
| 4 | **Confusion Matrix Calculator** | Hitung metrik evaluasi dari confusion matrix | https://www.marcovanetti.com/pages/cfm/cfm.html |
| 5 | **Scikit-learn Docs** | Dokumentasi library ML Python paling populer | https://scikit-learn.org/stable/user_guide.html |

### Tugas Eksplorasi

**Tugas 3.1: Teachable Machine (20 menit)**
1. Buka Teachable Machine → pilih "Image Project"
2. Buat 2 kelas: "Kendaraan Militer" dan "Kendaraan Sipil"
3. Upload/ambil 10-15 gambar untuk setiap kelas
4. Klik "Train Model" dan amati proses training
5. Test model dengan gambar baru — catat hasilnya

**Tugas 3.2: Visual Introduction to ML (20 menit)**
1. Buka http://www.r2d3.us/visual-intro-to-machine-learning-part-1/
2. Scroll melalui seluruh visualisasi interaktif
3. Perhatikan bagaimana decision tree mempartisi ruang fitur
4. Jawab: Apa yang terjadi ketika tree terlalu dalam?

**Tugas 3.3: ML Playground (20 menit)**
1. Buka ML Playground
2. Pilih dataset "classification" dan algoritma "Decision Tree"
3. Ubah kedalaman tree dan amati perubahan decision boundary
4. Bandingkan dengan "Naive Bayes" — apa perbedaan boundary-nya?
5. Catat observasi tentang overfitting vs underfitting

---

## 4. Pendalaman dengan Video Lanjutan (60 menit)

### 🎬 Video Series

| No | Judul Video | Channel | Durasi | Link |
|----|-------------|---------|--------|------|
| 1 | Decision Trees: From Scratch | Sentdex | 22:15 | https://www.youtube.com/watch?v=sgQAhG5Q7iY |
| 2 | Random Forests Explained | StatQuest | 9:22 | https://www.youtube.com/watch?v=J4Wdy0Wc_xQ |
| 3 | Overfitting & Underfitting Explained | IBM Technology | 5:33 | https://www.youtube.com/watch?v=dBLZg-RqoLg |
| 4 | Gradient Descent, Step-by-Step | StatQuest | 23:55 | https://www.youtube.com/watch?v=sDv4f4s2SB8 |
| 5 | ROC and AUC Clearly Explained | StatQuest | 16:17 | https://www.youtube.com/watch?v=4jRBRDbJemM |

### 📚 Bacaan Tambahan

| No | Judul | Sumber | Link |
|----|-------|--------|------|
| 1 | A Visual Guide to Decision Trees | Medium | https://towardsdatascience.com/decision-trees-in-machine-learning-641b9c4e8052 |
| 2 | Naive Bayes for Text Classification | Towards Data Science | https://towardsdatascience.com/naive-bayes-classifier-81d512f50a7c |
| 3 | Understanding the Confusion Matrix | Towards Data Science | https://towardsdatascience.com/understanding-confusion-matrix-a9ad42dcfd62 |
| 4 | Bias-Variance Tradeoff | Scott Fortmann-Roe | http://scott.fortmann-roe.com/docs/BiasVariance.html |
| 5 | Russell & Norvig Ch.19 | Textbook | AIMA 4th Edition |

### Catatan Pendalaman

Setelah menonton video di atas, perhatikan hal-hal berikut:

1. **Random Forest** (video #2) adalah pengembangan decision tree yang menggunakan ensemble dari banyak tree — akan dibahas lebih lanjut di semester 5 (Machine Learning)
2. **Gradient Descent** (video #4) adalah metode optimisasi iteratif yang sangat penting di deep learning — pahami intuisi dasarnya
3. **ROC/AUC** (video #5) adalah metrik evaluasi lanjutan yang melengkapi precision/recall — berguna untuk membandingkan model

---

## 5. Latihan Soal Online (90 menit)

### Platform Latihan

| No | Platform | Topik | Link |
|----|----------|-------|------|
| 1 | **Kaggle Learn: Intro to ML** | Decision Trees, Random Forest | https://www.kaggle.com/learn/intro-to-machine-learning |
| 2 | **Google ML Crash Course** | Supervised Learning Fundamentals | https://developers.google.com/machine-learning/crash-course |
| 3 | **HackerRank: ML** | Classification Problems | https://www.hackerrank.com/domains/ai/machine-learning |

### Soal Latihan Mandiri

**Soal 1: Membangun Decision Tree (30 menit)**

Dataset patroli perbatasan:

| No | Waktu | Cuaca | Sensor | Ancaman? |
|----|-------|-------|--------|----------|
| 1 | Malam | Cerah | Aktif | Ya |
| 2 | Siang | Cerah | Aktif | Tidak |
| 3 | Malam | Hujan | Aktif | Ya |
| 4 | Siang | Cerah | Mati | Tidak |
| 5 | Malam | Cerah | Mati | Ya |
| 6 | Siang | Hujan | Aktif | Tidak |
| 7 | Malam | Hujan | Mati | Ya |
| 8 | Siang | Hujan | Mati | Tidak |

(a) Hitung entropy awal dataset  
(b) Hitung Information Gain untuk setiap atribut  
(c) Bangun decision tree lengkap  
(d) Klasifikasikan data baru: {Malam, Cerah, Aktif}

**Soal 2: Naive Bayes (20 menit)**

Sistem pendeteksi malware memiliki dua fitur:

| | Akses Registry | Traffic Anomali |
|---|---|---|
| Malware (20) | 16 | 14 |
| Bukan Malware (80) | 8 | 4 |

(a) Hitung P(Malware | Akses Registry, Traffic Anomali)  
(b) Hitung P(Bukan Malware | Akses Registry, Traffic Anomali)  
(c) Klasifikasi: file baru yang mengakses registry DAN memiliki traffic anomali  

**Soal 3: Evaluasi Model (20 menit)**

Dua model deteksi ancaman siber diuji pada 200 kasus:

**Model A:**

|  | Pred: Ancaman | Pred: Normal |
|---|:---:|:---:|
| Aktual: Ancaman | 28 | 12 |
| Aktual: Normal | 3 | 157 |

**Model B:**

|  | Pred: Ancaman | Pred: Normal |
|---|:---:|:---:|
| Aktual: Ancaman | 38 | 2 |
| Aktual: Normal | 15 | 145 |

(a) Hitung Accuracy, Precision, Recall, F1 untuk kedua model  
(b) Model mana yang lebih baik untuk pertahanan siber? Jelaskan!

**Soal 4: Regresi Linear (20 menit)**

Data hubungan frekuensi latihan dan skor kesiapan unit:

| Latihan/bulan (x) | Skor Kesiapan (y) |
|---|---|
| 5 | 60 |
| 10 | 72 |
| 15 | 80 |
| 20 | 90 |
| 25 | 95 |

(a) Hitung w₀ dan w₁ menggunakan Least Squares  
(b) Prediksi skor kesiapan jika frekuensi latihan = 30  
(c) Interpretasikan makna slope dalam konteks militer

---

## 6. Refleksi dan Diskusi (60 menit)

### Pertanyaan Refleksi

Jawab pertanyaan-pertanyaan berikut dalam bentuk paragraf (masing-masing 100-200 kata):

1. **Paradigma ML untuk Pertahanan:** Bandingkan supervised learning dan reinforcement learning untuk melatih drone otonom. Paradigma mana yang lebih cocok untuk fase training vs fase deployment? Mengapa?

2. **Trade-off Precision vs Recall:** Dalam konteks sistem peringatan dini (early warning system) rudal balistik, mengapa kita lebih memilih model dengan recall 99% dan precision 70% daripada model dengan recall 85% dan precision 95%? Apa konsekuensi operasional dari masing-masing?

3. **Overfitting di Dunia Nyata:** Sebuah decision tree dilatih menggunakan data radar 5 tahun terakhir dan mendapat akurasi 98% pada training data, tetapi hanya 72% pada data baru. Apa yang terjadi? Bagaimana cara memperbaikinya? Faktor apa di lingkungan pertahanan yang bisa menyebabkan perubahan distribusi data?

4. **Etika Machine Learning Militer:** Apakah keputusan engagement (tembak/tidak tembak) oleh senjata otonom boleh diserahkan sepenuhnya kepada model ML? Apa risiko jika model memiliki bias atau false positive tinggi? Bagaimana peran manusia (human-in-the-loop)?

### Forum Diskusi

Diskusikan dengan rekan mahasiswa (atau tulis refleksi pribadi):

- Mengapa evaluation metrics yang berbeda penting untuk aplikasi yang berbeda?
- Bagaimana cara menentukan threshold yang tepat antara "false alarm" dan "missed threat" dalam konteks pertahanan?
- Apakah Anda setuju bahwa model ML harus selalu memiliki human oversight dalam aplikasi militer?

---

## Checklist Belajar Mandiri

- [ ] Section 1: Review Paradigma ML dan Decision Tree selesai
- [ ] Section 2: Review Naive Bayes, Regresi Linear, dan Evaluasi Model selesai
- [ ] Section 3: Tools interaktif dieksplorasi
- [ ] Section 4: Video lanjutan ditonton
- [ ] Section 5: Latihan soal dikerjakan (min. 4 soal)
- [ ] Section 6: Refleksi ditulis

---

## Sumber Daya Tambahan (Opsional)

### 🎓 Kursus Online Gratis

| Kursus | Platform | Link |
|--------|----------|------|
| Introduction to Machine Learning | Coursera (Andrew Ng) | https://www.coursera.org/learn/machine-learning |
| Intro to Machine Learning | Kaggle Learn | https://www.kaggle.com/learn/intro-to-machine-learning |
| Machine Learning Crash Course | Google | https://developers.google.com/machine-learning/crash-course |
| Elements of AI | University of Helsinki | https://www.elementsofai.com/ |

### 📚 Buku & Artikel

**Textbooks:**
- Mitchell, T. (1997). *Machine Learning*. McGraw-Hill. Chapter 3 (Decision Tree Learning).
- Russell, S. & Norvig, P. (2020). *AIMA* (4th Ed.). Pearson. Chapter 19.
- Bishop, C.M. (2006). *Pattern Recognition and Machine Learning*. Springer. Chapter 4.

**Papers:**
- Quinlan, J.R. (1986). "Induction of Decision Trees." Machine Learning, 1(1), 81-106.
- Quinlan, J.R. (1993). "C4.5: Programs for Machine Learning." Morgan Kaufmann.

**Online Articles:**
- A Visual Introduction to ML: http://www.r2d3.us/visual-intro-to-machine-learning-part-1/
- Bias-Variance Tradeoff: http://scott.fortmann-roe.com/docs/BiasVariance.html
- Understanding Decision Trees: https://towardsdatascience.com/decision-trees-in-machine-learning-641b9c4e8052

### 🎥 Channel YouTube Rekomendasi

- **StatQuest with Josh Starmer** — Penjelasan statistik dan ML dengan visualisasi excellent
- **3Blue1Brown** — Intuisi matematika di balik ML
- **Sentdex** — Tutorial Python ML dari dasar
- **IBM Technology** — Penjelasan konsep AI/ML level enterprise
- **Normalized Nerd** — Decision tree dan information theory

### 🛠️ Software & Libraries

**Python Libraries:**
```python
# Scikit-learn - library ML paling populer
pip install scikit-learn

# Pandas - manipulasi data
pip install pandas

# Matplotlib - visualisasi
pip install matplotlib

# Contoh decision tree:
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.model_selection import cross_val_score
from sklearn.metrics import classification_report, confusion_matrix
```

**Online Tools:**
- Google Colab (notebook Python gratis): https://colab.research.google.com/
- Kaggle Kernels: https://www.kaggle.com/code

---

## Kunci Jawaban Latihan Pemahaman

### Section 1

1. **Identifikasi Paradigma:**
   - (a) **Unsupervised Learning** — deteksi anomali tanpa label (clustering/outlier detection)
   - (b) **Supervised Learning** — klasifikasi dengan database berlabel
   - (c) **Reinforcement Learning** — belajar melalui simulasi trial-and-error

2. **Hitung Entropy:**
   
   p(Ancaman) = 8/12 = 2/3, p(Aman) = 4/12 = 1/3
   
   $$H(S) = -(2/3)\log_2(2/3) - (1/3)\log_2(1/3)$$
   $$= -(2/3)(-0.585) - (1/3)(-1.585)$$
   $$= 0.390 + 0.528 = 0.918$$

3. **Information Gain untuk Altitude:**
   
   H(S) = 0.918 (dari soal 2)
   
   H(S_Tinggi): p(Anc) = 6/7, p(Aman) = 1/7
   $$H(S_{Tinggi}) = -(6/7)\log_2(6/7) - (1/7)\log_2(1/7) = 0.592$$
   
   H(S_Rendah): p(Anc) = 2/5, p(Aman) = 3/5
   $$H(S_{Rendah}) = -(2/5)\log_2(2/5) - (3/5)\log_2(3/5) = 0.971$$
   
   $$H(S|Altitude) = (7/12)(0.592) + (5/12)(0.971) = 0.345 + 0.405 = 0.750$$
   
   $$IG(S, Altitude) = 0.918 - 0.750 = 0.168$$

### Section 2

4. **Naive Bayes Email:**
   
   P(Spam) = 6/15 = 0.4, P(¬Spam) = 9/15 = 0.6
   
   P(promo|Spam) = 5/6 = 0.833, P(promo|¬Spam) = 1/9 = 0.111
   P(¬meeting|Spam) = 5/6 = 0.833, P(¬meeting|¬Spam) = 2/9 = 0.222
   
   P(Spam|evidence) ∝ 0.4 × 0.833 × 0.833 = 0.278
   P(¬Spam|evidence) ∝ 0.6 × 0.111 × 0.222 = 0.0148
   
   Normalisasi: P(Spam) = 0.278/(0.278+0.0148) = **94.9%** → Spam

5. **Regresi Linear:**
   
   | x | y | x² | xy |
   |---|---|---|---|
   | 1 | 3 | 1 | 3 |
   | 2 | 5 | 4 | 10 |
   | 3 | 7 | 9 | 21 |
   | 4 | 9 | 16 | 36 |
   | Σ | 10 | 24 | 30 | 70 |
   
   n=4, x̄=2.5, ȳ=6.0
   
   w₁ = (4×70 − 10×24)/(4×30 − 100) = (280−240)/(120−100) = 40/20 = **2.0**
   
   w₀ = 6.0 − 2.0×2.5 = **1.0**
   
   Model: ŷ = 1.0 + 2.0x (perfectly linear data)

6. **Confusion Matrix:**
   
   TP=35, FP=10, FN=5, TN=150
   
   - Accuracy = (35+150)/200 = **92.5%**
   - Precision = 35/45 = **77.8%**
   - Recall = 35/40 = **87.5%**
   - F1 = 2×(0.778×0.875)/(0.778+0.875) = **82.4%**

### Section 5

**Soal 1: Decision Tree Patroli Perbatasan**

(a) Entropy awal: 4 Ya, 4 Tidak → H(S) = 1.0

(b) Information Gain:

**Atribut Waktu:**
- Malam: {1,3,5,7} → 4 Ya, 0 Tidak → H = 0
- Siang: {2,4,6,8} → 0 Ya, 4 Tidak → H = 0
- IG(Waktu) = 1.0 − 0 = **1.0** ← perfect split!

**Atribut Cuaca:**
- Cerah: {1,2,4,5} → 2 Ya, 2 Tidak → H = 1.0
- Hujan: {3,6,7,8} → 2 Ya, 2 Tidak → H = 1.0
- IG(Cuaca) = 1.0 − 1.0 = **0**

**Atribut Sensor:**
- Aktif: {1,2,3,6} → 2 Ya, 2 Tidak → H = 1.0
- Mati: {4,5,7,8} → 2 Ya, 2 Tidak → H = 1.0
- IG(Sensor) = 1.0 − 1.0 = **0**

(c) Decision tree:
```
     [Waktu?]
     /      \
  Malam    Siang
    |        |
  [Ya]    [Tidak]
```
Tree hanya memerlukan satu atribut — Waktu memisahkan data sempurna.

(d) {Malam, Cerah, Aktif} → Waktu = Malam → **Ya (Ancaman)**

**Soal 2: Naive Bayes Malware**

P(Malware) = 20/100 = 0.2, P(¬Malware) = 80/100 = 0.8

P(Registry|Mal) = 16/20 = 0.8, P(Registry|¬Mal) = 8/80 = 0.1
P(Traffic|Mal) = 14/20 = 0.7, P(Traffic|¬Mal) = 4/80 = 0.05

(a) P(Mal|R,T) ∝ 0.2 × 0.8 × 0.7 = 0.112
(b) P(¬Mal|R,T) ∝ 0.8 × 0.1 × 0.05 = 0.004

Normalisasi:
- P(Malware) = 0.112/(0.112+0.004) = **96.6%**
- P(Bukan Malware) = 0.004/0.116 = **3.4%**

(c) Klasifikasi: **Malware** (probabilitas 96.6%)

**Soal 3: Perbandingan Model**

**Model A:** TP=28, FN=12, FP=3, TN=157
- Accuracy = 185/200 = 92.5%
- Precision = 28/31 = 90.3%
- Recall = 28/40 = **70.0%**
- F1 = 78.9%

**Model B:** TP=38, FN=2, FP=15, TN=145
- Accuracy = 183/200 = 91.5%
- Precision = 38/53 = 71.7%
- Recall = 38/40 = **95.0%**
- F1 = 81.7%

**Model B lebih baik** untuk pertahanan siber karena recall 95% (hanya 2 ancaman terlewat dari 40) jauh lebih penting daripada precision tinggi. Model A melewatkan 12 ancaman (30% ancaman lolos!) yang berpotensi menyebabkan kerusakan serius.

**Soal 4: Regresi Linear Kesiapan**

| x | y | x² | xy |
|---|---|---|---|
| 5 | 60 | 25 | 300 |
| 10 | 72 | 100 | 720 |
| 15 | 80 | 225 | 1200 |
| 20 | 90 | 400 | 1800 |
| 25 | 95 | 625 | 2375 |
| Σ | 75 | 397 | 1375 | 6395 |

n=5, x̄=15, ȳ=79.4

(a) w₁ = (5×6395 − 75×397)/(5×1375 − 75²) = (31975−29775)/(6875−5625) = 2200/1250 = **1.76**

w₀ = 79.4 − 1.76×15 = 79.4 − 26.4 = **53.0**

Model: ŷ = 53.0 + 1.76x

(b) Prediksi x=30: ŷ = 53.0 + 1.76×30 = 53.0 + 52.8 = **105.8**

(Catatan: skor >100 menunjukkan perlu diperhatikan batas domain model)

(c) **Interpretasi slope:** Setiap tambahan 1 kali frekuensi latihan per bulan meningkatkan skor kesiapan sebesar 1.76 poin. Ini menunjukkan bahwa latihan reguler memiliki dampak positif yang signifikan terhadap kesiapan tempur unit.

---

## License

This repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)**.

Commercial use is permitted, provided attribution is given to the author.

© 2026 Anindito
