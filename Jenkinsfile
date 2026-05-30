pipeline {
    agent any

    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Select environment')
    }

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
                
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'my-remote-server',
                            verbose: true,
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*',
                                    remoteDirectory: "/${params.ENV}",
                                    execCommand: """
                                        echo "========================================="
                                        echo "Deployment to ${params.ENV} completed"
                                        echo "Files copied to /home/user/deploy/${params.ENV}"
                                        ls -la /home/user/deploy/${params.ENV}/
                                        echo "========================================="
                                    """
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }

    post {
        always {
            echo "Cleaning workspace..."
            cleanWs()
        }
    }
}
