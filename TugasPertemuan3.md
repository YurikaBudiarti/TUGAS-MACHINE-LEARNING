Nama : Yurika Budiarti 

Kelas : TIF-A2

NPM : 41155050210047

Tugas Pertemuan 3

1.1.	Pengenalan komponen Decision Tree: root, node, leaf

Root (Akar)

•	Root adalah simpul pertama atau simpul awal dari Decision Tree. Di sinilah proses pembelahan (splitting) pertama terjadi berdasarkan fitur yang paling penting atau yang memberikan informasi paling besar.

•	Root node dipilih berdasarkan kriteria tertentu, seperti Gini Index atau Information Gain, tergantung pada algoritma yang digunakan untuk membangun Decision Tree.

•	Setelah root ditentukan, cabang-cabang akan berkembang dari node ini.


Node (Simpul)

•	Node adalah titik percabangan pada Decision Tree. Di setiap node, data dibagi berdasarkan satu fitur tertentu yang dipilih secara optimal untuk memisahkan data ke dalam kategori yang lebih homogen.

•	Ada dua jenis node:

•	Internal Node: Node yang memiliki cabang-cabang ke node berikutnya, sehingga belum mencapai hasil akhir. Proses pembelahan berlanjut hingga mencapai node daun.

•	Leaf Node (Daun): Node terakhir yang tidak memiliki cabang lebih lanjut, berisi klasifikasi atau hasil akhir dari proses pengambilan keputusan.


Leaf (Daun)

•	Leaf node adalah simpul akhir di Decision Tree yang tidak dapat dipecah lagi. Di sinilah keputusan atau prediksi akhir dibuat.

•	Setiap leaf merepresentasikan kelas atau nilai hasil dari model Decision Tree berdasarkan fitur-fitur yang telah diproses.

•	Ketika pengamatan atau instance sampai di leaf node, itu berarti Decision Tree telah selesai melakukan klasifikasi atau regresi, dan memberikan prediksi atau hasil berdasarkan data input.


1.2.	Pengenalan Gini Impurity

Gini Impurity adalah salah satu metrik yang digunakan dalam algoritma Decision Tree untuk mengukur seberapa baik suatu node membagi data ke dalam kelompok-kelompok tertentu. Semakin kecil nilai Gini Impurity, semakin baik node tersebut memisahkan data ke dalam kategori yang homogen (artinya, sebagian besar data dalam satu kelas yang sama). Metrik ini biasanya digunakan dalam CART (Classification and Regression Tree), sebuah varian dari Decision Tree.
 
Definisi:

Gini Impurity untuk suatu node diukur dengan menghitung peluang bahwa suatu data yang dipilih secara acak dari node tersebut salah diklasifikasikan jika diklasifikasikan berdasarkan distribusi kelas di node tersebut.

Secara matematis, Gini Impurity dihitung dengan rumus:

