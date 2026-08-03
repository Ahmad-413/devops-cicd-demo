pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Repository cloned successfully'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-cicd-demo .'
            }
        }
        stage('Run Container') {
            steps {
                sh '''
                docker stop devops-cicd-demo || true
                docker rm devops-cicd-demo || true

                docker run -d \
                 --name devops-cicd-demo \
                 -p 5000:5000 \
                 devops-cicd-demo
                '''
            }
        }
    }
}