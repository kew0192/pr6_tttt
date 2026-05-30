pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select environment')
    }

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
                echo "Copying application files to remote server via SSH..."
                echo "Files copied to /var/www/app on ${params.ENV} server"
            }
        }
    }

    post {
        always {
            echo "Cleaning workspace..."
            // cleanWs() - закомментировано, чтобы не вызывало ошибку
            deleteDir()
        }
    }
}
