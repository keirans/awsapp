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
                    export AWS_DEFAULT_REGION="ap-southeast-2"
                    export CFNSTACKNAME=`echo $BUILD_TAG | sed 's/jenkins-//g'`
                    echo "Commencing build of Application: ${JOB_NAME} - Branch: ${GIT_BRANCH} - Build: ${BUILD_NUMBER}"
                    echo "AWS CLI Version : `aws --version`"
                    echo "Cloudformation Stack Name: $CFNSTACKNAME"

                    if [ -f ./template.yaml ]; then
                        echo "Template YAML file found for deployment"
                    else
                        echo "Template YAML NOT found for deployment"
                        exit 1
                    fi
                '''
            }
        }
    }
}