pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git', branch: 'main'
            }
        }
        stage('Install Docker Client') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y docker-ce-cli'
            }
         }   
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-springboot-app .'
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name springboot my-springboot-app'
            }
        }
    }
}