pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                   echo "Multiline shell steps works too"
                   ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {l
                sh 'tidy -q -e *.html'
              }
         }
         // stage('Security Scan') {
         //      steps { 
         //        aquaMicroscanner imageName: 'alpine:latest', notCompilesCmd: 'exit 1', onDisallowed: 'fail', outputFormat: 'html'
         //      }
         // }         
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'cb760bce-5da0-42f2-9bb4-43a3387ab483') {
                  sh 'echo "Uploading content with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-blueocean-pipeline')
                  }
              }
         }
     }
}
