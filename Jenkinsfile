pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "checking files at the starting of the container"
                    ls -la
                    node --version
                    npm --version                
                    npm ci
                    echo "Checking files after npm ci"
                    ls -la
                    npm run build
                    ls -la
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
