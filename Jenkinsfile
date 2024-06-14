pipeline {
    agent any

    
    environment {
        GITHUB_TOKEN = credentials('github_token')
    }

    stages {
        stage('Clone Repository') {
            steps {
                
                 script {
                    def githubEvent = env.GITHUB_EVENT_NAME
                    if (githubEvent == 'push') {
                        echo 'This is a push event'
                    }
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
