pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t shreedevihalli/docker-ci-project:v2 .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Docker image...'
                sh 'docker images shreedevihalli/docker-ci-project:v2'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                echo 'Pushing Docker image to Docker Hub...'
                sh 'docker push shreedevihalli/docker-ci-project:v2'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container...'
            }
        }
    }
}
