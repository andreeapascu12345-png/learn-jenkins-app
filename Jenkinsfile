pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u root --dns 8.8.8.8' 
                }
            }
            steps {
                sh '''
                    ls -la 
                    node --version
                    npm install --no-audit
                    npm run build 
                    ls -la
                '''
            }
        }
    }
}