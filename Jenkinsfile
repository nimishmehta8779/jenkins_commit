pipeline {
    agent any
    parameters {
        choice(choices: "$environment", description: '', name: 'ENVIRONMENT')
        string(defaultValue: "nimish.mehta@gmail.com",
                description: 'Nimish',
                name: 'Nimish Mehta')
    }
    environment {
        reponame =  "musician-app"
        repourl = "https://github.com:nimishmehta8779/musician-app.git"
    }
    stages {
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
                dir (reponame) {
                sh (script: "git rev-parse HEAD")
            }
        }
    }
}
}
