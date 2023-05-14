# Laporan Proyek Machine Learning - Ahmad Zein Al Wafi

## Project Overview

Pelayanan yang baik kepada pelanggan yang menggunakan layanan *e-business* dapat meningkatkan presentase prilaku *repeat-buying* [(Quan, N. *et al.* 2020)](http://m.growingscience.com/beta/msl/3389-the-influence-of-website-brand-equity-e-brand-experience-on-e-loyalty-the-mediating-role-of-e-satisfaction.html). Hal ini dapat diukur dan ditingkatkan melalui interaksi pelanggan serta pengalaman dan sangat erat kaitannya dengan loyalitas pelanggan [(Srivastavaa, M. & Rai, A. 2018)](https://www.sciencedirect.com/science/article/pii/S0970389618302416) sehingga hal ini menjadi urgensi untuk meningkatkan keuntungan perusahaan. Pembelajaran mesin ikut serta dalam bidang tersebut, salah satunya dalam perusahaan netflix yang memanfaatkan pembelajaran mendalam untuk memberikan kepuasan jangka panjang pada pelanggan melalui sistem rekomendasi yang baik [(Steck, H., *et al*. 2021)](https://ojs.aaai.org/index.php/aimagazine/article/view/18140). Sistem rekomendasi adalah sistem cerdas yang mampu untuk memberikan rekomendasi melalui metode tertentu melalui deteksi pola kesamaan [(Sharma, L., &  Gera, A., 2013)](https://www.academia.edu/download/38584474/IJETT-V4I5P132_1_.pdf). Sistem ini memiliki memampuan untuk menyaring informasi yang masif dengan efektif  [(Lu, L. *et al*. 2012)](https://www.sciencedirect.com/science/article/abs/pii/S0370157312000828), mendeteksi minat pengguna dan memberikan informasi terbaik [(Nagarnaik, P., & Thomas, A. 2015)](https://ieeexplore.ieee.org/abstract/document/7124857) sesuai kebutuhannya sehingga terpersonalisasi[(Isinyake, F., Folojami, Y., & Ojokoh, B. 2015)](https://www.sciencedirect.com/science/article/pii/S1110866515000341). Proyek  ini mencoba untuk mengutilisasi sistem rekomendasi sederhana, khususnya pada rekomendasi buku. Sistem rekomendasi ini penting untuk direalisasikan karena dapat dimanfaatkan dalam layanan *e-business* sampai *e-library* untuk meningkatkan pengalaman pengguna dan dampaknya tidak hanya pada dua belah pihak, tapi bahkan ke perekonomian negara melalui peningkatan mutu sumber daya manusia.

## Business Understanding

### Problem Statements

Memiliki suatu sistem rekomendasi yang dapat melakukan rekomendasi, khususnya pada proyek ini adalah sistem rekomendasi buku untuk pengguna dapat memberikan dampak baik yang signifikan bagi kedua belah pihak. Oleh karenanya dengan situasi ini, rumusan masalahnya adalah sebagai berikut

- Dapatkah sistem rekomendasi yang diajukan memberikan rekomendasi kepada pengguna dengan baik?
- Dapatkah sistem rekomendasi memberikan rekomendasi secara cepat dan mendekati waktu nyata?

### Goals

Untuk menjawab masalah tersebut, disusun tujuan dari proyek ini sebagai berikut.

- Mendapatkan sistem rekomendasi yang mampu memberikan rekomendasi kepada pengguna dengan baik
- Mendapatkan sistem rekomendasi yang mampu memberikan rekomendasi kepada pengguna secara cepat dan mendekati waktu nyata

### Solution Approach

Solusi yang diajukan untuk memenuhi goals diatas adalah sebagai berikut.

- Mengajukan metode Content Based Filtering untuk membuat sistem rekomendasi berbasis konten
- Mengajukan metode Colaborative Filtering untuk membuat sistem rekomendasi berbasis interaksi user terhadap buku

## Data Understanding

Data yang digunakan dalam proyek ini adalah data [goodbooks-10k](https://www.kaggle.com/datasets/zygmunt/goodbooks-10k) dari Kaggle Dataset. Kumpulan data ini berisi sepuluh ribu buku populer. Data ini memiliki enam file, namun pada proyek ini hanya akan menggunakan dua file dengan format csv yaitu **books** yang berisi data buku untuk membuat sistem rekomendasi berbasis content based filtering dan **ratings** yang berisi data *rating* yang diberikan oleh pengguna untuk membuat sistem rekomendasi berbasis colaborative filtering

### Variabel
#### Books
Pada file csv **books**, data memiliki sepuluh variabel sebagai berikut:
- **id:** id secara umum
- **book_id:** id buku
- **best_book_id:** id buku populer
- **work_id:** id buku berdasarkan pada *abstract sense*
- **books_count:** hitungan buku
- **isbn:**  *International Standard Book Number*
- **isbn13:** *13 digits International Standard Book Number*
- **authors:** penulis buku
- **original_publication_year:** tahun publikasi buku
- **original_title:** judul buku dari bahasa asli
- **title:** judul buku yang telah diterjemahkan
- **language_code:** kode bahasa yang dipakai buku
- **average_rating:** rating rata-rata
- **ratings_count:** jumlah rating yang dihitung
- **work_ratings_count:**  jumlah rating keseluruhan
- **work_text_reviews_count:** jumlah rating dengan teks
- **ratings_1:** jumlah pengguna yang memberikan rating 1
- **ratings_2:** jumlah pengguna yang memberikan rating 2
- **ratings_3:** jumlah pengguna yang memberikan rating 3
- **ratings_4:** jumlah pengguna yang memberikan rating 4
- **ratings_5:** jumlah pengguna yang memberikan rating 5
- **image_url:** tautan gambar
- **small_image_url:** tautan gambar dengan resolusi rendah
- 
#### Books
Pada file csv **ratings**, data memiliki tiga variabel sebagai berikut:
- **book_id:** id buku
- **user_id:** id pengguna
- **rating:** rating yang diberikan pengguna ke buku

### EDA

Data tersebut dapat dianalisis mula-mula dengan beberapa eksplorasi dan juga visualisasi.
Ditemukan beberapa insight berikut
- Data memiliki nilai *null* yang banyak pada bagian isbn, isbn13, dan language_code seperti pada gambar 1 berikut
\
![gambar1](https://drive.google.com/uc?export=view&id=1cDEaWxAbbk-qsy2qwt3lpxqahKbl6hvW)
Gambar 1
- Data memiliki kecenderungan tahun publikasi pada abad 19 keatas, namun ternyata ada buku kuno sebelum masehi seperti pada gambar 2 berikut
 ![gambar2](https://drive.google.com/uc?export=view&id=1uLh_whzhuTOCDEsM4DIC7piSAoOjkM5o)
Gambar 2
- Distribusi rata-rata rating yang diberikan memiliki spike di berberapa nilai seperti pada gambar 3 berikut
\
![gambar3](https://drive.google.com/uc?export=view&id=1Ibmxlcieka33f6f6JdoiiymqtZUsMevw)
Gambar 3 
- Distribusi rata-rata rating secara umum terlihat seperti distribusi normal dengan ekor yang panjang dengan nilai skewness -0.51 dan kurtosis 0.88 yang distribusinya terlihat seperti pada gambar 4 berikut
\
![gambar](https://drive.google.com/uc?export=view&id=1n3mYZ-Uhxt56AkYu4cpBukNs6GMZLyEv)
Gambar 4
- Distribusi bahasa sangat dominasi dengan bahasa inggris biasa, diikut dengan bahasa lainnya seperti pada gambar 5 berikut
\
![gambar](https://drive.google.com/uc?export=view&id=19EvC0ldt4WtX1UMfFH4ESaGK_d_vdqVT)
Gambar 5
- Id selain id umum memiliki korelasi yang sangat besar, kemudian nilai rating selain nilai rata-rata rating memiliki korelasi yang sangat besar seperti pada gambar 6 berikut
\
![gambar](https://drive.google.com/uc?export=view&id=1KfMdp8uaUYyZvT0r-wYaLgXuxuptRV-C)
Gambar 6

## Data Preparation
Persiapan data yang dilakukan agar sistem rekomendasi dapat dibuat sebagai berikut

### Feature Engineering
Ada dua metode yang diajukan untuk mengerjakan proyek ini, yaitu content based filtering dan collaborative filtering. Kedua metode tersebut memiliki metode *feature engineering* yang berbeda. Namun tujuannya kurang lebih sama dengan metode analisa teks pada umumnya, *feature engineering* yang digunakan dalam proyek ini ditujukan untuk memberikan representasi teks dalam bentuk yang bisa dikalkulasi atau dipahami dengan baik oleh mesin dengan melakukan suatu rekayasa. Berikut metode *feature engineering* yang digunakan.

#### Content Based Filtering 
Content Based Filtering akan menghitung kesamaan konten yang ada, dalam proyek ini fitur/variabel yang dipilih untuk dicari kesamaannya adalah original-title, authors, ratings-count, dan language-code. Untuk mengakomodasi hal tersebut, setiap variabel akan dikonkatenasi dan dijadikan tipe data string. Kemudian teks tersebut yang berisi kombinasi variabel akan diberikan bobot dengan metode TF-IDF. Ini adalah salah satu metode dalam *information retrieval* yang umum digunakan dalam pengolahan teks dimana setiap kata akan dikaitkan dengan suatu nilai bobot yang menunjukan seberapa relevan kata terhadap dokumen. TF merujuk pada akronim *Term Frequency* dimana suatu kata akan dihitung frekuensi kemunculannya di dalam teks. IDF merujuk pada akronim *Inverse Document Frequency* dimana suatu kata akan diidentifikasi nilai keumumannya atau koefisien seberapa sering kemunculan kata, hal ini dapat mengidentifikasi nilai keunikan dalam suatu dokumen teks sehingga kata yang jarang muncul akan lebih dikenali dengan bobot yang lebih besar, sebaliknya jika kata sering muncul maka akan diberikan bobot yang lebih rendah. Hasil dari TF-IDF ini akan menjadi vektor yang merepresentasikan teks. Dalam proyek ini, pembobotan TF-IDF akan dibantu dengan pustaka scikit-learn.

#### Colaborative Filtering
Colaborative Filtering akan menghitung kesamaan karakteristik atau tingkah laku dari pengguna, kemudian akan diakumulasikan dan direkayasa untuk memberikan rekomendasi ke pengguna lainnya yang memiliki karakteristik atau tingkah laku yang mirip. Dalam proyek ini, karakteristik pengguna yang akan direkayasa adalah pemberian rating, data ini memberikan informasi jika pengguna telah membaca buku tersebut dengan bukti rating yang telah diberikan. Data riwayat pengguna tersebut akan direkayasa dengan diberikan suatu vektor, dimana suatu pengguna akan direpresentasikan dengan *embedding vectors*. Hal ini sangat krusial untuk mengidentifikasi relasi yang kompleks dari entitas yang berbeda-beda. Dalam proyek ini, pembobotan *embeddings* akan dibantu dengan pustaka tensorflow.

## Modeling
Proyek ini mengajukan dua metode untuk membuat sistem rekomendasi, yaitu Content Based Filtering dan Colaborative Filtering. Kedua metode ini memiliki karakteristik yang berbeda serta memiliki kelebihan dan kekurangan masing-masing sebagai berikut

### Content Based Filtering
Metode ini mencari kesamaan suatu entitas dengan entitas lainnya dalam suatu data untuk memberikan rekomendasi, singkatnya rekomendasi diberikan berdasarkan kesamaan konten atau karakteristik item. Dalam proyek ini, metode ini dilakukan dengan memberikan representasi teks berupa vektor kemudian representasi tersebut akan dihitung ukuran kesamaanya dengan *cosine similarity*, suatu metode matematika yang menghitung kedekatan derajat busur antar vektor. Walaupun kadangkala vektor yang dimiliki data sangat banyak dan bervariatif, metode ini cukup andal karena kompleksitas perhitungannya yang rendah. Metode ini juga tidak berhubungan dengan pengguna, sehingga skalabilitas dan keandalannya sangat terjamin jika ada peningkatan pengguna yang signifikan. Hal ini mempermudah dalam *deployment* karena model tidak perlu diperbaharui, hanya perlu untuk vektorisasi tambahan pada entitas/konten tambahan. Namun model ini terlimitasi karena tidak terkait dengan karakteristik pengguna sehingga ketertarikan pengguna terhadap konten sulit untuk diidentifikasi. Metode ini membutuhkan metode *feature engineering* yang lengkap untuk menjadi model yang baik dalam memberikan rekomendasi. Berikut rekomendasi 10 entitas terbaik dari sampel.

**Sample Content Details - Content Based Filtering**
| Title | Author | Rating
| --- | --- | --- |
|The Hunger Games (The Hunger Games, #1) | Suzanne Collins | 4.34 |

**Top 10 Recomendation - Content Based Filtering**
| Title | Author | Rating
| --- | --- | --- |
| The Hunger Games Box Set | Suzanne Collins | 4.49 |
| Catching Fire | Suzanne Collins | 4.3 |
| Mockingjay | Suzanne Collins | 4.03 |
| Gregor the Overlander | Suzanne Collins | 3.99 |
| Gregor and the Curse of the Warmbloods | Suzanne Collins | 4.2 |
| Gregor and the Marks of Secret | Suzanne Collins | 4.21 |
| Gregor and the Prophecy of Bane | Suzanne Collins | 4.17 |
| Gregor and the Code of Claw | Suzanne Collins | 4.25 |
| Hunger  | Michael  Grant | 4.02 |
| A Hunger Like No Other | Kresley Cole | 4.21 |

### Colaborative Filtering
Metode ini memberikan rekomendasi dengan memperhatikan karakteristik pengguna lain terhadap interaksi konten yang dimiliki data. Ini artinya pengembang model tidak perlu memahami domain data sehingga lebih mudah untuk dikembangkan. Namun model sulit untuk dapat menangani konten baru yang ditambahkan, hal ini karena belum ada user yang berinteraksi dengan konten tersebut. Berikut adalah contoh sampel yang diambil dengan menggunakan parameter user_id=911

**Top 10 Recomendation - Colaborative Filtering**
| Title | Author | Rating
| --- | --- | --- |
| The Source of Magic (Xanth, #2) | Piers Anthony | 3.86 |
| Love Story | Erich Segal | 3.6 |
| Hothouse Flower | Lucinda Riley | 3.8 |
| The Night is for Hunting | John Marsden | 4.15 |
| The First Confessor | Terry Goodkind | 4.19 |
| Pinkalicious | Victoria Kann, Elizabeth Kann | 4.05 |
| Identical | Ellen Hopkins | 4.34 |
| How Soccer Explains the World: An Unlikely Theory of Globalization | Franklin Foer | 3.76 |
| The Next Accident | Lisa Gardner | 4.16 |
| Red | Ted Dekker | 4.3 |
## Evaluation

Metrik yang menjadi nilai keberhasilan model secara umum pada **kedua model** adalah waktu model saat dijalankan untuk mendapatkan rekomendasi. Hal ini akan merepresentasikan performa model untuk diterapkan pada studi kasus dimana membutuhkan sistem rekomendasi yang cepat dan andal. Sistem rekomendasi yang baik adalah sistem yang tidak memberatkan perangkat komputasi dan terjaga keandalannya terhadap peningkatan pengguna. Dalam hal ini metode Content Based Learning menjadi pemenangnya. Dalam pengambilan sampel yang dilakukan dengan kedua metode, Content Based Learning dengan kemampuannya untuk memberikan rekomendasi dengan waktu sekitar 0.05 detik, berbeda dengan Colaborative Filtering yang membutuhkan waktu sekitar 1.5 detik. Dalam proyek ini berarti Content Based Learning 30 kali lebih cepat dibanding Colaborative Filtering dan berhasil menjadi sistem rekomendasi yang mendekati waktu nyata.

Pada **Content Based Learning**, *intersection over union*(IoU) dapat digunakan, namun dalam proyek ini dengan aturan yang sederhana saja. IoU atau kadang dikenal dengan *jaccard similarity* akan menghitung irisan(yaitu kesamaan) terhadap gabungan(yaitu keseluruhan data tanpa duplikat). IoU dimodifikasi dengan memberikan syarat khusus, dalam judul jika ada satu kata yang sama dengan judul dalam konten yang lain maka dihitung sebagai irisan, dalam author jika memiliki author yang sama dengan konten lain maka dihitung sebagai irisan. Dalam sampel yang diambil, judul memiliki presentase kesamaan 3/10 atau 30%, sedangkan pada author memiliki kesamaan 8/10 atau 80%. Dapat dilihat sistem rekomendasi dapat sangat baik dalam memberikan rekomendasi.

Kemudian untuk **Colaborative Filtering**, *Mean Square Error*(MSE) atau *Square Average Error* (MAE) dapat digunakan. Estimator ini menghitung rata-rata dari kesalahan kuadrat atau perbedaan rata-rata kuadrat pada estimasi nilai terhadap nilai yang sesungguhnya. Salah satu karakteristik dari MAE adalah tidak memberikan bias ekstrim dalam hal error. Jika ada outlier atau kesalahan yang besar, itu akan sama beratnya dengan prediksi lainnya. Metrik evaluasi ini cocok pada metode ini, dimana dalam proyek ini mendapat MAE sebesar 0.4765 pada akhir pelatihan, nilai MAE menandakan sistem rekomendasi cukup baik dalam memberikan rekomendasi. Grafik riwayat pelatihan dapat dilihat pada gambar 7 berikut.
![gambar](https://drive.google.com/uc?export=view&id=1BgjGKOSX-dNcR26_3gAVu-H0G7uXcDDi)
Gambar 7
## Referensi
- Quan, N., Chi, N. T. K. C., Nhung, D., Ngan, N., & Phong, L. (2020). The influence of website brand equity, e-brand experience on e-loyalty: The mediating role of e-satisfaction. Management Science Letters, 10(1), 63-76.
- Srivastava, M., & Rai, A. K. (2018). Mechanics of engendering customer loyalty: A conceptual framework. IIMB management review, 30(3), 207-218.
- Sharma, L., & Gera, A. (2013). A survey of recommendation system: Research challenges. International Journal of Engineering Trends and Technology (IJETT), 4(5), 1989-1992.
- Steck, H., Baltrunas, L., Elahi, E., Liang, D., Raimond, Y., & Basilico, J. (2021). Deep learning for recommender systems: A Netflix case study. AI Magazine, 42(3), 7-18.
- Lü, L., Medo, M., Yeung, C. H., Zhang, Y. C., Zhang, Z. K., & Zhou, T. (2012). Recommender systems. Physics reports, 519(1), 1-49.
- Nagarnaik, P., & Thomas, A. (2015, February). Survey on recommendation system methods. In 2015 2nd International Conference on Electronics and Communication Systems (ICECS) (pp. 1603-1608). IEEE.
- Isinkaye, F. O., Folajimi, Y. O., & Ojokoh, B. A. (2015). Recommendation systems: Principles, methods and evaluation. Egyptian informatics journal, 16(3), 261-273.