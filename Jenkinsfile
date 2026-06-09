pipeline {

    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/username/fullstack-app.git'
            }
        }

        stage('Build Backend') {
            steps {
                sh 'cd backend && mvn clean package'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy Containers') {
            steps {
                sh '''
                docker compose down
                docker compose up -d
                '''
            }
        }
    }
}
