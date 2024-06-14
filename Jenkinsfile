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
                    PAYLOAD=$payload
                    if [ "${PAYLOAD}" == *pushed_at* ]; then
                      echo ZNALAZLEM
                    fi
                    
                    echo shiit
                    '''
                }
            }
        }
    }
}
