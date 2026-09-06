pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t naveen-nginx:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop naveen-nginx 2>/dev/null || true
                    docker rm naveen-nginx 2>/dev/null || true
                    docker run -d --name naveen-nginx -p 8081:80 naveen-nginx:latest
                '''
            }
        }
    }
}
