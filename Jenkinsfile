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
                    node --version
                    npm --version                
                    echo "checking files at the starting of the container"
                    ls -la
                    npm ci
                    echo "Checking files after npm ci"
                    ls -la
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
