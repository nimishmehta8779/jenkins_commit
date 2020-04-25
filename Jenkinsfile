pipeline {
    agent any
    environment {
        reponame =  "musician-app"
        repourl = "https://github.com:nimishmehta8779/musician-app.git"
    }
    stages {
        stage ('This is a test') {
            sh 'echo $hostname'
        }
        stage ('checkout all branches'){
            steps{
            checkout scm:([
                $class: 'GitSCM',
                branches: [[name: master]],
                doGenerateSubModuleConfigurations: false,
                extensions: [
                    [$class: 'CleanCheckout'],
                    [$class: 'RelativeTargetDirectory', relativeTargetDir: reponame]
                ],
                submoduleCfg: [],
                useRemoteConfigs: [
                [credentialsId: 'git', url: repourl]
            ]
            ])
        }
    }
}
}
