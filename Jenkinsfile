pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                        echo "Multiline shell works too"
                        ls -lah
                    '''
            }
        }
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS') {
            steps {
                // withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsID: 'udacityDevops', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']])
                withAWS(region: 'us-west-2', credentials: 'udacityDevops') {
                    s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled:true, file: index.html, bucket:'jenkinspipelinespractice')
                }
            }
        }
    }
}
