pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Выберите окружение для деплоя')
    }

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
                
                // Имитация копирования на удаленный сервер через SSH
                // (без реального SSH-сервера - просто вывод команды)
                sh 'echo "Copying application files to remote server via SSH..."'
                sh 'echo "Files copied to /var/www/app on ${params.ENV} server"'
            }
        }
    }

    post {
        always {
            echo "Cleaning workspace..."
            cleanWs()  // Очищает рабочую директорию
        }
    }
}
