pipeline {

  agent any

  stages {
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-east-2',credentials: ' 5c53fd8d-6340-46fa-9836-a479310c15bb') {
        sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-blueocean-pipeline')
        }
      }
    }
  }
}
