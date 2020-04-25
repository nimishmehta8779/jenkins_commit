pipeline {
    agent any
    environment {
        reponame =  "oracle-install-scripts"
        repourl = "git@github.com/nimishmehta8779/oracle-install-scripts.git"
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
                    [$class: 'RelativeTargetDirectory', relativeTargetDir: reponame],
                    [$class: 'CloneOption', reference: "/opt/${reponame}"]
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
        stage ('validate ') {
            steps{
                sh (script: "completed")
            }
        }
    }
}
}
