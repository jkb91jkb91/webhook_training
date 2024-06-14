pipeline {
    agent any


    
    triggers {
        GenericTrigger(
            genericVariables: [
                 genericVariables: [
      [key: 'ref', value: '$.ref']

            ]
        )
    }
    
    
    
    stages {
        stage('Some step') {
            steps {
                sh "echo $ref"
       
            }
        }
    }
}
