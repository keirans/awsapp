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
                    cfnVUpdate(file: 'template.yaml', stack:"app-${ENVIRONMENT}-${GIT_BRANCH}-${BUILD_ID}" , pollInterval:1000)
                }
            }
        }
        stage('Delete Stack') {
            input { 
                message "Should we tear down the deployment ?"
                ok "Yes, We should"
            }
            steps {
                withAWS(region:'ap-southeast-2',credentials:'AWSDemoCredentials') {
                    cfnDelete(stack:"app-${ENVIRONMENT}-${GIT_BRANCH}-${BUILD_ID}" , pollInterval:1000)
                }
            }
        }
    }
}