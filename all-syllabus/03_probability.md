# Probability Theory (Uncertainty Handling)

Bagian ini berfokus pada cara machine learning memodelkan ketidakpastian (*uncertainty*), mengukur risiko, dan membuat keputusan berbasis data probabilistik saat menghadapi fenomena dunia nyata yang stokastik atau bising (*noisy*).

---

### 1. Dasar Probabilitas & Variabel Acak

- [ ] **Konsep Dasar Probabilitas**
  * **Topik Terkait**: *Basic Terms like Random Experiment, Trial, Outcome, Sample Space, Event*, *Types of Events*, *Empirical Probability vs Theoretical Probability*[cite: 5].
  * **Konsep**: Percobaan acak (*random experiment*), ruang sampel ($S$), kejadian (*event*), serta perbedaan probabilitas teoretis (berdasarkan asumsi matematika) versus empiris (berdasarkan frekuensi observasi data aktual)[cite: 5].
  * **Penerapan di ML/DL**: Dataset pelatihan pada dasarnya adalah sampel empiris dari distribusi populasi data di dunia nyata; evaluasi model mengukur probabilitas empiris keberhasilan prediksi.

- [ ] **Random Variables (Variabel Acak)**
  * **Topik Terkait**: *What is a Random Variable*[cite: 5].
  * **Konsep**: Fungsi yang memetakan hasil dari suatu proses atau percobaan acak ke dalam nilai numerik riil ($X: S \to \mathbb{R}$)[cite: 5].
  * **Penerapan di ML/DL**: Fitur input ($X$) dan target/label output ($Y$) dimodelkan sebagai variabel acak; model ML bertugas mempelajari hubungan ketergantungan antarvariabel tersebut.

- [ ] **Discrete vs Continuous Variables**
  * **Konsep**: 
    * **Variabel Diskrit**: Memiliki nilai terhitung atau kategori terpisah (misal: jumlah klik, label kelas 0 atau 1).
    * **Variabel Kontinu**: Memiliki nilai tak hingga dalam suatu rentang kontinu (misal: suhu, harga rumah, bobot neuron).
  * **Penerapan di ML/DL**: Menentukan pemilihan jenis model dan perlakuan fungsi objektif—tugas klasifikasi menangani variabel diskrit, sedangkan regresi menangani variabel kontinu.

---

### 2. Distribusi Probabilitas & Karakteristik Statistik

- [ ] **Probability Distributions (Distribusi Probabilitas)**
  * **Topik Terkait**: *Probability Distribution of a Random Variable*[cite: 5].
  * **Konsep**: Fungsi atau tabel matematis yang menggambarkan sebaran kemungkinan nilai yang bisa dimiliki oleh suatu variabel acak[cite: 5].
  * **Penerapan di ML/DL**: Model generatif (seperti VAE dan Diffusion Models) dirancang khusus untuk mempelajari dan mereplikasi distribusi probabilitas data asli.

- [ ] **PMF, PDF, CDF**
  * **Konsep**:
    * **PMF (*Probability Mass Function*)**: Menghitung probabilitas tepat untuk variabel diskrit: $P(X = x)$.
    * **PDF (*Probability Density Function*)**: Mengukur kerapatan probabilitas untuk variabel kontinu; probabilitas diperoleh dari luas area di bawah kurva fungsi kerapatan: $P(a \le X \le b) = \int_a^b f(x) dx$.
    * **CDF (*Cumulative Distribution Function*)**: Mengukur akumulasi probabilitas bahwa variabel bernilai kurang dari atau sama dengan nilai tertentu: $F(x) = P(X \le x)$.
  * **Penerapan di ML/DL**: Digunakan dalam sampling data, pembuatan ambang batas (*thresholding*) klasifikasi, dan pemodelan fungsi aktivasi berbasis probabilitas.

- [ ] **Expectation & Variance (Nilai Harapan & Varians)**
  * **Topik Terkait**: *Mean of a Random Variable*, *Variance of a Random Variable*[cite: 5].
  * **Konsep**:
    * **Expectation ($\mathbb{E}[X]$)**: Nilai rata-rata teoretis berbobot probabilitas dari variabel acak (titik pusat)[cite: 5].
    * **Variance ($\text{Var}(X)$)**: Ukuran seberapa jauh nilai variabel menyebar dari nilai harapannya[cite: 5].
  * **Penerapan di ML/DL**: Fungsi kerugian (*loss function*) pada dasarnya menghitung ekspektasi galat di seluruh sampel data; varians digunakan untuk mendiagnosis kestabilan estimasi model dan masalah *overfitting*.

---

### 3. Distribusi Umum di Machine Learning (Common Distributions)

