By: Ricardo Perez and Angel Higueros
# Google  SQL - MySQL
#comandos para crear la instancia sql 
gcloud sql instances create sqlproject \
--database-version=MYSQL_8_0_28
gcloud sql instances describe sqlproject
#comando para agregar contrasena al usuario root
gcloud sql users set-password root \
--host=% \
--instance=INSTANCE_NAME \
--prompt-for-password

# Google  Function
#comandos para la cloud functions
gcloud functions deploy 'finalproject' --runtime nodejs16 --trigger-http --entry-point=function

# Google Kubernetes Engine (Deployment)
```sh
# Deploy del frontend
npm run build

# Crear imagen de docker, ejecucion del contenedor para prueba local y subirlo al hub docker
docker build -t umgtato/finalproject .   
docker run -d -p 3001:3001 --name final umgtato/finalproject
docker push umgtato/finalproject:v1

#configuracion del GKE
gcloud config set compute/zone us-central1-a 
gcloud container clusters create cluster-final --num-nodes=3
touch deployment.yml
#pegar configuracion de docker.
nano deployment.yml 
kubectl apply -f deployment.yml
```


# Google Engine y Network Balancer (Deployment)

docker build --platform linux/amd64 -t angelhigueros11/frontend .
docker run -d -p 80:3000 --name frontend angelhigueros11/frontend
docker push angelhigueros11/frontend



# App Engine (Deployment)

<!-- Primera vez -->
git clone https://github.com/1Optimus/GCP-project.git
npm i 
npm run build
gcloud app deploy

<!-- actualizar -->
git pull
npm run build
gcloud app deploy


https://gcp-gcp-final.uc.r.appspot.com



# Cloud Monitoring
## CREAR VM Y HACER DEPLOY
```sh
# Activar APIs and services
gcloud services enable runtimeconfig.googleapis.com
gcloud services enable stackdriver.googleapis.com

# Crear un deployment
gcloud deployment-manager deployments create dsudeployment --config deployment.yaml


docker stop gcp-frontend
docker rm  gcp-frontend
docker rmi angelhigueros11/gcp-frontend:latest
docker run -d -p 80:3000 --name gcp-frontend  angelhigueros11/gcp-frontend:latest



```
## INSTALAR HERRAMIENTAS EN LA VM 
```sh

# instalar stress
sudo apt install stress-ng
sudo apt install stress 

curl -sSO  https://dl.google.com/cloudagents/install-monitoring-agent.sh
curl -sSO  https://dl.google.com/cloudagents/install-logging-agent.sh

sudo bash install-logging-agent.sh
sudo bash install-monitoring-agent.sh


# Peticiones de prueba
stress-ng --cpu 1 --timeout 60s --metrics-brief
```