# Chatbot Konseling dan Dukungan Mahasiswa Semester Akhir Universitas Bengkulu
Tugas Pembuatan Model Chatbot Konseling dan Dukungan Mahasiswa Semester Akhir Universitas Bengkulu dengan metode Long Sort Time Memory (LSTM) untuk tugas klasifikasi teks, sebagai bagian dari Ujian Akhir Semester Mata Kuliah Deep Learning. Peran penting dari pembuatan sistem ini adalah sebagai media untuk mendukung kesehatan mental dan emosional para Mahasiswa yang sedang menghadapi berbagai problematika pada tahap akhir perkuliahan. Terkadang para Mahasiswa bingung untuk menceritakan keluh kesah dan sekadar meminta saran serta tips untuk menghadapi tantangan Tugas Akhir ataupun bagaimana mempersiapkan diri dengan tantangan baru di dunia kerja setelah lulus dari bangku perkuliahan. Sistem ini diharapkan dapat memberikan dukungan mental dan emosional, serta memberikan tips-tips kepada Mahasiswa untuk dapat terus bersemangat dan dapat menjadi media penyampaian untuk dapat mengelola waktu dan tingkat stres dengan baik.

## **Anggota Kelompok**

| Nama               | NPM             | 
| ------------------ |---------------- |
| Fachrurazi         | G1A021016       |
| Fadilah Syakirah   | G1A021022       | 
| Adelia Ayu Lestari | G1A021066       | 

## **Dataset Yang Digunakan**
**Jenis Data** : Primer<br>
**Metode Pengumpulan Dataset** : Data dikumpulkan secara manual dengan research dan analisis mendalam terkait permasalahan-permasalahan Mahasiswa semester akhir<br>
**Total Kelas** : 93<br>
**Format File** : .JSON<br>

## **Detail Pelatihan**
1. Proses Pra-pemrosesan Data<br>
Pada tahap ini, teks terlebih dahulu ditokenisasi menggunakan Tokenizer untuk mengubah setiap kata menjadi representasi numerik. Selanjutnya, padding diterapkan untuk menyamakan panjang semua urutan, sehingga data dapat diproses dalam bentuk batch. Setelah itu, encoding label dilakukan menggunakan LabelEncoder untuk mengonversi label kategori menjadi format numerik yang dapat digunakan oleh model.
2. Arsitektur Model<br>
Arsitektur model yang digunakan terdiri dari beberapa komponen utama. Embedding Layer digunakan untuk merepresentasikan kata dalam bentuk vektor numerik berdimensi tetap. LSTM Layer bertugas memproses data berurutan dan menangkap hubungan temporal antar kata. Keluaran dari LSTM kemudian diratakan menggunakan Flatten Layer untuk menyesuaikan bentuknya dengan lapisan berikutnya. Akhirnya, Dense Layer dengan fungsi aktivasi softmax digunakan untuk menghasilkan prediksi dalam beberapa kelas
3. Penyusunan dan Konfigurasi Model<br>
   Model disusun menggunakan fungsi loss Sparse Categorical Crossentropy, yang sesuai untuk tugas klasifikasi dengan label berupa integer. Optimizer Adam dipilih untuk mempercepat proses konvergensi model, sementara metrik akurasi digunakan untuk mengevaluasi kinerja model selama pelatihan.
4. Training<br>
   Proses pelatihan model dilakukan selama 300 epoch dengan pembagian dataset menjadi data pelatihan dan data pengujian. Hal ini memungkinkan model untuk belajar dari data pelatihan dan divalidasi kinerjanya menggunakan data pengujian.

## **Arsitektur Model**
<br>
<div align="left">
  <img src="https://github.com/user-attachments/assets/8b481795-6b29-48dd-ba2a-9cd08eab397a" width="500"/>
</div>
<br>

| **Layer**   | **Tipe Layer** | **Input Shape**    | **Output Shape**   | **Deskripsi**                                                            |
|-------------|----------------|--------------------|--------------------|---------------------------------------------------------------------------|
| Input Layer | InputLayer     | `(None, 17)`       | `(None, 17)`       | Layer input yang menerima data berupa urutan panjang 17.                  |
| Embedding   | Embedding      | `(None, 17)`       | `(None, 17, 20)`   | Mengubah indeks kata menjadi representasi vektor embedding berdimensi 20. |
| LSTM        | LSTM           | `(None, 17, 20)`   | `(None, 17, 20)`   | Layer LSTM untuk memproses data sequential dengan keluaran sekuensial.    |
| Flatten     | Flatten        | `(None, 17, 20)`   | `(None, 340)`      | Mengubah tensor 3D menjadi 1D agar dapat digunakan pada layer Dense.      |
| Dense       | Dense          | `(None, 340)`      | `(None, 93)`       | Fully connected layer dengan 93 neuron (kemungkinan untuk klasifikasi).   |


## **Detail Model**

| Metric             | Value   |
|--------------------|---------|
| **Total Epochs**    | 300     |
| **Average Accuracy** | 0.9797  |
| **Loss**            | 0.0428  |

**Grafik Accuracy**

<div align="left">
  <img src="https://github.com/user-attachments/assets/7692469f-be22-49d4-a930-7b5378baa0ea" width="700"/>
</div>

**Grafik Loss**

<div align="left">
   <img src="https://github.com/user-attachments/assets/1e25b6cc-783b-44df-b76d-31814f04b61b" width="700"/>
</div>

## **Output Model**
<br>
<img src="https://github.com/user-attachments/assets/d9e295fc-265f-48c4-8b56-918ea053cde9" width="1000"/>

## **Apakah Model Yang Dibangun Merupakan Deep Learning Atau Shallow Learn?**
Pada Model yang dibangun merupakan model LSTM (Long Short Time Memory), dimana model ini memiliki beberapa layer, seperti layer input, layer embedding, layer lSTM, layer flatten, dan layer dense. Jika menganalisa perbedaan dari model Deep Learning dan model Shallow Learn, Deep Learning cenderung memiliki banyak lapisan layer , sementara itu Shallow Learn merupakan model sederhana yang hanya memiliki beberapa lapisan layer saja, atau bahkan 1 lapisan layer. Model Shallow Learn juga tidak cocok untuk menangani tugas kompleks seperti ChatBot. Maka dari itu, model LSTM yang dibangun merupakan model Deep Learning karena memiliki beberapa lapisan layer yang saling terhubung dan dapat menyelesaikan tugas yang cukup kompleks seperti pembuatan model ChatBot atau tugas klasifikasi teksun. 

## **Kesimpulan**<br>
  Dari pengujian model LTSM dalam pembangunan ChatBot Konseling dan Dukungan mahasiswa semester akhir Universitas Bengkulu dapat disimpulkan bahwa model mendapat akurasi yang cukup bagus, yakni dengan rata-rata akurasi sebesar 0.9797. Kemudian, nilai loss pada model menunjukkan angka 0.0428 yang berarti nilai kesalahan atau error pada model terbilang sangat kecil. Model LSTM dengan  total data sebesar 93 kelas dengan total pelatihan atau epoch sebanyak 300 ini sudah layak untuk diimplementasikan pada berbagai tugas yang melibatkan klasifikasi teks.

## **Saran**<br>
  Model sudah cukup baik, tetapi masih harus diperbanyak lagi penambahan data, apalagi tema yang terkait konseling sangat amat bervariasi serta permasalahan sosial dan tekanan mental pada Mahasiswa sangat banyak yang dipengaruhi oleh berbagai faktor. Maka, untuk kedepannya Chatbot SahabatAkhirUnib haruslah dapat menjawab berbagai persoalan secara lebih luas lagi.


