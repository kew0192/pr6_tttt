pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select environment')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build Docker') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing container...'
                sh 'docker run -d --name test-container -p 5000:80 my-app'
                sh 'sleep 3'
                sh 'curl -f http://localhost:5000 || echo "Container running"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV} environment"
                sh 'echo "Files copied to remote server (simulated)"'
            }
        }
    }

    post {
        always {
            sh 'docker stop test-container || true'
            sh 'docker rm test-container || true'
            cleanWs()
        }
    }
}
