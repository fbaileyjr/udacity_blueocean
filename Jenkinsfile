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
                withAWS(region:'us-east-2',credentials:'fbailey') {
                sh 'echo "Uploading content with AWS credentials"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-c3-l2-pipelines')
                    }
            }
        }
    }
}
