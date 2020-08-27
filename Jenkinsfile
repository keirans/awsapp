pipeline {
    agent any

    environment {
        ENVIRONMENT = 'nonp'
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
                    cfnUpdate(file: 'template.yaml', stack:"app-${ENVIRONMENT}-${GIT_BRANCH}-${BUILD_ID}" , pollInterval:1000)
                }
            }
        }
    }
}