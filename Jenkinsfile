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
                docker.build('my-springboot-app') {
                    dockerfile '.'
                }
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                docker.image('my-springboot-app').withRun('-p 8080:8080 --name springboot') {
                    // 컨테이너가 실행되는 동안 수행할 작업 (선택 사항)
                    // 예를 들어 로그 확인 등
                    sh 'echo "Spring Boot 애플리케이션 실행 중..."'
                }
            }
        }
    }
}