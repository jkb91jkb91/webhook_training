pipeline {
    agent any


    
    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'payload', value: '$.payload'] // Przekazujemy payload jako zmienną
            ],
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
