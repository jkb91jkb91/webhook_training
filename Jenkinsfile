pipeline {
    agent any

    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'action', value: '$.action']
            ],
            causeString: 'Triggered on $action',
            token: 'gowno',
            printContributedVariables: true,
            printPostContent: true,
            silentResponse: false
        )
    }

    stages {
        stage('Check Trigger Type') {
            steps {
                script {
                    // Odczytanie typu wyzwalacza
                    def triggerType = env.action

                    echo "Trigger Type: ${triggerType}"
                }
            }
        }
        // Reszta stages...
    }
}
