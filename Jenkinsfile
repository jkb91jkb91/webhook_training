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
                    echo "${githubEvent}"

                    def eventName = sh(script: 'echo $GITHUB_EVENT_NAME', returnStdout: true).trim()
                    def eventAction = sh(script: 'echo $GITHUB_EVENT_ACTION', returnStdout: true).trim()
                    echo "GitHub Event Name: ${eventName}"
                    echo "GitHub Event Action: ${eventAction}"
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
