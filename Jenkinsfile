pipeline {
    agent any
    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'payload', value: '$'] // Przekazujemy cały payload jako zmienną
            ],
            causeString: 'Triggered on $ref',
            token: 'gowno',
            tokenCredentialId: '',
            printContributedVariables: true,
            printPostContent: true, // Print post content
            silentResponse: false,
            shouldNotFlatten: false,
            regexpFilterText: '$ref'
        )
    }
    stages {
        stage('Some step') {
            steps {
                script {
                    // Odczytaj treść żądania (payload) z parametrów
                    def payloadContent = params.payload
                    echo "Received Payload: ${payloadContent}"
                }
            }
        }
    }
}
