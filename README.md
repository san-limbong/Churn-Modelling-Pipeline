# Submission 2: Nama Proyek Anda
Nama:

Username dicoding:

| | Deskripsi |
| ----------- | ----------- |
| Dataset | [nama dataset](https://www.kaggle.com/) |
| Masalah | Deskripsi masalah yang di angkat |
| Solusi machine learning | Deskripsi solusi machine learning yang akan dibuat |
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