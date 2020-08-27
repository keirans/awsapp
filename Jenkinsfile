pipeline {
    agent any

    environment {
        Environment = 'nonp'
    }
    stages {
        stage('Validate Template') {
            steps {
                withAWS(region:'ap-southeast-2',credentials:'AWSDemoCredentials') {
                    cfnValidate(file: 'template.yaml')
                }
            }
        }
        stage('Create Stack') {
            steps {
                withAWS(region:'ap-southeast-2',credentials:'AWSDemoCredentials') {
                    cfnVUpdate(file: 'template.yaml', stack:"app-${ENVIRONMENT}-${GIT_BRANCH}-${BUILD_ID}" , pollInterval:1000)
                }
            }
        }
    }
}