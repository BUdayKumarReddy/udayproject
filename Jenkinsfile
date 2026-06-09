pipeline {
    agent any

    stages {

        stage('Build Frontend') {
            steps {
                sh 'docker build -t frontend-test ./frontend'
            }
        }

        stage('Build Backend') {
            steps {
                sh 'docker build -t backend-test ./backend'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f frontend backend || true

                docker run -d --name frontend -p 3000:80 frontend-test
                docker run -d --name backend -p 5000:5000 backend-test
                '''
            }
        }
    }
}
