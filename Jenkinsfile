pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git'
            }
        }
        stage('Build and Package') {
            steps {
                // Spring Boot (Gradle 사용)
                sh 'cd springboot && ./gradlew clean build -x test'
                sh 'cd springboot && docker build -t my-springboot-app .'

                // FastAPI
                sh 'cd fastapi && pip install -r requirements.txt'
                sh 'cd fastapi && docker build -t my-fastapi-app .'
            }
        }
        stage('Run Docker Containers') {
            steps {
                sh 'docker run -d -p 8080:8080 --name springboot my-springboot-app'
                sh 'docker run -d -p 8000:8000 --name fastapi my-fastapi-app'
            }
        }
    }
}