//@Library("nimishmehta8779/sharedLibrary") _
pipeline{
    agent any
    stages{
        stage("A"){
            steps{
                scripts {
                    echo 'Starting'
                    echo 'Nothing to do here'
                }
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}