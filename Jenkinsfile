pipeline {
    agent any
    environment {
        BRANCH_NAME = 'main'
    }
    stages {
        stage('Cloning Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: "*/${BRANCH_NAME}"]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GithubCredential', url: 'https://github.com/hoquanglai/nestjs-jenkins.git']]])
                echo "Clone git repository from branch: ${BRANCH_NAME}"
            }
        }
        stage('Start') {
        }
    }
}
