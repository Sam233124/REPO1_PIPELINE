pipeline {
    agent any
    
    stages {
        stage('Copy index.html to Apache Webserver') {
            steps {
                script {
                    // SSH-credentials ID (configure this in Jenkins credentials)
                    def sshCredentialsId = '74a84b86-0524-41f1-9c56-a63b2164a16b'
                    
                    // Doelserverinformatie
                    def remoteServer = '192.168.1.8'
                    def remoteUsername = 'student'
                    def remotePassword = 'poepie'

                    // SCP-commando met sshpass
                    sh "sshpass -p ${remotePassword} scp -r /var/lib/jenkins/workspace/Pipeline_main/*.html ${remoteUsername}@${remoteServer}:/var/www/html/"
                }
            }
        }
    }
}
