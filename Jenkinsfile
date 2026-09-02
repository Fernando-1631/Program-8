pipeline {
    agent any

    stages {

        stage('Test Docker') {
            steps {
                bat 'docker --version'
                bat 'docker ps'
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
                    docker stop myapp
                    if %ERRORLEVEL% NEQ 0 exit /b 0

                    docker rm myapp
                    if %ERRORLEVEL% NEQ 0 exit /b 0

                    docker run -d --name myapp -p 3000:3000 myapp:latest
                '''
            }
        }
    }
}