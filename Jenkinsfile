pipeline {
    agent any


    
    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'payload', value: '$.payload'] // Przekazujemy payload jako zmienną
            ],
            causeString: 'Triggered on $ref',
            token: 'abc123',
            tokenCredentialId: '',
            printContributedVariables: true,
            printPostContent: true,
            silentResponse: false,
            shouldNotFlatten: false,
            regexpFilterText: '$ref',
            regexpFilterExpression: 'refs/heads/' + BRANCH_NAME
        )
    }
    
    
    
    stages {
        stage('Some step') {
            steps {
                script {
                    echo "Received Payload: ${params.payload}"
                }
            }
        }
    }
}
