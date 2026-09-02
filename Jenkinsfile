pipeline {
    agent any

    environment {
        DOCKER_PATH = 'C:\\Users\\student1\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin'
    }

    stages {

        stage('Test Docker') {
            steps {
                bat '''
                    set PATH=%DOCKER_PATH%;%PATH%
                    docker --version
                    docker ps
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '''
                    set PATH=%DOCKER_PATH%;%PATH%
                    docker build -t myapp:latest .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                    set PATH=%DOCKER_PATH%;%PATH%

                    docker stop myapp
                    if %ERRORLEVEL% NEQ 0 echo Container not running

                    docker rm myapp
                    if %ERRORLEVEL% NEQ 0 echo Container does not exist

                    docker run -d --name myapp -p 8000:3000 myapp:latest
                '''
            }
        }
    }
}