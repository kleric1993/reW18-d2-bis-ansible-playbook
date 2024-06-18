pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'zip ansible-${BUILD_ID}.ZIP * --exclude Jenkinsfile'
                sh 'ls -l'
            }
        }
    }
}
    