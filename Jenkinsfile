pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.ZIP * --exclude Jenkinsfile'
            
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:AP4tbU8yG28DhL74UFcmddLM23r -T \
                ansible-${BUILD_ID}.ZIP \
                "http://ec2-54-197-112-53.compute-1.amazonaws.com:8081/artifactory/ansible/ansible-${BUILD_ID}.ZIP"'
            }
        }
    }
}
    