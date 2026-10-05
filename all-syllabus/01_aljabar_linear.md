# Linear Algebra (The Backbone of ML)

Roadmap ini menyatukan 12 pos utama dari peta belajar AI dengan rincian teknis operasional, skala prioritas, dan fungsi praktisnya dalam Machine Learning & Deep Learning.

---

### 1. Scalars, Vectors, Matrices, Tensors
- [ ] **What are Scalars**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Konsep**: Kuantitas numerik tunggal (elemen 0-dimensi)[cite: 3].
  * **Penerapan di ML/DL**: Fondasi dasar perhitungan komputasi numerik; digunakan untuk merepresentasikan nilai hiperparameter tunggal seperti *learning rate* ($\alpha$) dan nilai fungsi kerugian (*loss values*)[cite: 3].

- [ ] **What are Vectors (Row & Column Vectors)**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Larik (array) angka 1-dimensi dalam bentuk baris (*row vector*) maupun kolom (*column vector*)[cite: 3].
  * **Penerapan di ML/DL**: Di ML digunakan untuk merepresentasikan satu baris sampel data (*data points*); di DL merepresentasikan vektor fitur (*features*), bobot neuron (*weights*), dan bias[cite: 3]. Perbedaan baris vs kolom menentukan keabsahan dimensi pada operasi perkalian matriks di lapisan *neural network*[cite: 3].

- [ ] **What are Matrices & Types of Matrices**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Larik angka 2-dimensi yang tersusun atas baris dan kolom[cite: 3].
  * **Penerapan di ML/DL**: Merepresentasikan tabel dataset (*batch of data*), kumpulan bobot antarlapisan model, atau operator transformasi[cite: 3]. Jenis matriks khusus seperti *Identity Matrix* ($I$) berperan sebagai elemen netral perkalian, dan *Sparse Matrix* digunakan untuk menghemat memori saat menangani data berdimensi tinggi yang didominasi angka nol (seperti TF-IDF atau graf)[cite: 3].
  
- [ ] **What are Tensors & Data Representation**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Generalisasi dari skalar (0D), vektor (1D), dan matriks (2D) ke ruang berdimensi lebih tinggi ($N$-D array)[cite: 3].
  * **Penerapan di ML/DL**: Digunakan untuk menyimpan dan memanipulasi data multidimensi:
    * 1D Tensor: Data deret waktu (*time-series*)[cite: 3].
    * 2D Tensor: Data tabular (Baris data $\times$ Fitur)[cite: 3].
    * 3D Tensor: Data sekuensial teks (Ukuran Batch $\times$ Panjang Kalimat $\times$ Dimensi Embedding)[cite: 3].
    * 4D Tensor: Data gambar (Ukuran Batch $\times$ Tinggi $\times$ Lebar $\times$ Kanal Warna RGB)[cite: 3].
    * 5D Tensor: Data video (Batch $\times$ Frame $\times$ Tinggi $\times$ Lebar $\times$ Kanal)[cite: 3].

---

