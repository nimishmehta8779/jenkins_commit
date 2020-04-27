@Library("nimishmehta8779/sharedLibrary") _
pipeline{
    agent any
    stages{
        stage("A"){
            steps{
                script {
                    log.info 'Starting'
                    log.warning 'Nothing to do here'
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
}
