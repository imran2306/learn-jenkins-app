pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    node --version
                    npm --version                
                    echo "checking files at the starting of the container"
                    ls -la
                    npm clean install
                    echo "Checking files after npm install"
                    ls -la
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
