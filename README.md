# Analisis Sentimen pada Twitter dengan PySpark

![Twitter Sentiment Analysis on Recession using Pyspark with Logistic Regression](https://github.com/user-attachments/assets/ee29a07f-a2ad-4549-b519-723f866ffb38)


## Project Overview

Dalam era digital, data yang dihasilkan setiap harinya semakin banyak, terutama dengan adanya media sosial seperti Twitter yang memungkinkan pengguna untuk dengan mudah dan cepat membagikan pemikiran dan pandangan mereka tentang suatu hal. Oleh karena itu, analisis sentimen pada data Twitter menjadi penting untuk mengidentifikasi perasaan, pandangan, atau pendapat seseorang terhadap suatu hal dengan menggunakan teks sebagai data input. Teknik analisis sentimen dapat diterapkan pada berbagai jenis data teks, termasuk tweet, ulasan hotel, ulasan pelanggan, dan lain-lain.
Dalam konteks saat ini, analisis sentimen pada data Twitter mengenai resesi global menjadi semakin penting karena dapat mempengaruhi berbagai aspek kehidupan, termasuk keuangan pribadi, bisnis, dan ekonomi secara keseluruhan. Melalui twitter maka akan diketahui bagaimana bahwasannya perasaan masyarakat maupun pandangannya terhadap resesi secara real-time. Resesi dapat mempengaruhi perekonomian dan kesejahteraan sosial. Dengan teknologi dan metode analisis sentimen, data tweet terkait resesi ekonomi dapat diambil dan dianalisis dengan cepat, sehingga para peneliti dan pengambil keputusan dapat membuat kebijakan yang tepat dan efektif. Oleh karena itu, proyek pengolahan data besar ini diharapkan dapat memberikan manfaat dalam mengolah data dari Twitter dan meningkatkan akurasi algoritma dalam melakukan proses analisis sentimen terkait resesi.
Proyek pengolahan data besar ini mencakup klasifikasi analisis sentimen pada streaming data twitter dengan menggunakan layanan API Stream yang disediakan oleh Twitter. Tahap preprocessing diperlukan sebelum analisis sentimen, seperti folding case, penghapusan simbol, tokenisasi, konversi slang word, dan penghapusan stopword. Penelitian ini diharapkan dapat memberikan manfaat dalam mengolah data besar dari Twitter dan meningkatkan akurasi algoritma dalam melakukan proses analisis sentimen.

## Business Understanding

### Rumusan Masalah
Bagaimana melakukan analisis sentimen pada data live streaming Twitter dengan menggunakan keyword "resesi" untuk memahami pandangan dan opini pengguna Twitter terhadap fenomena resesi ekonomi global?

### Tujuan

Tujuan dari proyek ini adalah untuk melakukan analisis sentimen pada dataset live streaming Twitter dengan keyword "resesi" agar dapat memahami pandangan dan opini pengguna Twitter terhadap fenomena resesi ekonomi global.

### Scope
Berikut ini dijabarkan batasan dari pengerjaan proyek sentimen analisis pada dataset live streaming twitter sebagai berikut.
1.	Penggunaan algoritma Logistic Regression dalam melakukan analisis sentimen pada dataset live streaming Twitter dengan keyword "resesi" dalam bahasa inggris.
2.	Pengumpulan data dilakukan dengan memanfaatkan layanan API Stream yang disediakan oleh Twitter.
3.	Data yang digunakan adalah data tweet yang mengandung keyword "resesi" dalam bahasa Inggris yang diposting dalam rentang waktu tertentu.
4.	Analisis sentimen akan fokus pada polaritas sentimen positif dan negatif dalam konteks pandangan dan opini pengguna Twitter terhadap fenomena resesi ekonomi global.

## Arsitektur Sistem

![arsitektur](https://github.com/user-attachments/assets/c3c2078b-db7c-460f-8121-ac28f63e967d)


### Streaming data twitter
Tahapan yang pertama dilakukan adalah Streaming data twitter. Pada tahap ini, data streaming Twitter diambil menggunakan Tweepy dan difilter menggunakan fungsi Tweepy untuk mengambil data yang sesuai dengan kata kunci “resesi”. Data yang telah diambil kemudian akan disimpan dalam format yang dapat diolah dan diproses.

### Data Storage
Data streaming yang diterima dapat disimpan dalam sistem penyimpanan data yang sesuai, seperti dalam format CSV (Comma-Separated Values) merupakan salah satu pilihan yang umum digunakan.

### Streaming Data Processing
Setelah menyimpan data streaming dari Twitter dalam format CSV, langkah selanjutnya adalah melakukan streaming data processing menggunakan structured data streaming. Dalam structured data streaming Twitter, data streaming Twitter yang disimpan. Output dari pemrosesan data streaming dapat disimpan dalam format yang sesuai dan mencakup wawasan yang mendalam tentang data streaming Twitter. Structured data streaming Twitter memfasilitasi pemrosesan yang terstruktur dan efisien, mendukung analisis mendalam, dan pengambilan keputusan yang lebih baik dalam konteks Twitter.

### Evaluate Model
Setelah memproses data streaming dengan struktur data streaming, langkah selanjutnya adalah mengevaluasi model yang digunakan. Evaluasi model bertujuan untuk mengukur sejauh mana kinerja model dalam menghasilkan prediksi akurat. Hasil evaluasi meliputi metrik-metrik seperti akurasi, presisi, recall, F1-score. Selain itu, klasifikasi report memberikan informasi rinci tentang performa model pada setiap kelas. Evaluasi model ini penting untuk memahami efektivitas model dalam pemrosesan data streaming dan mendukung pengambilan keputusan.

## Machine Learning Pipeline

![Picture2](https://github.com/user-attachments/assets/eebcd876-ca74-4787-ae94-e65e9e4a7e3e)

## Data Retrieval
Twitter menghasilkan aliran data kontinu yang mana data tersebut dihasilkan oleh aktivitas pengguna di media sosial tersebut. Data ini mencakup berbagai jenis informasi seperti tweet, retweet, mention, like, dan juga metadata seperti lokasi, tanggal, dan waktu. Twitter menyediakan API (Application Programming Interface) yang memungkinkan pengembang untuk mengakses dan mengumpulkan data ini untuk berbagai tujuan analisis dan pengolahan.
Menggunakan stream data Twitter, pengguna dapat memantau dan menganalisis topik, tren, dan sentimen yang sedang populer dalam waktu nyata. Berikut ini beberapa langkah dalam mengolah stream data Twitter.

### Akses API Twitter
Untuk mengakses data streaming Twitter, pengguna perlu mendaftar dan membuat aplikasi di situs pengembang Twitter. Setelah aplikasi dibuat, pengguna akan menerima kredensial API seperti API key, API secret key, access token, dan access token secret.

![Picture3](https://github.com/user-attachments/assets/65a94169-1bc4-4836-8a83-7e7b8c53f700)

Selanjutnya token dan key akan dikonfigurasikan sesuai dengan autentikasi koneksi API yang digunakan pada baris kode python dengan melakukan import library tweepy terlebih dahulu seperti berikut.

![Picture4](https://github.com/user-attachments/assets/8b07c255-8bf9-4e86-b697-cfb57e505588)


### Crawling Data 
Setelah melakukan konfigurasi API, selanjutnya akan dilakukan penarikan data dengan kata kunci “recession”. Pada saat penarikan tweets, data yang diambil maksimal sebanyak 100 data, karena sesuai dengan ketentuan penggunaan pengguna yang berlaku. Kemudian data akan dibagi menjadi 2 kolom, yakni “Date” dan “Tweet” . Data resesi yang diambil dispesifikasikan dengan mengambil kata kunci yang memiliki bahasa inggris, disamping itu kata yang mengandung tautan atau link serta memiliki kata yang sama persis akan di filter, hal ini bertujuan untuk menghindari redudansi data. Penerapan ini dilandasi oleh adanya penggunaan data yang berulang akibat adanya penggunaan BOT sehingga data yang digunakan cenderung menghasilkan data yang duplikat sehingga dianggap tidak sesuai dengan fokus tujuan dari penelitian ini, yakni sentimen analisis.

```
def crawltweets(search_tweet, n_tweets=100):
    data_tweets = pd.DataFrame(columns=['Date', 'Tweet'])
    tweets = tweepy.Cursor(api.search_tweets, q=search_tweet, lang="en", tweet_mode='extended').items(n_tweets)
    url_pattern = re.compile(r'http\S+|www\S+')
   
    for tweet in tweets:
        Date = tweet.created_at
        try:
            Tweet = tweet.retweeted_status.full_text
        except AttributeError:
            Tweet = tweet.full_text
        if not bool(url_pattern.search(Tweet)):
            ith_tweet = [Date, Tweet]
            data_tweets.loc[len(data_tweets)] = ith_tweet
    data_tweets = data_tweets.drop_duplicates(subset='Tweet', keep='first')
    for index, tweet in enumerate(data_tweets['Tweet']):
      if index == 20:
          break
      print(tweet)
    print('Crawling is Done =', len(data_tweets))
    namafile = 'recession.csv'
    data_tweets.to_csv(namafile, index=False)


search_tweet = "recession"
crawltweets(search_tweet)

```

Setelah data duplikat di filter, maka tahapan berikutnya adalah menampilkan 20 sampel data yang diambil pada hasil keluaran yang bertujuan untuk menampilkan bagaimana contoh data tweets yang telah diambil. Selanjutnya apabila data telah mencapai jumlah penarikan data yang telah ditetapkan, maka akan menampilkan output Crawling is Done dengan menampilkan jumlah spesifik data yang diambil. Pada bagian terakhir, data akan disimpan dalam format csv dengan nama recession.csv.


## Data Understanding

### Collecting Data 
Pada tahap ini, fokus utama adalah mengumpulkan data dari berbagai sumber yang terkait dengan proyek ini. Sumber data adalah API. Proses pengumpulan data ini dilakukan dengan hati-hati dan mengacu pada kriteria yang telah ditentukan sebelumnya. 
Berikut ini adalah tampilan data yang telah dikumpulkan.

![Picture5](https://github.com/user-attachments/assets/a2d034a3-529a-4bdd-93be-3822653874d0)

### Describe Data
![Picture6](https://github.com/user-attachments/assets/546bfc28-a289-4bdb-9967-d6e5b5a11993)

Berdasarkan tahapan data describe melibatkan beberapa statistik ringkasan, antara lain:
●	Jumlah Data (Count): Statistik "count" menunjukkan jumlah entri yang tersedia untuk setiap kolom dalam dataset. Dalam contoh yang diberikan, terdapat 2095 entri untuk kolom "Date" dan 1261 entri untuk kolom "Tweet". Informasi ini memberikan gambaran tentang volume data yang telah dikumpulkan.
●	Rata-rata (Mean): Pada output yang diberikan, nilai "null" ditampilkan pada kolom "Date" dan "Tweet". Hal ini menunjukkan bahwa rata-rata tidak dapat dihitung untuk kedua kolom tersebut karena jenis data yang ada di dalamnya.
●	Simpangan Standar (Standard Deviation): Seperti pada nilai rata-rata, nilai "null" ditampilkan pada kolom "Date" dan "Tweet". Hal ini mengindikasikan bahwa simpangan standar tidak dapat dihitung untuk kedua kolom tersebut karena jenis data yang ada di dalamnya.
●	Nilai Terendah (Minimum): Pada kolom "Date", nilai terendah yang ditemukan adalah "God will help...". Sedangkan pada kolom "Tweet", nilai terendah adalah "#banking tension...". Ini memberikan contoh teks dengan nilai terendah dalam dataset yang telah dikumpulkan.
●	Nilai Tertinggi (Maximum): Pada kolom "Date", nilai tertinggi yang ditemukan adalah "🧊 US job market...". Sedangkan pada kolom "Tweet", nilai tertinggi adalah "🤡 First 'transit...". Ini memberikan contoh teks dengan nilai tertinggi dalam dataset yang telah dikumpulkan

### Validation Data 
Data validation adalah proses memastikan bahwa data yang ada dalam dataset memenuhi kriteria atau persyaratan yang telah ditetapkan sebelumnya. Data validation adalah proses memeriksa dan memastikan bahwa data dalam dataset memenuhi kriteria atau persyaratan yang telah ditetapkan. Dalam dataset yang diberikan, terdapat 2095 entri non-null pada kolom "Date" dan 1261 entri non-null pada kolom "Tweet". Selain itu, terdapat 834 nilai null secara keseluruhan dalam dataframe tersebut.


## Data Preparation
Berikut serangkaian langkah yang dilakukan dalam mengubah, membersihkan, mengintegrasikan, dan mengorganisir data.
1. Data Cleaning, meliputi _missing value_ dan duplikat
2. Text Preprocessing.
   Text processing, atau pengolahan teks, adalah proses manipulasi dan analisis teks dalam bentuk data. Tujuan dari text processing adalah untuk mengolah dan memahami teks secara komputasional, sehingga memungkinkan mesin untuk memahami, menganalisis, dan mengekstrak informasi dari teks secara otomatis. Text processing melibatkan serangkaian langkah dan teknik yang digunakan untuk memanipulasi dan menganalisis teks. Adapun tahapannya adalah sebagai berikut:
   - Filtering
   - Cleaning Text (mengubah teks menjadi huruf kecil, menghapus teks di dalam tanda kurung siku, menghapus link web, menghapus tanda baca, menghapus kata yang mengandung angka, menghapus angka, menghapus karakter @ yang diikuti oleh non-alphanumeric, menghapus karakter # yang diikuti oleh non-alphanumeric, menghapus karakter tanda baca tertentu, menghapus spasi berlebih, mengganti karakter \n dengan spasi, mengganti karakter \ ■ dengan spasi, dan menghapus karakter & yang diikuti oleh non-space)
   - Remove Stopwords (kata-kata umum yang tidak memberikan makna penting)
   - Stemming menggunakan algoritma SnowballStemmer.
  
Berikut merupakan tampilan data setelah dilakukan text processing.

  ![Picture7](https://github.com/user-attachments/assets/f6552c13-0ce2-4f68-8342-6c03d2e14b42)

3. Data Labelling.
Data labelling, juga dikenal sebagai anotasi data, merupakan proses memberikan label atau kategori kepada setiap dataset. Tujuan utama dari data labelling adalah untuk memberikan informasi yang spesifik dan bermakna pada setiap contoh data, sehingga dapat digunakan dalam melatih dan menguji model pembelajaran mesin. Dalam konteks proyek yang sedang dibahas, contoh data labelling yang digunakan adalah anotasi sentimen.
Dalam kode program yang digunakan, anotasi sentimen dilakukan dengan memanfaatkan library TextBlob. TextBlob merupakan sebuah library pemrosesan bahasa alami (NLP) yang menyediakan berbagai fungsi dan metode untuk melakukan analisis sentimen. Sentimen pada teks dinyatakan dalam nilai polaritas yang berada dalam rentang -1.0 hingga 1.0. Nilai 0 mengindikasikan sentimen positif, nilai 1 menunjukkan sentimen negatif. Pada tahap selanjutnya, nilai polaritas sentimen yang dihasilkan oleh TextBlob diubah menjadi label positif atau negatif. Jika nilai polaritas lebih besar dari 0, maka label yang diberikan adalah 1, yang menunjukkan sentimen positif. Jika nilai polaritas kurang dari atau sama dengan 0, maka label yang diberikan adalah 0, yang menunjukkan sentimen negatif.
Dengan menggunakan proses data labelling ini, tujuannya adalah untuk memberikan pemahaman yang jelas dan terstruktur tentang sentimen yang terkandung dalam teks pada setiap contoh data. Hal ini memungkinkan adanya analisis sentimen berdasarkan isi teks dalam dataset yang digunakan.

Berikut adalah data yang telah dilabelling menggunakan library TextBlob.

![Picture8](https://github.com/user-attachments/assets/f92fa01d-77db-4d8f-b397-ef5ff0a4aa29)

   
## Modeling
Pembangunan model Klasifikasi menggunakan Pipeline dalam Apache Spark adalah proses membangun alur kerja pembelajaran mesin yang melibatkan beberapa tahap untuk pra-pemrosesan teks dan pelatihan model. Pipeline memastikan aliran data dan operasi yang sistematis, sehingga memudahkan penanganan tugas pemrosesan teks yang kompleks dan pelatihan model klasifikasi dengan efisien.
Berikut merupakan langkah-langkah klasifikasi menggunakan pipeline dalam apache spark:
1.	Menghapus Kolom yang Tidak Diperlukan.
   Kolom "Date" dan "Tweet" dihapus dari dataframe "df" menggunakan metode "drop". Tujuan dari langkah ini adalah melakukan persiapan data sebelum dilakukan pemrosesan lebih lanjut. Variabel "drop_cols" digunakan untuk menyimpan daftar kolom yang akan dihapus. Kemudian, dilakukan operasi "drop(*drop_cols)" pada dataframe "df" untuk menghapus kolom-kolom tersebut.

2. Definisi Stages untuk Pipeline: 
Tahap-tahap (stages) dalam pipeline didefinisikan, termasuk Tokenizer, CountVectorizer, IDF, dan LogisticRegression. Tujuan dari langkah ini adalah untuk mengatur langkah-langkah pemrosesan teks dan pelatihan model klasifikasi dalam pipeline. Untuk melakukan itu, kita mengimpor kelas-kelas yang diperlukan dari modul "pyspark.ml.feature" dan "pyspark.ml.classification". Kemudian, objek tokenizer, countVectorizer, idf, dan logisticRegression didefinisikan sebagai tahap-tahap dalam pipeline.

3.	Membuat Pipeline.
Pipeline dibuat dengan menggabungkan semua tahap yang telah didefinisikan sebelumnya. Pipeline ini bertujuan untuk mengatur alur kerja pemrosesan teks dan pelatihan model secara otomatis. Untuk membuat pipeline, kita menggunakan objek-objek tahap yang telah didefinisikan sebelumnya dan menggunakan kelas "Pipeline" dari modul "pyspark.ml". Hasilnya, pipeline disimpan dalam variabel "pipeline".

4.	Pembagian Data menjadi Train Set dan Test Set.
Data dibagi menjadi set pelatihan (train set) dan set pengujian (test set) menggunakan metode "randomSplit". Tujuan dari langkah ini adalah untuk membagi data dengan proporsi tertentu agar dapat digunakan untuk melatih dan menguji model klasifikasi. Proporsi pembagian data train dan test ditentukan dengan menggunakan metode "randomSplit". Hasil pembagian data train dan test disimpan dalam variabel "trainDF" dan "testDF".

5.	Melatih Model dengan Data Train menggunakan Pipeline.
Model klasifikasi dilatih menggunakan dataset pelatihan (trainDF) menggunakan pipeline yang telah dibuat sebelumnya. Pipeline akan menjalankan langkah-langkah pemrosesan teks dan pelatihan model secara berurutan. Untuk melatih model, menggunakan metode "fit" pada objek pipeline dengan menggunakan data train (trainDF). Hasil model yang telah dilatih disimpan dalam variabel "model".

6.	Prediksi pada Data Test.
Setelah model dilatih, dilakukan prediksi pada dataset pengujian (testDF). Hasil prediksi disimpan dalam dataframe "predictions". Prediksi dilakukan menggunakan metode "transform".

7.	Konversi ke Pandas DataFrame
Dataframe "predictions" dikonversi menjadi Pandas DataFrame dengan nama "pred" untuk memudahkan analisis dan visualisasi data. Hal ini dilakukan dengan menggunakan metode "toPandas()" pada dataframe "predictions" dan hasilnya disimpan dalam variabel "pred". Untuk melihat beberapa baris pertama dari DataFrame "pred", menggunakan metode "head()".

Berikut adalah tampilan data untuk melakukan konversi ke pandas dataframe.

![Picture9](https://github.com/user-attachments/assets/2bb2e9be-bf4f-4251-9cf1-0c40514971e9)


## Word Cloud Visualization

### Positive Sentiment

![Picture10](https://github.com/user-attachments/assets/c1c68b8d-0148-42c0-a92a-f7f42b6a9771)


### Negative Sentiment

![Picture11](https://github.com/user-attachments/assets/2e081765-44f4-4adf-8303-776265501e18)


## Evaluation
Metrik evaluasi yang kita gunakan adalah areaUnderROC, yang memberikan gambaran tentang seberapa baik model dapat membedakan antara kelas positif dan negatif. 

Pada bagian berikut ini akan ditampilkan hasil evaluasi areaUnderROC pada bagian testing.

![Picture12](https://github.com/user-attachments/assets/956ddc94-cc15-4ba2-8960-f2ab0dc3c8a2)


Selain itu, kita juga melihat metrik evaluasi lainnya seperti presisi, recall, dan f1-score untuk setiap kelas. Presisi mengukur seberapa sering model benar ketika memprediksi kelas positif, sementara recall mengukur seberapa baik model dalam menemukan semua contoh positif dalam data. F1-score adalah gabungan dari presisi dan recall yang memberikan gambaran tentang seimbangnya model dalam mengukur kedua metrik tersebut.

![Picture13](https://github.com/user-attachments/assets/44e2b14d-c6c3-4cf1-b68b-eec1bf4d236d)

Kita juga mempertimbangkan jumlah data (support) untuk setiap kelas, yang menunjukkan seberapa banyak contoh yang kita miliki untuk kelas tersebut. Ini penting untuk memahami apakah model kita mungkin bias terhadap kelas tertentu.
Model kita memiliki akurasi 77%, yang berarti model memprediksi dengan benar dalam 77% dari total data pengujian. Rata-rata metrik evaluasi juga disajikan untuk semua kelas, dengan Macro avg memberikan rata-rata metrik tanpa mempertimbangkan ketidakseimbangan data pada setiap kelas, sedangkan weighted avg memperhitungkan ketidakseimbangan tersebut.

Confusion matrix memberikan cara lain yang berguna untuk memahami kinerja model kita. Matriks ini menunjukkan empat kemungkinan hasil.

![Picture14](https://github.com/user-attachments/assets/ddb4710f-c8b3-4387-93f9-b11639532f5c)

Ada 228 contoh di mana model dengan benar memprediksi kelas negatif, dan 43 contoh di mana model salah memprediksi kelas positif. Sedangkan untuk kelas positif, ada 50 contoh yang diprediksi dengan benar oleh model, dan 77 contoh di mana model salah memprediksi sebagai kelas negatif. Melihat ini, kita bisa melihat bahwa model kita cenderung membuat lebih banyak kesalahan dalam memprediksi kelas positif sebagai negatif.
Secara keseluruhan, informasi ini memberikan gambaran yang mendalam tentang bagaimana model kita bekerja, dan memungkinkan kita untuk mengidentifikasi area di mana model mungkin memerlukan perbaikan.

