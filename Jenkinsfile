pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Anupj11/CI-with-jenkins.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-static-site .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop static-site || true
                docker rm static-site || true
                docker run -d --name static-site -p 9090:80 my-static-site 
                '''
            }
        }
    }
}
