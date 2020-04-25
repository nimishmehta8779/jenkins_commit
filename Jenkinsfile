pipeline {
    agent any
    environment {
        reponame =  "musician-app"
        repourl = "git@github.com:nimishmehta8779/musician-app.git"
    }
    stages {
        stage ('checkout all branches'){
            when {
                branch 'master'
            }
            steps{
            checkout([
                $class: 'GitSCM',
                branches: [[name: commit]],
                doGenerateSubModuleConfigurations: false,
                extensions: [
                    [$class: 'RelativeTargetDirectory', relativeTargetDir: reponame]
                ],
                submoduleCfg: [],
                useRemoteConfigs: [
                [credentialsId: 'nimishmehta8779', url: repourl]
            ]
            ])
                dir (reponame) {
                sh (script: "git rev-parse HEAD")
            }
        }
    }
}
}
