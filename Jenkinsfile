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
                sh '''
                    aws --version

                    df -h

                    find / -type f
                '''
                            
            }
        }
    }
}