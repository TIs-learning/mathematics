# Information Theory (Modern ML Intuition)

Bagian ini berfokus pada cara mengukur ketidakpastian (*uncertainty*), menghitung kandungan informasi dalam data, serta mengukur seberapa jauh perbedaan antara dua distribusi probabilitas—fondasi utama fungsi kerugian (*loss function*) klasifikasi modern dan algoritma berbasis pohon.

---

- [ ] **Entropy**
  * **Konsep**: Ukuran ketidakpastian, keacakan, atau rata-rata kandungan informasi yang dihasilkan oleh suatu variabel acak diskrit ($X$):
    $$H(P) = -\sum_{x} P(x) \log_2 P(x)$$
    Jika probabilitas suatu kejadian bernilai pasti ($P=1$), nilai entropinya $0$ (tidak ada kejutan/informasi baru). Nilai entropi mencapai titik maksimum saat semua kemungkinan memiliki peluang yang sama rata (*uniform* / paling tidak pasti).
  * **Penerapan di ML/DL**: Mengukur tingkat kemurnian (*impurity*) data dalam suatu kelompok sampel; semakin rendah nilai entropi, semakin homogen atau bersih data tersebut.

- [ ] **Cross-Entropy**
  * **Konsep**: Ukuran jumlah rata-rata bit/informasi yang dibutuhkan untuk mengenali suatu peristiwa jika kita menggunakan distribusi probabilitas perkiraan ($Q$) alih-alih distribusi aslinya ($P$):
    $$H(P, Q) = -\sum_{x} P(x) \log Q(x)$$
  * **Penerapan di ML/DL**: Menjadi fungsi kerugian standar (*loss function*) pada klasifikasi:
    * **Binary Cross-Entropy (BCE)**: Untuk klasifikasi dua kelas (menggunakan aktivasi Sigmoid).
    * **Categorical Cross-Entropy (CCE)**: Untuk klasifikasi multi-kelas (menggunakan aktivasi Softmax). Di sini, $P$ adalah label target sebenarnya (*one-hot vector*), dan $Q$ adalah probabilitas prediksi keluaran model.

- [ ] **KL Divergence (Kullback-Leibler Divergence)**
  * **Konsep**: Sering disebut *Relative Entropy*; mengukur seberapa besar inefisiensi atau penyimpangan distribusi probabilitas pendekatan ($Q$) terhadap distribusi acuan yang sebenarnya ($P$):
    $$D_{KL}(P \parallel Q) = \sum_{x} P(x) \log \left( \frac{P(x)}{Q(x)} \right) = H(P, Q) - H(P)$$
    Karakteristik penting: Nilainya selalu non-negatif ($D_{KL} \ge 0$), bernilai $0$ jika dan hanya jika kedua distribusi identik ($P = Q$), serta bersifat asimetris ($D_{KL}(P \parallel Q) \ne D_{KL}(Q \parallel P)$).
  * **Penerapan di ML/DL**: 
    * **Variational Autoencoders (VAE)**: Sebagai suku regularisasi pada fungsi objektif untuk memaksa distribusi ruang laten (*latent distribution*) menyerupai distribusi normal standar (*standard Gaussian*).
    * **Knowledge Distillation**: Mentransfer pengetahuan dari model guru (*teacher*) yang besar ke model murid (*student*) yang ringkas.
    * **Penyelarasan LLM (RLHF)**: Mencegah keluaran model bahasa menyimpang terlalu jauh dari model dasar (*base policy*).

- [ ] **Information Gain**
  * **Konsep**: Pengurangan nilai entropi (penurunan ketidakpastian) setelah suatu dataset dipilah berdasarkan atribut/fitur tertentu:
    $$IG(T, a) = H(T) - H(T \mid a)$$
    di mana $H(T)$ adalah entropi sebelum pemisahan, dan $H(T \mid a)$ adalah rata-rata entropi tertimbang setelah pemisahan menggunakan fitur $a$.
  * **Penerapan di ML/DL**: Kriteria matematis utama untuk menentukan aturan pemisahan cabang (*splitting feature*) pada algoritma pohon keputusan klasik (*Decision Trees* seperti ID3) dan *Random Forest*. Fitur dengan *Information Gain* terbesar akan dipilih sebagai simpul pemisah (*split node*).

- [ ] **Why Cross-Entropy is Used in Classification**
  * **Alasan Matematis & Praktis**:
    1. **Penalti Eksponensial Terhadap Kesalahan Fatal**: Fungsi $-\log(q)$ mendekati tak hingga ($\infty$) ketika model memprediksi probabilitas mendekati $0$ untuk kelas yang sebenarnya benar ($P=1$). Ini memaksa model memperbaiki prediksi salah secara agresif.
    2. **Mencegah Masalah Saturasi Gradien (*Plateau*)**: Jika klasifikasi menggunakan *Mean Squared Error* (MSE) bersama aktivasi Sigmoid/Softmax, gradiennya akan mengandung suku turunan $S'(z) = S(z)(1-S(z))$. Jika prediksi sangat salah, gradiennya justru mendekati nol sehingga model berhenti belajar (*vanishing gradient*). Sebaliknya, turunan dari Cross-Entropy yang dipadukan dengan Softmax/Sigmoid menghasilkan bentuk gradien linier yang sangat sederhana dan stabil:
       $$\frac{\partial L}{\partial z} = \hat{y} - y$$
    3. **Ekuivalen dengan Maximum Likelihood Estimation (MLE)**: Meminimalkan *Cross-Entropy Loss* secara matematis setara dengan meminimalkan *Negative Log-Likelihood* (NLL) dari distribusi probabilitas data target.