pipeline {
    agent any
    stages {
        stage('Example') {
          try{
            timeout(time: 60, unit: 'SECONDS'){
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            }
            }
            catch(err){
              echo "Aborted"
              currentBuild.result = "SUCCESS"
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }
}
