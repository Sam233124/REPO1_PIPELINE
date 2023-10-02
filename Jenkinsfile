pipeline {
    agent any
    
    stages {
        stage('Copy index.html to Remote Server') {
            steps {
                script {
                    // Define your SSH credentials ID (configure this in Jenkins credentials)
                    def sshCredentialsId = '74a84b86-0524-41f1-9c56-a63b2164a16b'
                    
                    // Define the source and destination paths
                    def sourcePath = 'path/to/your/index.html'
                    def destinationPath = '/var/www/html'

                    // Define the target server and SSH port
                    def remoteServer = '192.168.1.8'
                    def sshPort = 22 // Default SSH port is 22

                    // Use the sshAgent to securely execute SSH commands
                    sshAgent(credentials: [sshCredentialsId]) {
                        // Execute the SCP command to copy the file to the remote server
                        sh "scp -P ${sshPort} ${sourcePath} ${remoteServer}:${destinationPath}"
                    }
                }
            }
        }
    }
}
