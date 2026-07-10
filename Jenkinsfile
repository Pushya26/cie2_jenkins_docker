pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Pushya26/cie2_jenkins_docker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cie2:latest .'
            }
        }
        stage('Cleanup Old Container') {
            steps {
                sh 'docker rm -f cie2-app || true'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8083:80 --name cie2-app cicd-demo:latest'
            }
        }
    }
}
