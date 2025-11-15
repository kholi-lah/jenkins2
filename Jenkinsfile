pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/kholi-lah/jenkins2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t muk2-app .'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests (dummy)..."
                sh 'echo "Test Passed!"'
            }
        }

        stage('Deploy to Server') {
            steps {
                echo "Stopping old container..."
                sh '''
                    docker stop muk2 || true
                    docker rm muk2 || true
                '''

                echo "Running new container..."
                sh '''
                    docker run -d --name muk2 -p 8081:80 muk2-app
                '''
            }
        }
    }
}
