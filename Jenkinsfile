pipeline {
    agent any // Folosește Node-ul instalat direct pe sistemul unde e Jenkins

    stages {
        stage('Install') {
            steps {
                sh 'npm install --no-audit'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
}