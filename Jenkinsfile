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
        stages('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
    }
}
