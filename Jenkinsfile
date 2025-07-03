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
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    rm -f test-results/junit.xml || true
                    rmdir test-results || true
                    ls -la
                    
                '''
            }
        }
    }
}
