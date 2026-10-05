# Calculus (Learning Happens Here)

Bagian ini berfokus pada mesin penggerak pembelajaran di Machine Learning dan Deep Learning: bagaimana model mengukur tingkat perubahan, memperbarui bobot secara adaptif, dan meminimalkan galat (*error*).

---

## 1. Differential Calculus

- [ ] **Functions and Graphs**
  * **Topik Terkait**: *Function*, *Multivariate Functions*, *Parameters of a Function*[cite: 4].
  * **Konsep**: Relasi yang memetakan input ke satu output tertentu, baik untuk variabel tunggal $f(x)$ maupun banyak variabel $f(x_1, x_2, \dots, x_n)$[cite: 4].
  * **Penerapan di ML/DL**: Model machine learning pada dasarnya adalah sebuah fungsi matematika bervalue banyak variabel (*multivariate function*) yang memetakan matriks fitur input menjadi target prediksi menggunakan sejumlah parameter (bobot $W$ dan bias $b$)[cite: 4].

- [ ] **Limits (Intuition Only)**
  * **Konsep**: Nilai pendekatan yang dituju oleh suatu fungsi saat inputnya mendekati suatu titik tertentu hingga selisihnya mendekati nol ($\Delta x \to 0$).
  * **Penerapan di ML/DL**: Memberikan intuisi perubahan sesaat (*instantaneous rate of change*) yang menjadi fondasi definisi turunan matematika dasar.

- [ ] **Derivatives and Gradients**
  * **Topik Terkait**: *What is Differentiation*, *Differentiation of a Constant*, *Power Rule*, *Sum Rule*, *Product Rule*, *Quotient Rule*, *Higher Order Derivatives*, *Matrix Differentiation*[cite: 4].
  * **Konsep**: Aturan diferensiasi dasar untuk menghitung laju perubahan fungsi serta *Matrix Differentiation* (turunan terhadap matriks/vektor)[cite: 4].
  * **Penerapan di ML/DL**: Digunakan untuk mengetahui seberapa sensitif fungsi galat terhadap perubahan nilai tiap parameter. *Matrix Differentiation* menjadi dasar kalkulasi analitik pada *Normal Equation* di regresi linier dan formulasi penurunan bobot lapisan *neural network*[cite: 4].

- [ ] **Partial Derivatives**
  * **Topik Terkait**: *Partial Differentiation*[cite: 4].
  * **Konsep**: Turunan fungsi multivariabel terhadap satu variabel tertentu dengan menganggap variabel lainnya konstan ($\frac{\partial f}{\partial x_i}$)[cite: 4].
  * **Penerapan di ML/DL**: Lapisan model memiliki jutaan bobot; turunan parsial memungkinkan model menghitung kontribusi spesifik dari satu bobot tunggal terhadap total galat tanpa mengacaukan bobot lainnya[cite: 4].

- [ ] **Chain Rule (Very Important)**
  * **Topik Terkait**: *Chain Rule*[cite: 4].
  * **Konsep**: Aturan turunan berantai untuk fungsi bersarang (*composite function*): $\frac{dz}{dx} = \frac{dz}{dy} \cdot \frac{dy}{dx}$[cite: 4].
  * **Penerapan di ML/DL**: Aturan paling vital di Deep Learning; merupakan fondasi algoritma **Backpropagation** untuk mengalirkan sinyal galat dari lapisan keluaran (*output layer*) mundur lapis demi lapis hingga ke lapisan masukan (*input layer*)[cite: 4].

- [ ] **Gradient as Direction of Steepest Descent**
  * **Topik Terkait**: *Gradient Descent*, *Gradient Descent with Multiple Parameters*[cite: 4].
  * **Konsep**: Gradien ($\nabla f$) adalah vektor turunan parsial yang selalu mengarah ke laju peningkatan fungsi paling curam; arah kebalikannya ($-\nabla f$) merupakan arah penurunan paling curam (*steepest descent*)[cite: 4].
  * **Penerapan di ML/DL**: Menjadi arah kompas bagi algoritma optimasi untuk melangkah menuruni lembah fungsi kerugian guna menemukan parameter terbaik[cite: 4].

- [ ] **Local vs Global Minima**
  * **Topik Terkait**: *Maxima & Minima*[cite: 4].
  * **Konsep**: Titik minimum lokal adalah nilai terendah pada lingkungan sekitarnya, sedangkan titik minimum global adalah nilai terendah absolut di seluruh permukaan fungsi[cite: 4].
  * **Penerapan di ML/DL**: Memahami risiko model terjebak (*trapped*) di solusi suboptimal pada fungsi nonlinear kompleks di Deep Learning[cite: 4].

