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
                docker.build(image: 'my-springboot-app', dockerfile: '.')
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                docker.run(image: 'my-springboot-app', ports: '8080:8080', name: 'springboot')
            }
        }
    }
}