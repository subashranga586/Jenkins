pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/subashranga586/Jenkins.git'
            }
        }
        stage('Build Docker Images') {
            steps {
                script {
                    docker.build('sample-web-app', '-f Dockerfile .')
                }
            }
        }
        stage('Run Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests or check if app is running
                    sh 'curl -f http://localhost:3000'
                }
            }
        }
        stage('Cleanup') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}
