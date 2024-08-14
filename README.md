docker build -t churn-monitoring .\monitoring\
docker run -p 9090:9090 churn-monitoring  

https://churn-modelling-pipeline-production.up.railway.app/v1/models/churn-model/metadata

http://localhost:9090/