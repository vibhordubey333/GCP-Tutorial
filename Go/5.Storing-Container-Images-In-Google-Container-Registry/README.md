1. `gcloud cloud-shell ssh` <br>
2. Once SSH connection is open execute below commands.<br>
```
gcloud services enable containerregistry.googleapis.com

export PROJECT_ID=cpl-ddcs-l-sandbox-01

docker pull busybox

docker images
```
3. Now create a Dockerfile in Google Cloud Shell only[SSH connection]
```
from busybox:latest
CMD ["date"]
```
4. Execute below commands.

```
docker build . -t mybusybox

docker tag mybusybox gcr.io/$PROJECT_ID/mybusybox:latest

docker run gcr.io/$PROJECT_ID/mybusybox:latest

gcloud auth configure-docker

docker push gcr.io/$PROJECT_ID/mybusybox:latest
```

4. Image should be pushed to Google Container Registry.
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/a9316e6b-7ee7-46d9-9fa7-e17f8c7cfa58)

