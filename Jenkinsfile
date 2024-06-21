pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile'
            
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:AP4tbU8yG28DhL74UFcmddLM23r -T \
                ansible-${BUILD_ID}.zip \
                "http://ec2-52-55-109-255.compute-1.amazonaws.com:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }
}
    