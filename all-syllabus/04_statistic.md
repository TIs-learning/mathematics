# Statistics (From Data to Decisions)

Bagian ini berfokus pada pengambilan kesimpulan dari data: memahami bentuk sebaran, mendeteksi hubungan antarvariabel, menangani anomali, serta mengukur kestabilan model agar mampu menggeneralisasi dengan baik pada data baru.

---

### 1. Population vs Sample
- [ ] **Population vs Sample**
  * **Topik Terkait**: *Population vs Sample*, *Types of Data*[cite: 6].
  * **Konsep**: Populasi mencakup seluruh kumpulan data atau individu yang relevan dengan suatu masalah, sedangkan sampel adalah subset data yang diambil dari populasi tersebut[cite: 6].
  * **Penerapan di ML/DL**: Data pelatihan (*training set*) yang kita miliki hanyalah sebuah sampel dari seluruh kemungkinan data di dunia nyata (populasi)[cite: 6]. Konsep ini mendasari statistik inferensial untuk memprediksi seberapa baik model akan bekerja saat menghadapi data baru yang belum pernah dilihat (*unseen data*)[cite: 6]. Pemahaman jenis data (kuantitatif, kategorikal, ordinal) juga menentukan teknik pra-pemrosesan dan algoritma yang tepat[cite: 6].

---

### 2. Measures of Central Tendency
- [ ] **Measures of Central Tendency (Mean, Median, Mode)**
  * **Topik Terkait**: *Mean*, *Median*, *Mode*, *Weighted Mean `[L]`*, *Trimmed Mean `[L]`*[cite: 6].
  * **Prioritas**: 🔴 Extremely Important (Median), 🟡 Important (Mean), ⚪ Later (Mode, Weighted Mean, Trimmed Mean)[cite: 6].
  * **Konsep**: Ukuran ringkasan numerik yang menunjukkan letak nilai tipikal atau titik pusat suatu distribusi data[cite: 6].
  * **Penerapan di ML/DL**:
    * **Exploratory Data Analysis (EDA)**: Menilai gambaran umum distribusi setiap fitur numerik[cite: 6].
    * **Data Imputation**: Mengisi nilai yang hilang (*missing values*) menggunakan mean (jika berdistribusi normal tanpa pencilan) atau median (jika data memiliki pencilan atau condong/skewed)[cite: 6].
    * **Trimmed & Weighted Mean**: Menghitung titik tengah yang lebih stabil dengan memotong nilai ekstrem atau memberi bobot kepentingan berbeda pada sampel tertentu[cite: 6].

---

### 3. Measures of Dispersion
- [ ] **Measures of Dispersion (Spread & Variability)**
  * **Topik Terkait**: *Range*, *Variance*, *Standard Deviation*, *Quantiles and Percentiles*, *Skewness*, *Kurtosis `[L]`*[cite: 6].
  * **Konsep**: Mengukur tingkat keragaman, variabilitas, atau sebaran titik data di sekitar nilai pusatnya[cite: 6].
  * **Penerapan di ML/DL**:
    * **Varians & Standar Deviasi**: Mengukur kestabilan dan sebaran data; menjadi komponen utama dalam teknik penskalaan standardisasi (*StandardScaler*)[cite: 6].
    * **Kuantil & Persentil**: Menentukan ambang batas keputusan (*decision thresholds*) serta analisis segmentasi fitur[cite: 6].
    * **Skewness & Kurtosis**: Mendeteksi ketidaksimetrisan (*kemiringan*) dan ketebalan ekor data distribusi[cite: 6]. Data yang sangat condong (*skewed*) sering kali perlu ditransformasi (misal transformasi Log atau Box-Cox) agar memenuhi asumsi model linier[cite: 6].

---

### 4. Covariance
- [ ] **Covariance & Covariance Matrix**
  * **Topik Terkait**: *Covariance*, *Covariance Matrix*[cite: 6].
  * **Konsep**: Ukuran yang menunjukkan arah hubungan bersama antara dua variabel acak—apakah keduanya cenderung naik bersamaan (kovarians positif) atau berlawanan arah (kovarians negatif)[cite: 6]. Matriks kovarian merangkum nilai kovarians untuk setiap pasangan fitur dalam dataset[cite: 6].
  * **Penerapan di ML/DL**: 
    * **Reduksi Dimensi (PCA)**: Menjadi input utama dekomposisi matriks untuk menemukan arah varians terbesar dalam data (*eigenvectors*)[cite: 6].
    * **Clustering**: Digunakan pada *Gaussian Mixture Models* (GMM) untuk memodelkan bentuk klaster elips multivariat[cite: 6].

---

### 5. Correlation
- [ ] **Correlation Coefficients & Causation**
  * **Topik Terkait**: *Pearson Correlation Coefficient*, *Spearman Correlation Coefficient `[L]`*, *Correlation and Causation*[cite: 6].
  * **Konsep**: Derajat keeratan hubungan dua variabel yang nilainya dinormalisasi antara $-1$ hingga $+1$[cite: 6]. Pearson mengukur hubungan linier, sedangkan Spearman mengukur hubungan monotonik (bebas dari asumsi linearitas dan normalitas)[cite: 6].
  * **Penerapan di ML/DL**:
    * **Seleksi Fitur (Feature Selection)**: Mendeteksi dan membuang fitur yang saling berkorelasi sangat tinggi (*multicollinearity*) agar model tidak redundan dan lebih mudah diinterpretasikan[cite: 6].
    * **Korelasi vs Kausalitas**: Mengingatkan bahwa korelasi statistik semata tidak membuktikan hubungan sebab-akibat, sehingga model tidak terkecoh oleh relasi semu (*spurious correlations*)[cite: 6].

