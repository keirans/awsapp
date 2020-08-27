pipeline {
    agent none
    stages {
        stage('Validate Template') {
            steps {
                withAWS(region:'ap-southeast-2',credentials:'AWSDemoCredentials') {
                    cfnValidate(file: 'template.yaml')
                }
            }
        }
    }
}