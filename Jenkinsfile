pipeline{
    agent any

    stages{
        stage('zip the file'){
            steps{
                sh 'rm -rf *.zip || echo ""'
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
        stage('publish to ansible server'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible-server', \
                transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'unzip ansible-${BUILD_ID}.zip; rm -rf ansible-${BUILD_ID}.ZIP; rm -rf ansible-${BUILD_ID}.zip', \
                execTimeout: 120000, flatten: false, makeEmptyDirs: false, \
                noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', \
                remoteDirectorySDF: false, removePrefix: '', \
                sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, \
                useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
    