pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'git-cred'
        SSH_CREDENTIALS_ID = 'ishan-cred'
        REMOTE_HOST = '192.168.21.21'
        REMOTE_USER = 'cloudspace'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: env.GIT_CREDENTIALS_ID, url: 'https://github.com/Ishan-Bharti/ishan-demo.repo', branch: 'main'
            }
        }
        stage('Run Docker Compose on Remote Server') {
            steps {
                script {
                    sshagent (credentials: [env.SSH_CREDENTIALS_ID]) {
                        sh """
                            ssh -o StrictHostKeyChecking=no ${env.REMOTE_USER}@${env.REMOTE_HOST} '
                                cd ${env.WORKSPACE} &&
                                docker-compose up -d
                            '
                        """
                    }
                }
            }
        }
    }
}
