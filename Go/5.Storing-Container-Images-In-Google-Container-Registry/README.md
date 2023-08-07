1. gcloud cloud-shell ssh <br>
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
docker build . -t mybusybox

docker tag mybusybox gcr.io/$PROJECT_ID/mybusybox:latest

docker run gcr.io/$PROJECT_ID/mybusybox:latest

gcloud auth configure-docker

docker push gcr.io/$PROJECT_ID/mybusybox:latest

4. Image should be pushed to Google Container Registry.