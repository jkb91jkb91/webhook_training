pipeline {
    agent any

    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'action', value: '$.action']
            ],
            causeString: 'Triggered on $action',
            token: 'your-token',
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

                    // Sprawdzenie, czy istnieje właściwość 'ref'
                    if (env.payload && env.payload.ref) {
                        echo "Ref: ${env.payload.ref}"
                    }
                }
            }
        }
        // Pozostałe etapy...
    }
}
