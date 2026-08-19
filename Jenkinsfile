pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the HTML application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the application...'
            }
        }

        stage('Deploy') {
            steps {
                sh 'cp index.html /var/www/html/index.html'
                echo 'HTML application deployed to Apache!'
            }
        }
    }
}
