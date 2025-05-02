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
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build -t my-springboot-app .'
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                sh '/usr/local/bin/docker run -d -p 8080:8080 --name springboot my-springboot-app'
            }
        }
    }
}