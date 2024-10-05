pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            }
    }
    stages {
        stage('Build') {
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
        stage('test'){
            steps {
                sh '''
                npm test
                '''
            }
        }
    }
    post{
        always {
            junit 'test-results/junit.xml'
        }
    }
}