---

### 6. Bias & Variance
- [ ] **Bias-Variance Tradeoff**
  * **Konsep**: Dekomposisi galat (*error*) generalisasi model machine learning ke dalam dua sumber utama:
    * **Bias**: Kesalahan akibat asumsi model yang terlalu menyederhanakan pola data (*Underfitting*).
    * **Variance**: Kesalahan akibat sensitivitas model yang terlalu tinggi terhadap fluktuasi/noise pada data latih (*Overfitting*).
  * **Penerapan di ML/DL**: Panduan utama dalam memilih kompleksitas arsitektur model, menentukan kekuatan regularisasi (L1/L2), serta memilih strategi algoritma *Ensemble* (metode *Bagging* seperti Random Forest untuk memangkas varians, atau metode *Boosting* seperti XGBoost untuk memangkas bias)[cite: 6].

---

### 7. Sampling Techniques
- [ ] **Sampling & Resampling Methods**
  * **Topik Terkait**: *Sampling*, *Cross Validation*, *Bootstrapping `[L]`*[cite: 6].
  * **Konsep**: Teknik memilih sebagian subset data dari populasi yang mampu merepresentasikan sifat populasi secara akurat tanpa harus memproses keseluruhan data[cite: 6].
  * **Penerapan di ML/DL**:
    * **Pembagian Dataset**: *Train-Test-Validation Split* dan *Stratified Sampling* (menjaga proporsi kelas yang seimbang)[cite: 6].
    * **Cross-Validation**: *K-Fold Cross-Validation* untuk menguji ketahanan model di berbagai subset sampel[cite: 6].
    * **Bootstrapping `[L]`**: Pengambilan sampel acak dengan pengembalian (*resampling with replacement*); digunakan untuk estimasi interval keyakinan dan menjadi mesin utama algoritma ensemble (*Bagging/Random Forests*)[cite: 6].

---

### 8. Central Limit Theorem (Intuition)
- [ ] **Central Limit Theorem (CLT) & Standard Error**
  * **Topik Terkait**: *Sampling Distribution*, *Central Limit Theorem*, *Standard Error*[cite: 6].
  * **Konsep**: Teorema yang menyatakan bahwa distribusi rata-rata sampel akan mendekati distribusi normal seiring bertambahnya ukuran sampel, tanpa memedulikan bentuk sebaran data pada populasi aslinya[cite: 6]. *Standard Error* mengukur variabilitas dari rata-rata sampel tersebut[cite: 6].
  * **Penerapan di ML/DL**: Menjadi fondasi matematis bagi pengujian hipotesis (*Hypothesis Testing*), perancangan eksperimen komparasi model (*A/B Testing*), serta penentuan *Confidence Interval* untuk melaporkan keandalan performa metrik evaluasi[cite: 6].

---

### 9. Law of Large Numbers
- [ ] **Law of Large Numbers (LLN)**
  * **Topik Terkait**: *Law of Large Numbers*[cite: 6].
  * **Konsep**: Teorema probabilitas yang menjamin bahwa semakin besar ukuran sampel yang diobservasi, rata-rata sampel yang diperoleh secara matematis akan semakin konvergen mendekati nilai rata-rata (*expected value*) populasi yang sebenarnya.
  * **Penerapan di ML/DL**: Landasan teoretis mengapa penambahan volume data pelatihan (*scaling data*) dapat membuat estimasi parameter bobot model menjadi lebih stabil, akurat, dan mendekati pola objektif dunia nyata.

---

### 10. Outliers & Robustness
- [ ] **Outlier Detection & Robust Techniques**
  * **Topik Terkait**: *5 number summary and BoxPlot*, *Trimmed Mean `[L]`*, *QQ Plot*, *Chebyshev's Inequality `[L]`*, *Standardization & Normalization*[cite: 6].
  * **Konsep**: Pencilan (*outlier*) adalah nilai data ekstrem yang menyimpang jauh dari pola keseluruhan distribusi data[cite: 6]. *Robustness* adalah ketahanan metode komputasi terhadap distorsi yang disebabkan oleh pencilan tersebut.
  * **Penerapan di ML/DL**:
    * **Identifikasi Outlier**: Menggunakan grafik *BoxPlot* (metode rentang interkuartil / IQR) atau *QQ Plot* untuk memeriksa deviasi dari asumsi normalitas[cite: 6].
    * **Pembersihan & Transformasi**: Memutuskan penanganan pencilan apakah dipangkas (*trimmed*), dibatasi (*capping/winsorizing*), atau ditransformasi menggunakan penskalaan yang kebal outlier (*RobustScaler* berbasis median & IQR daripada *StandardScaler* berbasis mean & varians)[cite: 6].
    * **Pemilihan Fungsi Loss**: Menggunakan *Mean Absolute Error* (MAE / L1 loss) atau *Huber Loss* yang jauh lebih tahan (*robust*) terhadap outlier dibandingkan *Mean Squared Error* (MSE / L2 loss).