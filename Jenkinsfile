pipeline {
    agent any
    environment {
        APPROVAL_NO = ''
    }
    stages {
        stage ('Checkout') { steps { echo "Checkout" } }
        stage ('Build') { steps { echo "Build" } }
        stage ('Docker Image Build') { steps { echo "Docker Image Build" } }
        stage ('Docker Image Push') { steps { echo "Docker Image Push" } }
        stage ('Staging Deploy') { steps { echo "Staging Deploy" } }
    }
    post {
        success {
            slackSend(tokenCredentialId: 'slack-token',
                        channel: '#cicd',
                        color: 'good',
                        message: "${JOB_NAME} (${BUILD_NUMBER}) 빌드가 성공적으로 끝났습니다. (<${BUILD_URL} : 여기>)")

        }
        failure {
            slackSend(tokenCredentialId: 'slack-token',
                        channel: '#cicd',
                        color: 'danger',
                        message: "${JOB_NAME} (${BUILD_NUMBER}) 빌드가 실패하였습니다. (<${BUILD_URL} : 여기>)")

        }
    }
}