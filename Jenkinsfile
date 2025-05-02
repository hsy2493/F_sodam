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
		        // Spring Boot (Gradle 사용)pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git', branch: 'main'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
		        sh './gradlew clean build -x test'
		        sh 'cd build/libspipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-id', url: 'https://github.com/hsy2493/F_sodam.git', branch: 'main'
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
} && docker build -t my-springboot-app .'
            }
        }
        stage('Run Spring Boot Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name springboot my-springboot-app'
            }
        }
    }
}