### 2. Vector and Matrix Operations
- [ ] **Scalar-Vector Operations (Shifting & Scaling)**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Penjumlahan/pengurangan skalar terhadap vektor (*shifting*) berguna untuk pemusatan data (*centering*) dan koreksi bias[cite: 3]. Perkalian/pembagian skalar (*scaling*) digunakan untuk penskalaan data dan pengaturan langkah pembaruan pada algoritma optimasi (*learning rate scaling*)[cite: 3].
- [ ] **Vector-Vector Addition & Subtraction**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Operasi elementer untuk menggabungkan representasi fitur dan menghitung pembaruan vektor bobot: $w_{baru} = w_{lama} - \alpha \nabla L$[cite: 3].
- [ ] **Matrix Equality, Addition, Subtraction, & Scalar Operations**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Memeriksa konvergensi algoritma optimasi (apakah matriks bobot sudah berhenti berubah) serta melakukan penyesuaian parameter serempak[cite: 3].
- [ ] **Hadamard Product `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Konsep**: Perkalian elemen-demi-elemen (*element-wise product*, simbol $\odot$) antar dua matriks berukuran sama[cite: 3].
  * **Penerapan di ML/DL**: Digunakan secara intensif pada mekanisme pintu (*gating mechanism*) arsitektur RNN, LSTM, dan GRU untuk menyaring aliran informasi[cite: 3].
- [ ] **Tensor Operations**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Manipulasi bentuk data meliputi penataan ulang dimensi (*reshaping*), perataan (*flattening*), pertukaran sumbu (*permutation/transposition*), serta operasi *broadcasting* pada PyTorch/TensorFlow[cite: 3].

---

### 3. Dot Product & Geometric Interpretation
- [ ] **Dot Product of 2 Vectors**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Perkalian dua vektor yang menghasilkan kuantitas skalar tunggal[cite: 3].
  * **Penerapan di ML/DL**: Operasi komputasi paling fundamental di AI; digunakan untuk menghitung jumlah berbobot (*weighted sum*: $z = w^T x + b$) pada setiap neuron dan mengukur proyeksi data[cite: 3].
- [ ] **Angle between 2 Vectors & Cosine Similarity**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Mengukur selisih arah orientasi antardua vektor tanpa memedulikan panjang magnitudonya[cite: 3].
  * **Penerapan di ML/DL**: Digunakan untuk sistem rekomendasi, pencarian kemiripan dokumen, serta pembandingan vektor semantik (*embeddings*) di NLP[cite: 3].
- [ ] **Projection of a Vector**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Memproyeksikan satu vektor ke vektor/sumbu lain; merupakan dasar geometris dari reduksi dimensi dan visualisasi fitur ruang tinggi ke ruang rendah[cite: 3].
- [ ] **Equation of a Line in n-D (Hyperplane)**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Generalisasi garis lurus ke ruang dimensi tinggi; menjadi dasar matematis garis regresi linier serta *decision boundary* (*hyperplane*) untuk pemisahan kelas pada Support Vector Machines (SVM) dan Logistic Regression[cite: 3].
- [ ] **Cross Product `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Konsep & Penerapan**: Menghasilkan vektor yang tegak lurus terhadap bidang dua vektor asal; terbatas pada ruang 3 dimensi dan umum digunakan pada grafik komputer atau pemrosesan visi komputer spasial 3D[cite: 3].

---

### 4. Matrix Multiplication
- [ ] **Matrix Multiplication**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Perkalian baris dengan kolom antara dua matriks ($A_{m \times k} \times B_{k \times n} = C_{m \times n}$)[cite: 3].
  * **Penerapan di ML/DL**: Mesin utama komputasi *forward pass* pada *neural network* ($Y = XW$) serta formulasi analitik persamaan regresi[cite: 3].
- [ ] **Matrix Multiplication as Composition**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Menggabungkan serangkaian transformasi linier bertahap menjadi satu matriks representasi tunggal[cite: 3].
  * **Penerapan di ML/DL**: Dasar pemahaman bagaimana jaringan saraf dalam (*deep neural networks*) bekerja, di mana setiap lapisan adalah fungsi transformasi yang diterapkan secara berurutan terhadap input[cite: 3].
- [ ] **Linear Transformation of Non-Square Matrix**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Matriks berukuran $m \times n$ (non-persegi) digunakan saat jumlah fitur berubah antar-lapisan jaringan, baik untuk memadatkan fitur (reduksi dimensi) maupun memproyeksikannya ke dimensi yang lebih tinggi (*feature expansion*)[cite: 3].

---

