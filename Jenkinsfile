pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-simple-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run --rm devops-simple-app'
            }
        }
    }
}

