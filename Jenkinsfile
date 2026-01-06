pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/SyedWaqeer/react-node-jenkins-demo.git',
                credentialsId: 'github-token'
            }
        }

        stage('Install Backend') {
            steps {
                dir('server') {
                    sh 'npm install'
                }
            }
        }

        stage('Test Backend') {
            steps {
                dir('server') {
                    sh 'npm test'
                }
            }
        }

        stage('Install Frontend') {
            steps {
                dir('client') {
                    sh 'npm install || true'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('client') {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo '✅ GitHub CI Pipeline Successful'
        }
        failure {
            echo '❌ Pipeline Failed'
        }
    }
}
