pipeline {
    agent any
    stages {
        stage('Node') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                    node --version
                '''
            }
        }
        stage('AWS') {
            agent {
                docker {
                    image 'amazon/aws-cli:'
                }
            }
            steps {
                sh '''
                    aws --version
                '''
            }
        }        
    }
}
