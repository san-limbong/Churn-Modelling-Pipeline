# Submission 2: Churn Modelling
Nama:

Username dicoding:

| | Deskripsi |
| ----------- | ----------- |
| Dataset | [Churn Modelling](https://www.kaggle.com/datasets/shrutimechlearn/churn-modelling/data) |
| Masalah | Dalam industri perbankan, memahami faktor-faktor yang menyebabkan nasabah meninggalkan bank adalah hal yang sangat penting. Dataset ini menyediakan rincian mengenai nasabah sebuah bank, termasuk atribut-atribut seperti negara asal, jenis kelamin, usia, lamanya menjadi nasabah, saldo rekening, jumlah produk bank yang digunakan, kepemilikan kartu kredit, status keaktifan sebagai anggota, dan estimasi gaji. Tujuan utama dari analisis ini adalah untuk mengidentifikasi pola dan faktor-faktor yang signifikan yang mempengaruhi keputusan nasabah untuk meninggalkan bank. Dengan mengetahui faktor-faktor ini, bank dapat merancang strategi yang lebih efektif untuk mempertahankan nasabahnya dan mengurangi tingkat churn. Model prediksi yang dibangun dari data ini dapat membantu bank dalam melakukan intervensi yang lebih tepat waktu dan sasaran dalam usaha mempertahankan nasabah, sehingga meningkatkan kepuasan dan loyalitas nasabah. |
| Solusi machine learning | Solusi yang akan dibangun adalah model klasifikasi menggunakan neural network yang dapat membantu mendeteksi kemungkinan seorang nasabah bank melakukan churn. |
| Metode pengolahan | Deskripsi metode pengolahan data yang digunakan |
| Arsitektur model | Deskripsi arsitektur model yang diguanakan |
| Metrik evaluasi | Deksripsi metrik yang digunakan untuk mengevaluasi performa model |
| Performa model | Deksripsi performa model yang dibuat |
| Opsi deployment | Deksripsi tentang opsi deployment |
| Web app | Tautan web app yang digunakan untuk mengakses model serving. Contoh: [nama-model](https://model-resiko-kredit.herokuapp.com/v1/models/model-resiko-kredit/metadata)|
| Monitoring | Deksripsi terkait hasil monitoring dari model serving |



docker build -t churn-monitoring .\monitoring\
docker run -p 9090:9090 churn-monitoring  

https://churn-modelling-pipeline-production.up.railway.app/v1/models/churn-model/metadata

http://localhost:9090/
