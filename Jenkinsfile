pipeline {
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