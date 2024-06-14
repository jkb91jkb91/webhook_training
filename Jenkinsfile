pipeline {
    agent any
    
    environment {
        GITHUB_TOKEN = credentials('github_token')
    }

    stages {
        stage('Clone Repository') {
            steps {
                 sh 'echo FFsdsdsdTRIGGERED'
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
