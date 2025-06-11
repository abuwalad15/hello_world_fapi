pipeline {
    agent any

    environment {
        IMAGE_NAME = "hello_world-app"
    }

    stages {
        stage('Clone from GitHub') {
            steps {
                git url: 'https://github.com/abuwalad15/hello_world_fapi.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t ${IMAGE_NAME} .'
                }
            }
        }

        stage('Stop Running Containers') {
            steps {
                script {
                    sh 'docker-compose down || true'
                }
            }
        }

        stage('Run Docker Compose') {
            steps {
                script {
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }
}
