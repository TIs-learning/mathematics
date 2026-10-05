# Probability + Linear Algebra in ML

Bagian ini merupakan titik temu antara Aljabar Linier dan Teori Probabilitas: bagaimana data berdimensi banyak dimodelkan bukan lagi sebagai angka skalar terpisah, melainkan sebagai vektor acak (*random vectors*) dengan relasi kovariansi matriks dalam ruang geometri berdimensi tinggi.

---

- [ ] **Multivariate Distributions**
  * **Topik Terkait**: *Multivariate Analysis*, *Random Variable*, *Probability Distribution of a Random Variable*, *Vector Spaces*[cite: 3, 5, 6].
  * **Konsep**: Perluasan konsep distribusi probabilitas dari satu variabel tunggal ke vektor variabel acak berdimensi-$d$:
    $$\mathbf{X} = [X_1, X_2, \dots, X_d]^T$$
    Distribusi gabungan (*joint distribution*) memodelkan sebaran probabilitas simultan di mana nilai dari satu fitur dapat bergantung atau berinteraksi dengan fitur lainnya[cite: 5, 6].
  * **Penerapan di ML/DL**: Setiap baris data pada dataset machine learning (misalnya data tabular dengan puluhan kolom fitur) adalah sampel yang ditarik dari suatu distribusi multivariat di ruang vektor fitur[cite: 3, 6].

- [ ] **Gaussian Distribution in Higher Dimensions (Multivariate Normal Distribution)**
  * **Topik Terkait**: *Normal Distribution*, *PDF of Continuous Variables*, *Determinant*, *Quadratic Forms*[cite: 3, 6].
  * **Konsep**: Generalisasi kurva lonceng Gaussian 1D ke ruang berdimensi-$d$, yang sepenuhnya ditentukan oleh dua parameter aljabar: vektor rata-rata pusat ($\boldsymbol{\mu} \in \mathbb{R}^d$) dan matriks kovarian ($\boldsymbol{\Sigma} \in \mathbb{R}^{d \times d}$)[cite: 6]:
    $$p(\mathbf{x}; \boldsymbol{\mu}, \boldsymbol{\Sigma}) = \frac{1}{(2\pi)^{d/2} |\boldsymbol{\Sigma}|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})\right)$$
    * **Peran Determinan Matriks ($|\boldsymbol{\Sigma}|$ atau $\det(\boldsymbol{\Sigma})$)**: Mengukur volume ruang pembagi untuk normalisasi kerapatan probabilitas total agar bernilai $1$[cite: 3, 6].
    * **Peran Bentuk Kuadratik (*Quadratic Form*)**: Suku $(\mathbf{x} - \boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})$ pada eksponen menentukan kontur elipsoid dari sebaran probabilitas[cite: 3].
  * **Penerapan di ML/DL**: 
    * **Gaussian Mixture Models (GMM)**: Mengelompokkan data kompleks sebagai gabungan dari beberapa distribusi Gaussian multivariat[cite: 6].
    * **Gaussian Processes (GP)**: Digunakan pada optimasi hiperparameter berbasis Bayesian dan estimasi ketidakpastian regresi non-parametrik[cite: 3].
    * **Linear Discriminant Analysis (LDA)**: Mengklasifikasikan data dengan asumsi tiap kelas mengikuti sebaran normal multivariat dengan matriks kovarian bersama.

- [ ] **Covariance Matrix Interpretation**
  * **Topik Terkait**: *Covariance*, *Covariance Matrix*, *Symmetric Matrices*, *Diagonal Matrices*, *Positive Definite Matrices*[cite: 3, 6].
  * **Konsep**: Matriks persegi simetris berukuran $d \times d$ di mana elemen diagonal utamanya adalah varians masing-masing fitur ($\sigma_i^2$), sedangkan elemen di luar diagonal (*off-diagonal*) adalah kovarians antar-pasangan fitur ($\text{Cov}(X_i, X_j)$)[cite: 3, 6].
  * **Interpretasi Geometris & Aljabar**:
    * **Matriks Simetris & Definit Positif**: Matriks kovarian selalu simetris ($A = A^T$) dan definit non-negatif/positif, sehingga nilai eigennya selalu riil dan tidak negatif[cite: 3].
    * **Bentuk Sebaran Data**: 
      * Jika semua nilai di luar diagonal adalah $0$ (matriks diagonal), fitur saling tidak berkorelasi dan sebaran kontur probabilitas berbentuk elips yang sejajar sumbu koordinat[cite: 3, 6].
      * Jika matriks diagonal dan semua variansnya sama, sebaran berbentuk bola bulat sempurna (*spherical*).
      * Jika nilai di luar diagonal bukan nol, kontur elips berputar miring, menandakan adanya korelasi antarfitur[cite: 6].
  * **Penerapan di ML/DL**: Menjadi input inti pada algoritma **Principal Component Analysis (PCA)** untuk merotasi ruang data menuju sumbu varians terbesar menggunakan nilai dan vektor eigen matriks kovarian[cite: 3, 6].

- [ ] **Mahalanobis Distance**
  * **Topik Terkait**: *Distance from Origin & Euclidean Distance*, *Inverse of a Matrix*, *Quadratic Forms*[cite: 3].
  * **Konsep**: Ukuran jarak antara titik data $\mathbf{x}$ dengan titik pusat distribusi $\boldsymbol{\mu}$ yang memperhitungkan korelasi antarvariabel serta skala varians masing-masing fitur[cite: 3, 6]:
    $$D_M(\mathbf{x}, \boldsymbol{\mu}) = \sqrt{(\mathbf{x} - \boldsymbol{\mu})^T \boldsymbol{\Sigma}^{-1} (\mathbf{x} - \boldsymbol{\mu})}$$
  * **Mengapa Lebih Unggul dari Jarak Euclidean di Ruang Multivariat**:
    1. **Skala Invarian**: Jarak Euclidean sangat bias terhadap fitur dengan rentang nilai besar, sedangkan jarak Mahalanobis menormalkan setiap fitur berdasarkan variansnya[cite: 3].
    2. **Mengatasi Korelasi**: Invers matriks kovarian ($\boldsymbol{\Sigma}^{-1}$) di dalam rumus bertindak mendistorsi ruang agar korelasi antarfitur dieliminasi terlebih dahulu sebelum jarak dihitung[cite: 3].
  * **Penerapan di ML/DL**: 
    * **Deteksi Pencilan Multivariat (*Multivariate Outlier Detection*)**: Titik data bisa terlihat normal jika dilihat pada fitur individual, tetapi menjadi pencilan ekstrem ketika korelasi antardua fitur diperhitungkan.
    * **Klasifikasi Berbasis Jarak**: Menghitung kedekatan sampel uji ke pusat klaster data yang memiliki bentuk sebaran elips condong[cite: 6].