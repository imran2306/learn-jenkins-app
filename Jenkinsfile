pipeline {
    agent any
    stages {
        stage('Node') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
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
                    image 'amazon/aws-cli:2.23.11'
                    reuseNode true
                    args '-entrypoint'''
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
