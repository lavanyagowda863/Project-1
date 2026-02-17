pipeline {
    agent any 
    stages {
        stage('Checkout') {
    steps {
        // 'github-token' must match the "ID" you gave your PAT in Jenkins
        git credentialsId: 'githubtoken', url: 'https://github.com/lavanyagowda863/Project-1.git'
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