### 5. Identity, Transpose, Inverse
- [ ] **Identity Matrix**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Matriks diagonal persegi bernilai 1 ($I$); berfungsi sebagai elemen identitas ($AI = A$) dan dasar pembentukan matriks regularisasi[cite: 3].
- [ ] **Transpose of a Matrix ($A^T$)**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Membalik orientasi baris menjadi kolom; esensial untuk menyelaraskan dimensi saat menghitung dot product vektor serta kalkulasi aljabar bobot[cite: 3].
- [ ] **Determinant, Minor, Cofactor, & Adjoint**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Mengukur faktor perubahan volume ruang oleh transformasi matriks[cite: 3]. Digunakan pada distribusi normal multivariat, model generatif berbasis aliran (*flow-based models*), serta kalkulasi analitis invers matriks[cite: 3].
- [ ] **Inverse of a Matrix ($A^{-1}$)**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Digunakan untuk menyelesaikan sistem persamaan linier secara analitik, seperti persamaan normal regresi linier: $w = (X^T X)^{-1} X^T y$[cite: 3].
- [ ] **Moore-Penrose Pseudoinverse ($A^+$) `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Memberikan solusi invers semu untuk matriks singular atau matriks persegi panjang (di mana invers biasa tidak ada); sangat penting untuk solusi kuadrat terkecil (*least squares*) ketika matriks fitur tidak berderajat penuh[cite: 3].

---

### 6. Rank of a Matrix
- [ ] **Rank of a Matrix**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Konsep**: Jumlah maksimum baris atau kolom yang saling bebas linier di dalam matriks[cite: 3].
  * **Penerapan di ML/DL**: Menentukan solvabilitas sistem linier serta menyelidiki sifat matriks bobot (*low-rank approximation* untuk kompresi model AI seperti LoRA)[cite: 3].
- [ ] **Linear Independence**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Konsep**: Kondisi di mana tidak ada vektor dalam himpunan yang dapat dibentuk dari kombinasi linier vektor lainnya[cite: 3].
  * **Penerapan di ML/DL**: Mencegah masalah multikolinieritas (*collinearity*) pada regresi linier yang dapat menyebabkan varians membengkak dan estimasi koefisien menjadi tidak stabil; menjadi asumsi dasar independensi pada komponen utama PCA[cite: 3].

---

### 7. Systems of Linear Equations
- [ ] **Solving a System of Linear Equations**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Berbagai algoritma ML pada intinya bermuara pada pencarian solusi persamaan $Ax = b$[cite: 3]. Proses *backpropagation* pada DL dapat dipandang sebagai penyelesaian sistem persamaan untuk memperbarui parameter jaringan[cite: 3].
- [ ] **LU Decomposition `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Memfaktorkan matriks menjadi matriks segitiga bawah (*Lower*) dan atas (*Upper*) guna menyelesaikan persamaan linier secara komputasi efisien dan stabil[cite: 3].
- [ ] **QR Decomposition `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Memecah matriks menjadi matriks ortogonal ($Q$) dan segitiga atas ($R$); digunakan untuk stabilitas numerik saat menyelesaikan persoalan kuadrat terkecil regresi linier[cite: 3].

---

### 8. Linear Transformations
- [ ] **Linear Transformations & 3D Transformations**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Konsep**: Pemetaan data dari satu ruang ke ruang lain dengan tetap mempertahankan garis lurus dan posisi titik pusat origin[cite: 3].
  * **Penerapan di ML/DL**: Memberikan intuisi geometris bagaimana data diputar (*rotation*), diregangkan (*scaling*), atau digeser saat melewati representasi tersembunyi (*latent space*) jaringan saraf[cite: 3].
- [ ] **Vector Spaces**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Ruang tempat titik-titik data berada[cite: 3]. Di *supervised learning*, terdapat ruang fitur (*input space*) dan ruang label (*output space*)[cite: 3]. Tiap lapisan *neural network* pada dasarnya mentransformasikan satu ruang vektor input menjadi ruang vektor output yang baru[cite: 3].
- [ ] **Change of Basis `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Mengubah sistem koordinat data ke basis baru yang lebih bermakna; konsep inti di balik reduksi dimensi PCA untuk memproyeksikan data ke sumbu varians tertinggi[cite: 3].

---

