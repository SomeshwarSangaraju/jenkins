pipeline{
    agent{
        node{
            label 'agent-1'
        }
    }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages{
        stage('Deploy'){
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            steps{
                // script{
                //     sh """
                //         echo "deploying"
                //     """
                //  echo "Hello, ${PERSON}, nice to meet you."
                // }
            
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
            }
        }
        stage('Test'){
            steps{
                script{
                    sh """
                        echo "testing"
                    """
                }
            }
        }
        stage('Build'){
            steps{
                script{
                    sh """
                        echo "building"
                    """
                }
            }
        }
    }
    post{
        always{
            echo "i will always say hello again"
            cleanWs()
        }
        success{
            echo "sucess"
        }
        failure{
            echo "failed"
        }
    }
}