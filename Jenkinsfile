pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            // Scoatem reuseNode true pentru a nu ne mai chinui cu permisiunile de folder din Windows
            args '-u root --dns 8.8.8.8' 
        }
    }

    stages {
        stage('Install & Build') {
            steps {
                sh '''
                    echo "Suntem in interiorul containerului Node..."
                    node -v
                    npm -v
                    
                    # Instalam totul de la zero in memoria containerului
                    npm install --no-audit
                    
                    # Pornim build-ul
                    npm run build
                    
                    ls -la build
                '''
            }
        }
    }
}