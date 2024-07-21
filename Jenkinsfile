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
                    // Navigate to the directory containing docker-compose.yml
                    dir('path/to/docker-compose-directory') {
                        // Run Docker Compose commands
                        sh 'docker-compose docker-compose.yml up -d'
                    }
                }
            }
        }
    }
}
