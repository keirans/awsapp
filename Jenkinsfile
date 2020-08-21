pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'amazon/aws-cli' }
            }
            steps {
                'aws --version'
            }
        }
    }
}