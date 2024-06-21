pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip -r ansible-${BUILD_ID}.ZIP * --exclude Jenkinsfile'
            
            }
        }
        stage('upload artifacts to jfrog'){
            steps{
                sh 'curl -uadmin:admin1234 -T ansible-${BUILD_ID}.zip \
                "http://52.55.109.255:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }
}
    