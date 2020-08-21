pipeline {
    agent none
    stages {
        stage('Validate Template') {
            agent {
                docker { image 'amazon/aws-cli' }
            }
            steps {
                echo 'AWS CLI Version'
                echo '-------------------'
                aws --version
            }
        }
    }
}