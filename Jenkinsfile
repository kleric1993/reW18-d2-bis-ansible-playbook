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
                sh 'curl -uadmin:AP4tbU8yG28DhL74UFcmddLM23r -T <PATH_TO_FILE> "http://ec2-52-55-109-255.compute-1.amazonaws.com:8081/artifactory/ansible/<TARGET_FILE_PATH>"'
            }
        }
    }
}
    