- [ ] **Bernoulli Distribution**
  * **Konsep**: Distribusi probabilitas diskrit untuk percobaan tunggal dengan dua kemungkinan hasil: sukses ($1$) dengan probabilitas $p$, atau gagal ($0$) dengan probabilitas $1-p$.
  * **Penerapan di ML/DL**: Menjadi asumsi dasar pada masalah **Binary Classification** dan model **Logistic Regression**.

- [ ] **Binomial Distribution**
  * **Konsep**: Distribusi diskrit yang menyatakan banyaknya kejadian sukses sebanyak $k$ kali dalam $n$ percobaan Bernoulli yang independen.
  * **Penerapan di ML/DL**: Digunakan untuk pengujian hipotesis A/B testing dan pemodelan data frekuensi konversi.

- [ ] **Normal Distribution (Gaussian)**
  * **Konsep**: Distribusi kontinu berbentuk kurva lonceng simetris yang ditentukan oleh rata-rata ($\mu$) dan varians ($\sigma^2$).
  * **Penerapan di ML/DL**: Distribusi paling krusial di AI; diasumsikan sebagai sebaran *noise* galat pada regresi linier, digunakan pada inisialisasi bobot jaringan saraf (Xavier/He Normal), pengklasifikasi Gaussian Naive Bayes, serta ruang laten pada *Variational Autoencoders* (VAE).

- [ ] **Uniform Distribution**
  * **Konsep**: Distribusi di mana setiap nilai di dalam interval yang ditentukan memiliki peluang kejadian yang sama rata.
  * **Penerapan di ML/DL**: Digunakan secara luas untuk inisialisasi bobot acak (*random weight initialization*), *hyperparameter tuning* (Random Search), dan teknik augmentasi data acak.

- [ ] **Poisson Distribution**
  * **Konsep**: Distribusi diskrit yang menyatakan probabilitas terjadinya sejumlah peristiwa dalam interval waktu atau ruang tertentu dengan laju kejadian rata-rata tetap ($\lambda$).
  * **Penerapan di ML/DL**: Digunakan dalam pemodelan data cacah (*count data*), seperti memprediksi volume *traffic* jaringan, jumlah klik tautan per jam, atau kedatangan pengguna pada sistem antrean.

---

### 4. Hubungan Antarvariabel & Teori Bayes

- [ ] **Independence & Conditional Probability (Probabilitas Bersyarat)**
  * **Topik Terkait**: *Venn Diagrams*, *Joint Probability*, *Marginal Probability*, *Conditional Probability*, *Independent Events*, *Mutually Exclusive Events*[cite: 5].
  * **Konsep**:
    * **Joint Probability**: Peluang terjadinya dua atau lebih kejadian secara bersamaan, $P(A \cap B)$[cite: 5].
    * **Marginal Probability**: Probabilitas tanpa syarat dari suatu kejadian tunggal tanpa memedulikan hasil kejadian lain, $P(A)$[cite: 5].
    * **Conditional Probability**: Probabilitas suatu kejadian $A$ dengan syarat kejadian $B$ telah terjadi: $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$[cite: 5].
    * **Independent vs Mutually Exclusive**: Dua kejadian saling bebas jika $P(A \cap B) = P(A)P(B)$; saling lepas (*mutually exclusive*) jika keduanya tidak bisa terjadi bersamaan ($P(A \cap B) = 0$)[cite: 5].
  * **Penerapan di ML/DL**: Menjadi dasar penalaran jaringan probabilistik (Bayesian Networks), analisis dependensi fitur, dan perhitungan risiko bersyarat.

- [ ] **Bayes' Theorem**
  * **Topik Terkait**: *Bayes Theorem*[cite: 5].
  * **Konsep**: Teorema yang memperbarui keyakinan probabilitas (*posterior*) terhadap suatu hipotesis setelah mendapatkan bukti data baru (*evidence*)[cite: 5]:
    $$P(\theta \mid D) = \frac{P(D \mid \theta) P(\theta)}{P(D)}$$
  * **Penerapan di ML/DL**: Fondasi utama algoritma **Naive Bayes Classifier**, optimasi hiperparameter berbasis Bayes (*Bayesian Optimization*), serta pendekatan estimasi Bayesian (*Maximum A Posteriori* / MAP).

- [ ] **Likelihood vs Probability**
  * **Konsep**:
    * **Probability**: Menghitung peluang data/hasil baru dengan asumsi parameter model sudah diketahui tetap: $P(\text{Data} \mid \text{Parameter})$.
    * **Likelihood**: Menilai seberapa masuk akal parameter model tertentu jika diberikan data hasil observasi nyata yang sudah ada: $L(\text{Parameter} \mid \text{Data})$.
  * **Penerapan di ML/DL**: Menjadi fondasi konsep **Maximum Likelihood Estimation (MLE)**; fungsi kerugian standar seperti *Mean Squared Error* (MSE) dan *Cross-Entropy Loss* diturunkan secara matematis dari prinsip maksimisasi *likelihood* parameter model.