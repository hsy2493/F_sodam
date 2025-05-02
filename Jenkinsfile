pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git tool: '/usr/local/bin/git', credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git'
            }
        }
        stage('Build and Package') {
		    steps {
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