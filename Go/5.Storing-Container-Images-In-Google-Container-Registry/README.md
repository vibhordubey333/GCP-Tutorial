0. Login to GCP.<br/>
 ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/07b23a10-6f9b-448f-84ec-7f69c433a7d0)
  
1. Search for Container Registry. <br/>
 ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/1ee1a9dd-f0e9-4095-9137-d0cb130b0e7b)<br/>
 ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/33e55491-c709-4749-a8b3-cdd1bd69b15d)

2. `gcloud cloud-shell ssh` <br>
3. Once SSH connection is open execute below commands.<br>
```
gcloud services enable containerregistry.googleapis.com

export PROJECT_ID=cpl-ddcs-l-sandbox-01

docker pull busybox

docker images
```
4. Now create a Dockerfile in Google Cloud Shell only[SSH connection]
```
from busybox:latest
CMD ["date"]
```
5. Execute below commands.

```
docker build . -t mybusybox

docker tag mybusybox gcr.io/$PROJECT_ID/mybusybox:latest

docker run gcr.io/$PROJECT_ID/mybusybox:latest

gcloud auth configure-docker

docker push gcr.io/$PROJECT_ID/mybusybox:latest
```

6. Image should be pushed to Google Container Registry.
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/a9316e6b-7ee7-46d9-9fa7-e17f8c7cfa58)

