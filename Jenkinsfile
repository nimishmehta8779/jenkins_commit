pipeline {
    agent any
    environment {
        reponame =  "oracle-install-scripts"
        repourl = "https://github.com:nimishmehta8779/oracle-install-scripts.git"
    }
    stages {
        stage ('checkout all branches') {
            steps{
            checkout scm:([
                $class: 'GitSCM',
                branches: [[name: 'origin/master']],
                doGenerateSubmoduleConfigurations: false,
                extensions: [
                    [$class: 'RelativeTargetDirectory', relativeTargetDir: reponame]
                ],
                submoduleCfg: [],
                userRemoteConfigs: [
                [credentialsId: 'git', url: repourl]
            ]
            ])
        }
        }
        stage ('create a tar file') {
            steps {
                script{
                    sh '''
                     #!/bin/bash
                     cd musician-app
                     echo $pwd
                    '''
                }
            }
        }
    }
}

