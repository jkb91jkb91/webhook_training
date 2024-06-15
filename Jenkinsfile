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
            regexpFilterText: '$ref',
            regexpFilterExpression: 'pull_request\\.opened' 
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
                    def result 
                    result = sh(script: '''
                        
                        PAYLOAD="$payload" 
                        KEYS=$(echo "$PAYLOAD" | jq -r 'keys[]' )
                        ACTION=$(echo "$PAYLOAD" | jq -r '.action')
                        PullRequestNumber=$(echo "$PAYLOAD" | jq -r '.number')
                        echo "KEYS: $KEYS"
                        echo "PullRequestNumber=$PullRequestNumber"
                        echo "ACTION: $ACTION"
                        if [ "$ACTION" = "closed" ] || [ "$ACTION" = "reopened" ]; then
                            echo "Pipeline został zatrzymany z powodu specjalnego warunku"
                            exit 1
                        fi
                        echo $PullRequestNumber > pr_number.txt
                    ''', returnStatus: true) 
                     if (result != 0) {
                        currentBuild.result = 'NOT_BUILT'
                        error "Pipeline został zatrzymany z powodu specjalnego warunku"
                    }  
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
                      withCredentials([string(credentialsId: 'jenkins_token', variable: 'TOKEN')]) {
                        def githubApiUrl = 'https://api.github.com'
                        def prNumber = readFile('pr_number.txt').trim()
                        def jenkins_token = env.TOKEN
                        echo "TOKEN: ${jenkins_token}"
                        sh """
                            curl -X PUT -u jkb91jkb91:${jenkins_token} ${githubApiUrl}/repos/jkb91jkb91/webhook_training/pulls/${prNumber}/merge
                        """
                    }
                }
            }
        }
    }
}
