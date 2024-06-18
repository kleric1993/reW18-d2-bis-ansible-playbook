pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.ZIP * --EXCLUDE Jenkinsfile'
                sh 'ls -l'
            }
        }
    }
}
    