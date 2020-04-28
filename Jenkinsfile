pipeline {
    agent any
    stages {
        stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
              script{
                try{
                  echo "Hello, ${PERSON}, nice to meet you."
                  }
                  catch (err){
                    echo "Aborted by user"
                    currentBuild.result = "SUCCESS"
                  }
                }
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
            sh '{currentBuild.result} = "SUCCESS"'
        }
    }
}
