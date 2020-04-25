pipeline {
    agent any
    environment {
        reponame =  "musician-app"
        repourl = "https://github.com:nimishmehta8779/musician-app.git"
    }
    stages {
        stage ('checkout all branches') {
            steps{
            checkout ([
                $class: 'GitSCM',
                branches: [[name: 'origin/master']],
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
