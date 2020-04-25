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
                branches: [[name: '*/master']],
                doGenerateSubmoduleConfigurations: false,
                extensions: [
                     [$class: 'WipeWorkspace'],
                    [$class: 'CloneOption', timeout: 10, noTags: true, reference: reponame],
                    [$class: 'RelativeTargetDirectory', relativeTargetDir: reponame]
                ],
                submoduleCfg: [],
                userRemoteConfigs: [
                [credentialsId: 'git', url: repourl]
            ]
            ])
            dir(reponame) {
                sh(script: "git rev-parse HEAD")
            }
        }
        }
        stage ('create a tar file') {
            steps {
                script{
                    sh '''
                     #!/bin/bash
                     cd oracle-install-scripts
                     echo $pwd
                    '''
                }
            }
        }
    }
}

