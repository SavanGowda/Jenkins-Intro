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
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }
    post {
        success {
            echo 'I have finished deploying the green deployment'
        }
        aborted {
            echo 'The build has succeeded until blue deployment. The user has aborted the green deployment'
            echo 'Rebuild the pipeline and choose - Yes, we should - to deploy the green deployment'
        }
        failure{
            echo ' The build has failed!'
        }
      }
}
