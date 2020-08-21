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
                    echo "Commencing build Branch: ${GIT_BRANCH} Build: ${BUILD_NUMBER}"
                    echo "AWS CLI Version : `aws --version`"
                    find /var/jenkins_home/workspace/awsapplication_dev/
                '''
            }
        }
    }
}