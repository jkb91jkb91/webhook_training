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
                    "${payload}" > payload.txt
                    echo wpisane
                    grep -q "pushed_at" payload.txt && echo "Znalazłem 'pushed_at' w pliku payload.txt" || echo "Nie znaleziono 'pushed_at' w pliku payload.txt"  
                    echo shiit
                    '''
                }
            }
        }
    }
}
