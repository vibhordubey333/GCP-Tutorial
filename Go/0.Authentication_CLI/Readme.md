#### Authentication From CLI Using Browser
gcloud auth application-default login

#### Authentication Using Service JSON File
  - To download service JSON file. Go to `Google Console > API Services > Credentials `. Refer below snap.
    ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/de8c0878-3963-4e0b-9473-b3788c6558bb)
  - Go to service accounts listed below or create new by clicking on "+ Create Credentials"
    ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/87a64ad1-0977-4d13-82b9-1033b1cde73f)
  - Download and place in a path. For instance, /root/
  - Execute command `gcloud auth login --cred-file=/root/credentials.json`

