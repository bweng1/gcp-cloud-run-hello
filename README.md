# hello-cloud-run

- Enable the Cloud Run API.
  From Cloud Shell, run 
  > gcloud services enable run.googleapis.com

- Create a simple Node.js application that can be deployed as a serverless, stateless container.

- Build Dockerfile on localhost
  > docker build -t hellocloudrun .

- Using Cloud Build to build Dockerfile and upload to Artifact Registry.
  > gcloud builds submit --tag gcr.io/$GOOGLE_CLOUD_PROJECT/hellocloudrun

  > gcloud auth configure-docker

- Localhost testing
  > docker run -d -p 8080:8080 hellocloudrun

- Cloud Shell testing
  > docker run -d -p 8080:8080 gcr.io/$GOOGLE_CLOUD_PROJECT/hellocloudrun

- Deploy a containerized application on Cloud Run.
  > gcloud run deploy --image gcr.io/$GOOGLE_CLOUD_PROJECT/hellocloudrun --allow-unauthenticated --region=$LOCATION

-> Clean up
  > gcloud container images delete gcr.io/$GOOGLE_CLOUD_PROJECT/hellocloudrun
  > gcloud run services delete helloworld --region="REGION"

