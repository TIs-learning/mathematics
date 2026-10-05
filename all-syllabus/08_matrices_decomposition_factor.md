# Matrix Factorization & Decomposition (High ROI)

Bagian ini merupakan puncak penerapan matematika di mana Aljabar Linier, Kalkulus, dan Statistika terintegrasi penuh: memecah matriks berukuran besar menjadi matriks-matriks komponen yang lebih sederhana guna memadatkan fitur, menyaring derau (*noise*), dan mengekstraksi pola laten tersembunyi[cite: 3, 6].

---

- [ ] **Eigen Decomposition**
  * **Topik Terkait**: *Eigen Decomposition `[L]`*, *Eigen Vectors and Eigen Values*, *Symmetric Matrices*[cite: 3].
  * **Prioritas**: ⚪ Later `[L]`[cite: 3]
  * **Konsep**: Memfaktorkan matriks persegi menjadi perkalian matriks vektor eigen dan matriks diagonal nilai eigen ($A = Q \Lambda Q^{-1}$)[cite: 3]. Jika matriksnya simetris (seperti matriks kovarian), vektor-vektor eigennya saling tegak lurus (*ortogonal*) dan nilai eigennya dijamin riil ($A = Q \Lambda Q^T$)[cite: 3].
  * **Penerapan di ML/DL**: Digunakan untuk memecahkan persoalan yang membutuhkan pemahaman terhadap struktur dasar penyusun data (seperti pada PCA) serta menganalisis sifat spektral dari matriks bobot model pada *deep learning*[cite: 3].

- [ ] **Singular Value Decomposition (SVD)**
  * **Topik Terkait**: *Singular Value Decomposition `[L]`*, *Orthogonal Matrices*, *Diagonal Matrices*[cite: 3].
  * **Prioritas**: ⚪ Later `[L]`[cite: 3]
  * **Konsep**: Generalisasi dari *Eigen Decomposition* yang dapat diterapkan pada sembarang matriks persegi panjang ($m \times n$), memecahnya menjadi tiga matriks komponen:
    $$A = U \Sigma V^T$$
    di mana $U$ dan $V$ adalah matriks ortogonal (vektor singular kiri dan kanan), serta $\Sigma$ adalah matriks diagonal yang memuat nilai singular (*singular values*) terurut dari yang terbesar[cite: 3].
  * **Penerapan di ML/DL**: 
    * **Reduksi Dimensi & Kompresi Data**: Membuang nilai-nilai singular terkecil untuk mendapatkan aproksimasi matriks berorde rendah (*low-rank approximation*)[cite: 3].
    * **Latent Semantic Analysis (LSA)**: Menemukan hubungan konsep/topik laten antar-dokumen dan kata pada pemrosesan bahasa alami (NLP)[cite: 3].
    * **Kompresi Model & Inisialisasi**: Digunakan untuk pemangkasan (*pruning*) ukuran bobot jaringan saraf dan inisialisasi parameter model di *deep learning*[cite: 3].

- [ ] **PCA Math Intuition (Principal Component Analysis)**
  * **Topik Terkait**: *Principal Component Analysis `[L]`*, *Covariance Matrix*, *Linear Independence*, *Change of Basis `[L]`*[cite: 3, 6].
  * **Prioritas**: ⚪ Later `[L]`[cite: 3]
  * **Konsep**: Merotasi kerangka koordinat data (*change of basis*) menuju sistem koordinat baru sedemikian rupa sehingga:
    1. Sumbu pertama (Komponen Utama 1) menangkap varians data terbesar[cite: 3, 6].
    2. Sumbu-sumbu berikutnya saling tegak lurus (*linearly independent* / tidak berkorelasi satu sama lain) dan menangkap sisa varians secara berurutan[cite: 3, 6].
    Secara matematis, arah komponen utama diperoleh langsung dari vektor eigen matriks kovarian data, dan besarnya varians yang ditangkap setara dengan nilai eigen yang bersesuaian[cite: 3, 6].
  * **Penerapan di ML/DL**: Menghilangkan derau (*noise removal*), mengatasi masalah multikolinieritas antarfitur, serta memproyeksikan data berdimensi tinggi ke ruang 2D/3D untuk visualisasi sebaran kelas atau representasi *learned embeddings*[cite: 3, 6].

- [ ] **Dimensionality Reduction Rationale (Alasan Rasional Reduksi Dimensi)**
  * **Topik Terkait**: *Linear Transformation of Non-square Matrix*, *Projection of a Vector*, *High-Dimensional Intuition*[cite: 3].
  * **Konsep**: Kebutuhan analitis untuk mentransformasikan data dari ruang berdimensi tinggi ($D$) ke ruang berdimensi lebih rendah ($d \ll D$) tanpa kehilangan informasi esensial dari data aslinya[cite: 3].
  * **Penerapan di ML/DL**:
    * **Mengatasi Kutukan Dimensi (*Curse of Dimensionality*)**: Menghilangkan kelangkaan data (*sparsity*) sehingga algoritma berbasis kedekatan spasial (seperti clustering atau regresi) dapat bekerja lebih optimal[cite: 3].
    * **Efisiensi Komputasi & Memori**: Mempercepat proses komputasi pelatihan model secara signifikan dan menghemat alokasi memori penyimpanan dataset[cite: 3].
    * **Pencegahan Overfitting**: Menyaring fitur-fitur redundan atau bising yang berpotensi membuat model menghafal pola derau data latih[cite: 3].