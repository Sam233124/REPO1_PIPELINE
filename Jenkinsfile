pipeline {
    agent any

    stages {
        stage('Checkout from GitHub (productie)') {
            steps {
                // Check out your code from the "productie" branch on GitHub.
                script {
                    def scmVars = checkout([
                        $class: 'GitSCM',
                        branches: [[name: 'productie']],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [
                            [$class: 'CloneOption', noTags: false, reference: '', shallow: false],
                            [$class: 'CleanBeforeCheckout'],
                        ],
                        userRemoteConfigs: [[url: 'https://github.com/Sam233124/REPO1_PIPELINE.git']]
                    ])
                }
            }
        }

        stage('Deploy to Testserver') {
            steps {
                // Copy HTML files from the "productie" branch to the test server.
                sh 'sshpass -p student scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Sam_main/index.html student@192.168.1.9:/var/www/html/'
            }
        }

        stage('Confirmation Dev') {
            steps {
                // Prompt for confirmation before proceeding.
                input(id: 'confirmDeployment', message: 'Review the test environment. If everything looks good, approve for Development.', ok: 'Deploy')
            }
        }


        stage('Deploy to test Server') {
            steps {
                sh 'sshpass -p student scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Sam_main/index.html student@192.168.1.8:/var/www/html/'
            }
        }
    }
}
