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
            printContributedVariables: false,
            printPostContent: false, // Print post content
            silentResponse: false,
            shouldNotFlatten: false,
            regexpFilterText: '$ref'
        )
    }
    stages {
        stage('Some step') {
         // when {
        //        expression {
        //            return false
        //        }
        //    }
            steps {
                script {
                     sh '''
                    echo shiit
                    PAYLOAD="$payload" 
                    echo wpisane
                    KEYS=$(echo "$PAYLOAD" | jq -r 'keys[]' )
                    echo $KEYS
                    echo shiit
                    '''
                }
            }
        }
        stage('Deliver') {
            steps {
                script {
                    // Wyświetlenie przycisku do kontynuacji
                      def userInput = input(
                        id: 'userInput',
                        message: 'Czy chcesz kontynuować dostarczanie?',
                        parameters: [
                            choice(name: 'Wybierz akcję', choices: ['Kontynuuj', 'Anuluj'], description: 'Wybierz, co chcesz zrobić')
                        ]
                    )
                    echo "Użytkownik wybrał: ${userInput}"

                    
                }
            }
        }
    }
}