### 9. Column Space & Null Space (Intuition Level)
- [ ] **Column Space and Null Space `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Konsep**:
    * **Column Space**: Seluruh rentang kombinasi linier yang dapat dibentuk oleh kolom-kolom matriks[cite: 3].
    * **Null Space**: Himpunan semua vektor solusi $x$ yang memenuhi persamaan homogen $Ax = 0$[cite: 3].
  * **Penerapan di ML/DL**: Menentukan apakah sistem persamaan memiliki solusi unik, tak hingga, atau tidak sama sekali; membantu memahami batasan kemampuan representasi model linier terhadap data[cite: 3].

---

### 10. Eigenvalues & Eigenvectors (Intuition + Usage)
- [ ] **Eigenvalues and Eigenvectors**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Konsep**: Vektor khusus ($v$) yang ketika dikenai transformasi linier oleh matriks $A$, arahnya tidak berubah dan hanya magnitudonya yang diskalakan oleh faktor skalar nilai eigen ($\lambda$): $Av = \lambda v$[cite: 3].
  * **Penerapan di ML/DL**: Memahami dinamika konvergensi algoritma optimasi serta menganalisis kestabilan gradien[cite: 3].
- [ ] **Eigenfaces `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Aplikasi klasik vektor eigen pada pengenalan wajah (*facial recognition*), di mana vektor eigen menangkap arah variasi fitur wajah yang paling dominan[cite: 3].
- [ ] **Eigen Decomposition `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Memfaktorkan matriks menjadi komponen vektor dan nilai eigen ($A = Q \Lambda Q^{-1}$)[cite: 3]. Menjadi dasar matematika algoritma PCA dan analisis struktur matriks kovarian[cite: 3]. *(Catatan: Di Roadmap AI makro, dekomposisi lanjut seperti SVD dan PCA ditempatkan di bab High ROI setelah memahami statistika)*[cite: 2, 3].

---

### 11. Orthogonality
- [ ] **Orthogonal Matrices**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Konsep**: Matriks persegi yang kolom-kolom dan baris-barisnya merupakan vektor satuan yang saling tegak lurus ($Q^T Q = I$)[cite: 3].
  * **Penerapan di ML/DL**: Mempertahankan panjang dan sudut vektor setelah transformasi[cite: 3]. Digunakan pada teknik inisialisasi bobot (*orthogonal weight initialization*) di jaringan saraf untuk mencegah gradien meledak (*exploding*) atau lenyap (*vanishing*)[cite: 3].
- [ ] **Unit Vectors & Basis Vectors**
  * **Prioritas**: 🔴 Very Important[cite: 3]
  * **Penerapan di ML/DL**: Standardisasi arah vektor untuk menjaga stabilitas pembaruan gradien dan menyusun kerangka koordinat ruang data[cite: 3].
- [ ] **Symmetric & Diagonal Matrices**
  * **Prioritas**: 🟡 Important[cite: 3]
  * **Penerapan di ML/DL**: Matriks simetris ($A = A^T$) selalu menghasilkan nilai eigen riil (contohnya Matriks Kovarian)[cite: 3]. Matriks diagonal digunakan untuk penskalaan variabel secara independen dan penyusunan jadwal *learning rate* adaptif[cite: 3].
- [ ] **Quadratic Forms & Positive Definite Matrices `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Penerapan di ML/DL**: Matriks definit positif memastikan kurvatur permukaan fungsi kerugian (*loss surface*) melengkung ke atas secara konveks, menjamin algoritma optimasi konvergen ke titik minimum global yang unik[cite: 3].

---

### 12. Norms & Distances (L1, L2)
- [ ] **Distance from Origin & Euclidean Distance `[L]`**
  * **Prioritas**: ⚪ Later / 🔴 Very Important[cite: 3]
  * **Konsep**: Mengukur panjang jarak garis lurus antara titik data ke origin atau antardua titik data di ruang berdimensi $n$ ($L_2$ distance)[cite: 3].
  * **Penerapan di ML/DL**: Digunakan pada algoritma berbasis kedekatan spasial seperti K-Means Clustering, K-Nearest Neighbors (KNN), serta formulasi fungsi *loss* Mean Squared Error (MSE)[cite: 3].
- [ ] **Vector Norms ($L_1, L_2$) `[L]`**
  * **Prioritas**: ⚪ Later[cite: 3]
  * **Konsep**: Fungsi yang memetakan vektor ke nilai skalar positif untuk merepresentasikan panjang/ukurannya[cite: 3].
  * **Penerapan di ML/DL**:
    * **Norma $L_1$ (Manhattan)**: Digunakan pada regularisasi L1 (Lasso) untuk menghasilkan model yang jarang (*sparse*) dan memilih fitur relevan secara otomatis[cite: 3].
    * **Norma $L_2$ (Euclidean)**: Digunakan pada regularisasi L2 (Ridge / *Weight Decay*) untuk mencegah bobot bernilai terlalu besar agar model tidak *overfitting*[cite: 3].
    * **Normalisasi DL**: Menjadi dasar kalkulasi *Batch Normalization* dan *Layer Normalization*[cite: 3].

---

### Tools & Libraries untuk Implementasi Kode
- [ ] **NumPy**: Pustaka komputasi numerik dasar Python untuk manipulasi array $N$-dimensi, operasi matriks (`np.dot`, `@`), transposisi (`.T`), dan invers (`np.linalg.inv`)[cite: 3].
- [ ] **SciPy `[L]`**: Pustaka komputasi saintifik lanjutan; menyediakan rutin dekomposisi matriks numerik berkecepatan tinggi (`scipy.linalg.lu`, `qr`, `svd`), optimasi fungsi, dan penanganan matriks renggang (*sparse matrices*)[cite: 3].