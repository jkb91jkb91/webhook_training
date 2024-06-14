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
        when {
                // Warunek uniemożliwiający uruchomienie joba
                expression {
                    return false
                }
            }
        stage('Some step') {
            steps {
                script {
                     sh '''
                    echo shiit
                    echo $payload
                    echo shiit
                    '''
                }
            }
        }
    }
}
