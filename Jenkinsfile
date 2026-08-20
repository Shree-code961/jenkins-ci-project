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
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                        docker push shreedevihalli/docker-ci-project:v2
                        docker logout
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container...'

                sh '''
                    docker pull shreedevihalli/docker-ci-project:v2

                    docker stop docker-ci-container || true
                    docker rm docker-ci-container || true

                    docker run -d \
                        --name docker-ci-container \
                        -p 8081:80 \
                        shreedevihalli/docker-ci-project:v2
                '''
            }
        }
    }
}