- [ ] **Convex vs Non-Convex Functions**
  * **Topik Terkait**: *Convex & Concave Loss Functions*, *Hessians*[cite: 4].
  * **Konsep**: Fungsi konveks hanya memiliki satu titik minimum tunggal (minimum global), sedangkan fungsi non-konveks memiliki banyak lembah, puncak, dan titik pelana (*saddle points*)[cite: 4].
  * **Penerapan di ML/DL**: Regresi Linier dan Logistic Regression memiliki fungsi objektif konveks (pasti konvergen ke solusi optimal). Sebaliknya, *Deep Neural Networks* memiliki lanskap non-konveks yang memerlukan strategi optimasi adaptif (seperti Adam atau SGD dengan momentum)[cite: 4].

---

## 2. Optimization Concepts

- [ ] **Cost / Loss Functions**
  * **Topik Terkait**: *Loss Functions*, *How to select a good Loss Function*, *Calculating Parameters of a Loss Function*, *Parametric vs Non-Parametric Models*[cite: 4].
  * **Konsep**: Fungsi matematis yang mengukur seberapa jauh selisih antara prediksi model dan target data nyata[cite: 4].
  * **Penerapan di ML/DL**: Menjadi kompas kuantitatif model; pemilihan fungsi kerugian disesuaikan dengan jenis tugas:
    * Regresi: *Mean Squared Error* (MSE), *Mean Absolute Error* (MAE)[cite: 4].
    * Klasifikasi: *Binary Cross-Entropy*, *Categorical Cross-Entropy*.

- [ ] **Gradient Descent**
  * **Topik Terkait**: *Gradient Descent*, *Gradient Descent with Multiple Parameters*[cite: 4].
  * **Konsep**: Algoritma optimasi iteratif untuk memperbarui bobot model secara bertahap: $w := w - \alpha \nabla L(w)$[cite: 4].
  * **Penerapan di ML/DL**: Mesin utama pelatihan model di ML/DL; diterapkan dalam varian *Batch Gradient Descent*, *Stochastic Gradient Descent* (SGD), dan *Mini-Batch Gradient Descent*[cite: 4].

- [ ] **Learning Rate Intuition**
  * **Konsep**: Skalar hiperparameter ($\alpha$) yang menentukan ukuran langkah (*step size*) pada setiap iterasi Gradient Descent.
  * **Penerapan di ML/DL**: 
    * Nilai terlalu besar: Algoritma dapat melompati titik minimum dan menyimpang (*diverge*).
    * Nilai terlalu kecil: Pelatihan model berjalan sangat lambat atau berhenti sebelum mencapai hasil optimal.

- [ ] **Saddle Points**
  * **Topik Terkait**: *Problems faced in Optimization*, *Hessians*[cite: 4].
  * **Konsep**: Titik pada permukaan fungsi di mana gradien bernilai nol, tetapi merupakan minimum pada satu dimensi dan maksimum pada dimensi lainnya (menyerupai bentuk pelana kuda)[cite: 4].
  * **Penerapan di ML/DL**: Di ruang dimensi tinggi (*deep networks*), hambatan utama optimasi bukanlah minimum lokal, melainkan titik pelana di mana gradien menjadi datar sehingga laju belajar model macet[cite: 4].

- [ ] **Vanishing & Exploding Gradients (Intuition)**
  * **Topik Terkait**: *Problems faced in Optimization*[cite: 4].
  * **Konsep**: Efek perkalian berantai turunan parsial (*chain rule*) pada jaringan yang dalam:
    * *Vanishing*: Nilai gradien menyusut mendekati nol sehingga lapisan depan berhenti belajar[cite: 4].
    * *Exploding*: Nilai gradien membesar tak terkendali hingga menyebabkan ketidakstabilan numerik (*NaN*)[cite: 4].
  * **Penerapan di ML/DL**: Mendasari lahirnya teknik arsitektur modern seperti fungsi aktivasi ReLU, inisialisasi bobot khusus (He/Xavier), *Batch Normalization*, serta koneksi pintas (*residual connections* pada ResNet).

- [ ] **Advanced Optimization Concepts: Hessians & Constrained Optimization**
  * **Topik Terkait**: *Hessians*, *Constrained Optimization Problem*[cite: 4].
  * **Konsep**:
    * **Hessian Matrix**: Matriks turunan parsial tingkat dua ($H_{ij} = \frac{\partial^2 f}{\partial x_i \partial x_j}$) yang mengukur kelengkungan (*curvature*) permukaan fungsi kerugian[cite: 4].
    * **Constrained Optimization**: Optimasi fungsi dengan batasan tertentu menggunakan metode pengali Lagrange (*Lagrange Multipliers*)[cite: 4].
  * **Penerapan di ML/DL**: Digunakan pada metode optimasi orde kedua (seperti metode Newton), analisis kestabilan kurvatur *loss surface*, serta perumusan matematis algoritma Support Vector Machines (SVM) dengan kendala margin[cite: 4].