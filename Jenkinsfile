pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Fernando-1631/Program-8.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t myapp:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                    docker stop myapp || exit 0
                    docker rm myapp || exit 0
                    docker run -d --name myapp -p 3000:3000 myapp:latest
                '''
            }
        }
    }
}