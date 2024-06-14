pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('github_token')
    }
    stages {
        stage('Check GitHub Event') {
            steps {
                script {
                    def githubEvent = env.GITHUB_EVENT_NAME
                    if (githubEvent == 'push') {
                        echo 'This is a push event'
                    } else {
                        echo "Unknown GitHub event type: ${githubEvent}"
                        
                    }
                }
            }
        }
        stage('Clone Repository') {
            steps {
                // Kroki do klonowania repozytorium, jeśli są wymagane
                sh 'echo Cloning repository...'
            }
        }
        stage('Build') {
            steps {
                sh 'echo Building...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Testing...'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying...'
            }
        }
    }
}
