pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git', branch: 'main'
            }
        }
        stage('Build and Package') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew clean build -x test'
                sh 'cd build/libs'
                user id: 'root', script: 'docker build -t my-springboot-app .'
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                user id: 'root', script: 'docker run -d -p 8080:8080 --name springboot my-springboot-app'
            }
        }
    }
}