![image](https://github.com/user-attachments/assets/3d35355d-c99d-4569-a155-43e784a1e564)

•	Dimana Pi adalah proporsi sampel yang berada dalam kelas i di node tersebut.

•	n adalah jumlah total kelas.

Penjelasan:

Gini Impurity menghitung ketidakmurnian (impurity) atau seberapa beragam data dalam suatu node:

•	Nilai Gini Impurity = 0 menunjukkan bahwa semua sampel dalam node termasuk dalam satu kelas (node murni).

•	Nilai Gini Impurity mendekati 0.5 (maksimum untuk dua kelas) menunjukkan bahwa data dalam node terdistribusi secara merata di antara kelas-kelas yang ada, sehingga node sangat tidak murni.

1.3.	Pengenalan Information Gain

Information Gain (IG) adalah metrik yang digunakan dalam Decision Tree untuk mengukur efektivitas suatu fitur dalam membagi data ke dalam kelas-kelas yang berbeda. Metrik ini berasal dari teori informasi, dan secara umum digunakan dalam algoritma ID3 dan C4.5 untuk memilih fitur terbaik saat membuat pohon keputusan.

Definisi:

Information Gain mengukur pengurangan ketidakpastian atau pengurangan entropi dari satu set data setelah data tersebut dibagi berdasarkan suatu fitur tertentu. Semakin tinggi Information Gain, semakin baik fitur tersebut dalam membagi data menjadi kelompok yang lebih homogen.

Entropi:

Untuk memahami Information Gain, kita harus terlebih dahulu memahami Entropi. Entropi adalah ukuran ketidakmurnian atau ketidakpastian dalam suatu set data. didefinisikan sebagai:

![image](https://github.com/user-attachments/assets/725f41b8-12ad-483b-919c-2276e420235c)

Di mana:

•	Pi adalah probabilitas kemunculan dari kelas i dalam set data S.

•	nadalah jumlah total kelas.

Entropi bernilai 0 jika semua sampel dalam satu kelas (murni), dan mencapai nilai maksimum jika data terdistribusi secara merata ke semua kelas (tidak murni).

Information Gain:

Setelah kita menghitung entropi awal dari dataset, kita dapat menghitung Information Gain sebagai pengurangan entropi setelah data dibagi menggunakan fitur tertentu. Rumusnya:

![image](https://github.com/user-attachments/assets/b0e7e740-37bf-47ea-8c6f-3de14743ae78)

Dimana:

•	H(S) adalah entropi dari set data awal

•	A adalah fitur yang digunakan untuk membagi data

•	Sv adalah subset dari S untuk nilai v pada fitur A

Dengan kata lain, Information Gain adalah selisih antara entropi set data awal dan entropi rata-rata dari subset-subset yang dihasilkan setelah pembagian data.

Langkah-langkah Menghitung Information Gain:

1.	Hitung entropi awal dari dataset (sebelum data dibagi berdasarkan fitur).

2.	Bagi dataset berdasarkan suatu fitur menjadi beberapa subset.

3.	Hitung entropi rata-rata dari subset-subset tersebut.

4.	Kurangi entropi rata-rata dari entropi awal. Hasilnya adalah Information Gain untuk fitur tersebut.


1.4.	Membangun Decision Tree

Decision Tree adalah algoritma pembelajaran mesin yang digunakan untuk tugas klasifikasi dan regresi. Pohon keputusan ini menyerupai struktur seperti diagram alur (flowchart), di mana setiap simpul (node) merepresentasikan sebuah keputusan atau tes pada fitur, setiap cabang merepresentasikan hasil dari tes tersebut, dan setiap leaf node (node daun) mewakili keputusan akhir atau label.

Decision Tree bekerja dengan membagi data secara berulang kali berdasarkan fitur yang dipilih, sehingga menghasilkan struktur pohon yang dapat digunakan untuk memprediksi kelas atau nilai output baru.
 

Komponen Utama Decision Tree:

1.	Root Node: Simpul awal yang mewakili seluruh dataset dan pembelahan pertama berdasarkan fitur terbaik.

2.	Internal Node (Node): Simpul-simpul yang mewakili fitur yang digunakan untuk membagi data. Setiap node memiliki satu pertanyaan atau tes yang membagi data menjadi subset- subset yang lebih kecil.

3.	Leaf Node: Simpul terminal yang memberikan prediksi akhir. Leaf node tidak memiliki pembelahan lebih lanjut.

4.	Cabang (Branch): Menghubungkan node ke node lainnya dan mewakili hasil dari tes yang dilakukan di node sebelumnya.

Dimana:
•	H(S) adalah entropi dari set data awal
•	A adalah fitur yang digunakan untuk membagi data
•	Sv adalah subset dari S untuk nilai v pada fitur A

adalah proporsi sampel yang jatuh ke subset Sv.
Dengan kata lain, Information Gain adalah selisih antara entropi set data awal dan entropi rata-rata dari subset-subset yang dihasilkan setelah pembagian data.
Langkah-langkah Menghitung Information Gain:
1.	Hitung entropi awal dari dataset (sebelum data dibagi berdasarkan fitur).
2.	Bagi dataset berdasarkan suatu fitur menjadi beberapa subset.
3.	Hitung entropi rata-rata dari subset-subset tersebut.
4.	Kurangi entropi rata-rata dari entropi awal. Hasilnya adalah Information Gain untuk fitur tersebut.
1.4.	Membangun Decision Tree
Decision Tree adalah algoritma pembelajaran mesin yang digunakan untuk tugas klasifikasi dan regresi. Pohon keputusan ini menyerupai struktur seperti diagram alur (flowchart), di mana setiap simpul (node) merepresentasikan sebuah keputusan atau tes pada fitur, setiap cabang merepresentasikan hasil dari tes tersebut, dan setiap leaf node (node daun) mewakili keputusan akhir atau label.
Decision Tree bekerja dengan membagi data secara berulang kali berdasarkan fitur yang dipilih, sehingga menghasilkan struktur pohon yang dapat digunakan untuk memprediksi kelas atau nilai output baru.
 
Komponen Utama Decision Tree:

1.	Root Node: Simpul awal yang mewakili seluruh dataset dan pembelahan pertama berdasarkan fitur terbaik.

2.	Internal Node (Node): Simpul-simpul yang mewakili fitur yang digunakan untuk membagi data. Setiap node memiliki satu pertanyaan atau tes yang membagi data menjadi subset- subset yang lebih kecil.

3.	Leaf Node: Simpul terminal yang memberikan prediksi akhir. Leaf node tidak memiliki pembelahan lebih lanjut.

4.	Cabang (Branch): Menghubungkan node ke node lainnya dan mewakili hasil dari tes yang dilakukan di node sebelumnya.

1.5.	Persiapan dataset: Iris Dataset

![image](https://github.com/user-attachments/assets/04f20514-aec5-4967-8abb-0417f2fd0558)

1.6.	Training model Decision Tree Classifier

![image](https://github.com/user-attachments/assets/a83afc9a-f698-4cfb-862a-dc29cca45d94)

1.7.	Visualisasi model Decision Tree

![image](https://github.com/user-attachments/assets/1988fa13-8932-427f-a4f4-a7549daaaf6a)

![image](https://github.com/user-attachments/assets/5bd65447-6429-48c9-bf8b-de5858fa09e4)

1.8.	Evaluasi model Decision Tree

![image](https://github.com/user-attachments/assets/53ce57f0-e3b5-478c-b5c9-3ad3bc00775a)

2.1.	Proses training model Machine Learning secara umum

![image](https://github.com/user-attachments/assets/40af3792-70d4-4421-bec9-44d54b678c34)

1.	Training Set:

•	X_train: Merupakan fitur-fitur input dari data latih yang digunakan untuk melatih model.

•	y_train: Merupakan label atau target (output sebenarnya) dari data latih yang sesuai dengan X_train.

Training set adalah dataset yang digunakan untuk melatih model, di mana model belajar untuk memetakan input (X_train) ke output yang diharapkan (y_train).

2.	Training Model:

•	Data latih (X_train dan y_train) dimasukkan ke dalam model.
 
 •	Model dipelajari untuk mengenali pola dari data input dan menyesuaikan parameter internalnya untuk memprediksi output.

3.	Trained Model:

•	Setelah model dilatih menggunakan data latih, kita mendapatkan Trained Model, yaitu model yang sudah siap digunakan untuk memprediksi data baru.

4.	Prediksi Data Baru:

•	X_new: Adalah data baru atau data uji yang belum pernah dilihat oleh model.

•	Trained Model kemudian digunakan untuk memprediksi output dari X_new, yang menghasilkan y_pred (prediksi dari data baru).

Secara umum, proses ini menggambarkan alur standar dalam supervised learning:

1.	Model dilatih dengan data yang memiliki label (X_train, y_train).

2.	Setelah dilatih, model digunakan untuk memprediksi label baru (y_pred) berdasarkan input baru (X_new).


2.2.	Pengenalan Ensemble Learning

![image](https://github.com/user-attachments/assets/e3391ca4-7a7e-493c-8fb2-c43edcebf0c8)

Penjelasan Proses pada Gambar:

1.	Training Set:

- X_train (fitur input) dan y_train (target/output sebenarnya) digunakan untuk melatih beberapa model berbeda secara paralel.

2.	Model-Model yang Digunakan:

- KNN (K-Nearest Neighbors): Model pertama yang dilatih dengan data training.

-	SVM (Support Vector Machine): Model kedua yang dilatih dengan data training.

-	Decision Tree: Model ketiga yang dilatih dengan data training.
 

3.	Prediksi Data Baru (X_new):

-	Setiap model yang telah dilatih menggunakan data training sekarang digunakan untuk memprediksi X_new (data baru).

-	Hasil prediksi dari setiap model adalah:

-	y_pred1 dari KNN

-	y_pred2 dari SVM

-	y_pred3 dari Decision Tree

4.	Menggabungkan Prediksi:

-	Setelah setiap model memberikan prediksinya, hasil prediksi dari beberapa model tersebut digabungkan menggunakan metode ensemble.

-	Metode gabungan dapat berupa:

-	Mean (rata-rata): Untuk regresi, prediksi akhir adalah rata-rata dari semua prediksi model.

-	Voting (mayoritas suara): Untuk klasifikasi, prediksi akhir diambil dari prediksi yang paling banyak dipilih (mayoritas) oleh model-model yang berbeda.


2.3.	Pengenalan Bootstrap Aggregating | Bagging

![image](https://github.com/user-attachments/assets/d6d32061-87e3-4350-8b95-ecf6b6514141)


Bootstrap Aggregating, atau sering disingkat sebagai Bagging, adalah teknik ensemble dalam pembelajaran mesin yang digunakan untuk meningkatkan akurasi model prediksi, terutama dalam model berbasis pohon keputusan. Tujuan utama bagging adalah mengurangi varian model dan mencegah overfitting dengan membuat beberapa model yang berbeda dan menggabungkan prediksinya.

Training Set: Proses dimulai dengan dataset pelatihan yang terdiri dari fitur input (X_train) dan target output (y_train).

Bagging (Bootstrap Aggregation):

•	Data pelatihan ini dibagi ke dalam beberapa subset (bag), menggunakan metode bootstrap sampling, yaitu pengambilan sampel secara acak dengan penggantian (beberapa sampel mungkin muncul lebih dari sekali, dan beberapa mungkin tidak muncul sama sekali).

•	Selain itu, pada setiap model, dilakukan pemilihan subset acak dari fitur (features randomness) agar model yang berbeda memiliki keanekaragaman.

Decision Trees:

•	Setiap subset data kemudian digunakan untuk melatih sebuah decision tree yang terpisah. Pada gambar ini, terdapat tiga decision tree yang dilatih dengan subset berbeda dari data asli.

•	Setelah decision tree dilatih pada masing-masing subset, terbentuklah beberapa model prediksi (Trained Model 1, 2, 3, dan seterusnya).

Prediksi pada Data Baru (X_new):

•	Setelah model dilatih, mereka diaplikasikan pada data baru (X_new) yang ingin diprediksi.

•	Masing-masing model akan menghasilkan prediksi (output).

Agregasi (Mean or Mode):

•	Prediksi dari beberapa model tersebut kemudian digabungkan. Dalam kasus regresi, prediksi rata-rata (mean) dari semua model digunakan sebagai prediksi akhir. Sedangkan dalam kasus klasifikasi, mode (nilai yang paling sering muncul) diambil sebagai prediksi akhir (y_pred).


2.4.	Pengenalan Random Forest | Hutan Acak

Random Forest adalah algoritma pembelajaran mesin berbasis metode ensemble yang digunakan untuk tugas klasifikasi, regresi, dan tugas-tugas lainnya. Algoritma ini menggabungkan banyak pohon keputusan yang dilatih secara terpisah untuk meningkatkan akurasi dan mengurangi overfitting. Prinsip utamanya adalah membuat keputusan secara kolektif dari beberapa model lemah (dalam hal ini pohon keputusan) sehingga menghasilkan model yang lebih kuat dan akurat.

Training Set (X_train, y_train):

•	Di bagian kiri atas, ada data pelatihan yang terdiri dari input fitur (X_train) dan label yang sesuai (y_train). Ini adalah data yang digunakan untuk melatih model.
 
Bagging + Features Randomness:

•	Di bagian tengah atas, ada blok yang menunjukkan proses bagging dan randomisasi fitur. Bagging (Bootstrap Aggregating) adalah teknik di mana beberapa subset (bag) dari data pelatihan dibuat secara acak dengan pengambilan sampel ulang. Pada saat yang sama, randomisasi fitur diterapkan, di mana hanya sebagian dari fitur yang dipilih secara acak untuk setiap pohon keputusan.

Bagging ke Tas 1, Tas 2, Tas 3:

•	Data pelatihan yang telah diacak dibagi menjadi beberapa subset, yaitu Bag 1, Bag 2, dan Bag 3. Masing-masing subset ini berisi sebagian data yang berbeda hasil dari pengambilan sampel acak.

Decision Tree (Pohon Keputusan):

•	Setiap subset data (tas) digunakan untuk melatih sebuah pohon keputusan. Di sini, setiap tas menghasilkan pohon keputusan yang berbeda karena adanya variasi dalam data dan pemilihan fitur yang acak.

Prediksi dengan Model yang Ditraining:

•	Setelah pohon keputusan dilatih dengan data dari tas-tas tersebut, mereka siap untuk membuat prediksi. Data baru yang akan diprediksi, yaitu X_new, diberikan kepada masing- masing model yang telah dilatih (Trained Model 1, Trained Model 2, dan Trained Model 3).

Agregasi Prediksi:

•	Hasil prediksi dari setiap pohon keputusan kemudian dikombinasikan melalui proses agregasi. Untuk regresi, prediksi biasanya digabungkan dengan rata-rata. Sedangkan untuk klasifikasi, prediksi diambil berdasarkan modus (mayoritas suara).

Prediksi Akhir (y_pred):

•	Hasil akhir dari proses agregasi adalah prediksi akhir, yang disebut y_pred. Prediksi ini adalah hasil dari penggabungan beberapa pohon keputusan yang bekerja sama.

2.5.	Persiapan dataset | Iris Flower Dataset

![image](https://github.com/user-attachments/assets/48ddf480-8422-460a-8e08-ff17a5048f96)

2.6.	Implementasi Random Forest Classifier dengan Scikit Learn

![image](https://github.com/user-attachments/assets/7f3ef87f-7523-4114-92c1-272d49480fb7)

2.7.	Evaluasi model dengan Classification Report

![image](https://github.com/user-attachments/assets/8d070d0c-8259-4052-a2a3-f07b7e746dc9)
