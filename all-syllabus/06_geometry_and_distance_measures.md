# Geometry & Distance Measures

Bagian ini berfokus pada intuisi geometris ruang data: bagaimana algoritma mengukur kedekatan (*proximity*), derajat kemiripan (*similarity*), dan orientasi arah antar-vektor fitur, serta memahami tantangan matematis saat data berada di ruang dimensi tinggi.

---

- [ ] **Euclidean Distance**
  * **Topik Terkait**: *Euclidean Distance between 2 vectors*, *Distance from Origin*, *Vector Norms ($L_2$)*[cite: 3].
  * **Konsep**: Jarak garis lurus terpendek antara dua titik/vektor di ruang berdimensi $n$ (dikenal sebagai norma $L_2$)[cite: 3]:
    $$d_{\text{Euclidean}}(u, v) = \|u - v\|_2 = \sqrt{\sum_{i=1}^{n} (u_i - v_i)^2}$$
  * **Penerapan di ML/DL**: Metrik jarak paling standar pada algoritma pengelompokan (*K-Means Clustering*), pencarian tetangga terdekat (*K-Nearest Neighbors / KNN*), serta dasar perumusan fungsi kerugian regresi seperti *Mean Squared Error* (MSE)[cite: 3].

- [ ] **Manhattan Distance**
  * **Topik Terkait**: *Vector Norms ($L_1$)*[cite: 3].
  * **Konsep**: Jarak tempuh berbasis kisi-kisi (*grid-based*) yang dihitung dari penjumlahan selisih nilai mutlak antar-koordinat (dikenal sebagai norma $L_1$ atau *City Block Distance*)[cite: 3]:
    $$d_{\text{Manhattan}}(u, v) = \|u - v\|_1 = \sum_{i=1}^{n} |u_i - v_i|$$
  * **Penerapan di ML/DL**: Digunakan pada algoritma yang membutuhkan ketahanan (*robustness*) lebih tinggi terhadap pencilan (*outliers*), dasar fungsi *loss* *Mean Absolute Error* (MAE), serta prinsip regularisasi L1 (Lasso) untuk seleksi fitur otomatis[cite: 3].

- [ ] **Cosine Similarity**
  * **Topik Terkait**: *Dot Product of 2 vectors*, *Angle between 2 vectors*, *Unit Vectors*[cite: 3].
  * **Konsep**: Ukuran kosinus dari sudut antara dua vektor bukan-nol; mengukur apakah kedua vektor mengarah ke arah orientasi yang sama tanpa terpengaruh oleh panjang magnitudonya[cite: 3]:
    $$\text{Cosine Similarity}(u, v) = \frac{u \cdot v}{\|u\|_2 \|v\|_2} = \cos(\theta)$$
    Rentang nilai berada di antara $-1$ (arah berlawanan mutlak), $0$ (saling tegak lurus/ortogonal/independen), hingga $+1$ (arah sejajar sempurna)[cite: 3].
  * **Penerapan di ML/DL**: Standar emas untuk mengukur kemiripan teks, pencarian dokumen semantik, sistem rekomendasi berbasis konten (*content-based filtering*), serta evaluasi vektor representasi (*embeddings*) pada model bahasa besar (LLM)[cite: 3].

- [ ] **Angle between Vectors**
  * **Topik Terkait**: *Angle between 2 vectors*, *Orthogonal Matrices*[cite: 3].
  * **Konsep**: Sudut ($\theta$) yang dibentuk oleh dua vektor di ruang berdimensi $n$:
    $$\theta = \arccos\left(\frac{u \cdot v}{\|u\|_2 \|v\|_2}\right)$$
  * **Penerapan di ML/DL**: Mengidentifikasi relasi dan dependensi arah antar-vektor fitur berdimensi tinggi[cite: 3]. Jika sudut $\theta = 90^\circ$ (dot product bernilai $0$), kedua vektor saling ortogonal/tegak lurus, yang berarti tidak ada korelasi atau proyeksi informasi yang saling tumpang tindih di antara keduanya[cite: 3].

- [ ] **High-Dimensional Intuition (Curse of Dimensionality)**
  * **Topik Terkait**: *Vector Spaces*, *Equation of a Line in n-D*, *Dimensionality Reduction Rationale*[cite: 3].
  * **Konsep**: Fenomena ketika volume ruang fitur bertambah secara eksponensial seiring bertambahnya jumlah dimensi ($d$), sehingga data yang ada menjadi sangat renggang (*sparse*). Di dimensi yang sangat tinggi:
    1. Hampir semua titik data saling berjauhan satu sama lain.
    2. Rasio selisih jarak antara titik terdekat (*nearest*) dan titik terjauh (*farthest*) mendekati nol:
       $$\lim_{d \to \infty} \frac{d_{\max} - d_{\min}}{d_{\min}} \to 0$$
    3. Intuisi geometris dimensi rendah (seperti 2D/3D) tidak lagi berlaku; hampir seluruh volume bola hiper berada di lapisan kulit terluarnya.
  * **Penerapan di ML/DL**: Menjelaskan mengapa algoritma berbasis jarak spasial (seperti KNN dan K-Means) mengalami penurunan performa drastis pada dataset dengan ribuan fitur tanpa adanya reduksi dimensi terlebih dahulu (seperti PCA atau t-SNE)[cite: 3]. Hal ini juga menjadi alasan diperlukannya regularisasi bobot untuk mencegah model menghafal derau (*noise*) dimensi tinggi[cite: 3].