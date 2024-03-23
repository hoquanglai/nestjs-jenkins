pipeline {
    agent any
    environment {
        BRANCH_NAME = 'main'
    }
    agent {
        docker { image 'node:20.11.1-alpine3.19' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
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
