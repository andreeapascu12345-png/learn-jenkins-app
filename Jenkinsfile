pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    args '-u root --dns 8.8.8.8 --memory="2g"' // Adăugăm limită de memorie
                }
            }
            steps {
                sh '''
                    # 1. Ștergem resturile de la instalările eșuate
                    rm -rf node_modules package-lock.json
                    
                    # 2. Instalare forțată cu cache curat
                    npm cache clean --force
                    npm install --no-audit --loglevel info
                    
                    # 3. Verificăm dacă react-scripts a apărut
                    ls -la node_modules/.bin/react-scripts || echo "EROARE: react-scripts tot lipsește!"
                    
                    # 4. Rulăm build-ul
                    npm run build
                '''
            }
        }
    }
}