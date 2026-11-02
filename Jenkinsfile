
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Chandresh365/docker-auto-build.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t chandreshkosaraju/docker-auto-build:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker rm -f jenkins-cicd-app || true'
                sh 'docker run -d --name jenkins-cicd-app -p 8082:80 chandreshkosaraju/docker-auto-build:latest'
            }
        }
    }
}
