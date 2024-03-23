pipeline {
    agent any
    environment {
        BRANCH_NAME = 'main'
    }
    tools {
        nodejs 'MyNodeJS'
    }
    stages {
        stage('Cloning Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: "*/${BRANCH_NAME}"]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GithubCredential', url: 'https://github.com/hoquanglai/nestjs-jenkins.git']]])
                echo "Clone git repository from branch: ${BRANCH_NAME}"
            }
        }
        stage('Start') {
            steps {
                echo 'Installing dependencies and starting the application...'
                sh 'npm install'
                sh 'npm start'
            }
        }
    }
}
