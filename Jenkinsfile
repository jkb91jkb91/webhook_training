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
        stage('Deliver and MERGE') {
            steps {
                script {
                      def userInput = input(
                        id: 'userInput',
                        message: 'MERGE REUQEST',
                        parameters: [
                            choice(name: 'CONFIRM MR', choices: ['MERGE'])
                        ]
                      )
                      sh '''
                         githubApiUrl='https://api.github.com'
                         prNumber='38'
                         githubToken='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'
                        curl -X PUT -u "jkb91jkb91:${githubToken}" ${githubApiUrl}/repos/jkb91jkb91/webhook_training/pulls/${prNumber}/merge
                      '''
                }
            }
        }
    }
}
