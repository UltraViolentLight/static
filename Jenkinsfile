pipeline {
     agent any
     stages {    
        stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }   
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'eu-central-1',credentials:'jenkins_user') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline-uvl')
                  }
              }
         }
     }
}