pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'git-cred'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: env.GIT_CREDENTIALS_ID, url: 'https://github.com/Ishan-Bharti/ishan-demo.repo'
            }
        }
        stage('Run Docker Compose') {
            steps {
                script {
                    // Run Docker Compose commands in the root directory
                    sh 'docker-compose docker-compose.yml up -d'
                }
            }
        }
    }
}
