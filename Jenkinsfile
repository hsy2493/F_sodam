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
                script {
                    docker.build(image: 'my-springboot-app', dockerfile: 'Dockerfile')
                }
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                script {
                    docker.image(image: 'my-springboot-app').withRun(ports: '8080:8080', name: 'springboot')
                }
            }
        }
    }
}