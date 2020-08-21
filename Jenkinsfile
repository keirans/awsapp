pipeline {
    agent none
    stages {
        stage('Validate Template') {
            agent {
                docker {
                    image 'amazon/aws-cli'
                    args '-i --entrypoint='
                    }
            }
            steps {
                echo 'AWS CLI Version'
                echo '-------------------'
                sh 'aws --version'
            }
        }
    }
}