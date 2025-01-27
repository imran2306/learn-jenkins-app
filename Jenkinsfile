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
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    #test -f build/index.html
                    npm test
                '''
            }
        }
        stage('End To End Test') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.50.0-noble'
                    args '-u root:root'
                    reuseNode true
                }
            }

            steps {
                sh '''
                   npm install serve
                   #node_modules/.bin/serve -s build
                   #above command will serve the build and stuck there until we abort it.
                   node_modules/.bin/serve -s build &
                   sleep 10
                   npx playwright test
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
