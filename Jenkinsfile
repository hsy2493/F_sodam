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
                // Spring Boot (Gradle 사용)
                sh 'chmod 755 gradlew' // 좀 더 명시적인 권한 부여
                sh './gradlew clean build -x test'
                sh 'cd build/libs && docker build -t my-springboot-app .'
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name springboot my-springboot-app'
            }
        }
    }
}