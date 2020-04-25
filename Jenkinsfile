pipeline {
    agent any
    environment {
        reponame =  "musician-app"
        repourl = "git@github.com:nimishmehta8779/musician-app.git"
        varsion = "1.0"
    }
    stages {
        stage ('creata a directory') {
            steps {
                script {
                    sh "if [ -d ./musician-app ]; then rm -rf musician-app; else mkdir musician-app; fi"
                }
            }
        }
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
                     cd musician-app
                     tar --exclude=.git -cvf ../musician-app${version}.tar . 
                     cd ..
                     ls -l *.tar                    
                    '''
                }
            }
        }
    }
}

