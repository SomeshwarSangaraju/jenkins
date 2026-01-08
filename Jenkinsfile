pipeline{
    agent{
        node{
            label 'agent-1'
        }
    }
     environment {
        COURSE = "Jenkins"
    }
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'Deploy', defaultValue: false, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages{
        stage('Build'){
            steps{
                script{
                    sh """
                        echo "Building"
                        echo $COURSE
                        sleep 10
                        env
                        
                        echo "Hello ${params.PERSON}"
                        echo "Biography: ${params.BIOGRAPHY}"
                        echo "Toggle: ${params.TOGGLE}"
                        echo "Choice: ${params.CHOICE}"
                        echo "Password: ${params.PASSWORD}"
                    """
                //  echo "Hello, ${PERSON}, nice to meet you."
                }
            
                
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
        stage('Deploy'){
            when{
                expression ("$params.Deploy" = "true")
            }
            steps{
                script{
                    sh """
                        echo "Deploying"
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