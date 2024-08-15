# Submission 2: Churn Modelling
Nama:

Username dicoding:

| | Deskripsi |
| ----------- | ----------- |
| Dataset | [Churn Modelling](https://www.kaggle.com/datasets/shrutimechlearn/churn-modelling/data) |
| Masalah | Dalam industri perbankan, memahami faktor-faktor yang menyebabkan nasabah meninggalkan bank adalah hal yang sangat penting. Dataset ini menyediakan rincian mengenai nasabah sebuah bank, termasuk atribut-atribut seperti negara asal, jenis kelamin, usia, lamanya menjadi nasabah, saldo rekening, jumlah produk bank yang digunakan, kepemilikan kartu kredit, status keaktifan sebagai anggota, dan estimasi gaji. Tujuan utama dari analisis ini adalah untuk mengidentifikasi pola dan faktor-faktor yang signifikan yang mempengaruhi keputusan nasabah untuk meninggalkan bank. Dengan mengetahui faktor-faktor ini, bank dapat merancang strategi yang lebih efektif untuk mempertahankan nasabahnya dan mengurangi tingkat churn. Model prediksi yang dibangun dari data ini dapat membantu bank dalam melakukan intervensi yang lebih tepat waktu dan sasaran dalam usaha mempertahankan nasabah, sehingga meningkatkan kepuasan dan loyalitas nasabah. |
| Solusi machine learning | Solusi yang akan dibangun adalah model klasifikasi menggunakan neural network yang dapat membantu mendeteksi kemungkinan seorang nasabah bank melakukan churn. |
| Metode pengolahan | Data bank pelanggan diproses melalui beberapa tahap menggunakan komponen-komponen TFX. Tahapan pemrosesan dimulai dengan pembacaan data dari direktori yang ditentukan melalui CsvExampleGen, yang membagi data menjadi dua bagian, yaitu pelatihan dan evaluasi. Statistik data kemudian dihasilkan oleh StatisticsGen, sementara skema data ditentukan oleh SchemaGen. ExampleValidator memastikan bahwa data tersebut sesuai dengan skema yang ditentukan. Selanjutnya, transformasi data dilakukan menggunakan modul transformasi khusus yang mengonversi fitur kategorikal menjadi vektor satu-hot dan mengubah fitur numerik menjadi skala antara 0 dan 1. |
| Arsitektur model | Model didefinisikan menggunakan Keras dengan input berupa fitur kategorikal yang di-one-hot encoding dan fitur numerik yang telah diskalakan. Input ini kemudian dikombinasikan melalui lapisan concatenate. Lapisan-lapisan dense berturut-turut dengan aktivasi ReLU kemudian digunakan untuk membuat model lebih dalam dan kompleks, dengan lapisan-lapisan berukuran 256, 64, dan 16 unit. Akhirnya, model menghasilkan output melalui lapisan dense dengan satu neuron dan fungsi aktivasi sigmoid, yang digunakan untuk klasifikasi biner. Model ini dioptimasi menggunakan Adam dengan laju pembelajaran 0.001, dan metrik yang digunakan adalah akurasi biner. Model kemudian dilatih dengan data yang telah diproses sebelumnya, serta diintegrasikan ke dalam pipeline TFX untuk pengujian dan evaluasi lebih lanjut. |
| Metrik evaluasi | Metrik yang digunakan meliputi Area Under Curve (AUC) untuk menilai area di bawah kurva ROC, False Positive untuk menghitung kesalahan klasifikasi data negatif sebagai positif, False Negative untuk menghitung kesalahan klasifikasi data positif sebagai negatif, True Positive untuk mengukur klasifikasi positif yang benar, True Negative untuk mengukur klasifikasi negatif yang benar, dan Binary Accuracy untuk mengukur proporsi prediksi yang benar dalam masalah klasifikasi biner. |
| Performa model | Model ini menunjukkan kinerja yang sangat baik pada data pelatihan dengan nilai loss sebesar 0.0414 dan akurasi binary sebesar 98.52%. Namun, pada data validasi, performanya menurun, dengan nilai loss sebesar 2.0221 dan akurasi binary sebesar 80.87%. Perbedaan performa yang cukup besar antara data pelatihan dan data validasi menunjukkan bahwa model mengalami overfitting. |
| Opsi deployment | Deksripsi tentang opsi deployment |
| Web app | Tautan web app yang digunakan untuk mengakses model serving. Contoh: [nama-model](https://model-resiko-kredit.herokuapp.com/v1/models/model-resiko-kredit/metadata)|
| Monitoring | Deksripsi terkait hasil monitoring dari model serving |



docker build -t churn-monitoring .\monitoring\
docker run -p 9090:9090 churn-monitoring  

https://churn-modelling-pipeline-production.up.railway.app/v1/models/churn-model/metadata

http://localhost:9090/
