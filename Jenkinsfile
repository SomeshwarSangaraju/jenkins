pipeline{
    agent{
        node{
            label 'agent-1'
        }
    }
    stages{
        stage('Deploy'){
            steps{
                script{
                    sh """
                        echo "deploying"
                    """
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