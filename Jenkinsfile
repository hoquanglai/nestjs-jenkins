pipeline {
    agent {
        docker { 
            image 'node:20.11.1-alpine3.19' 
            // Add any docker args if needed. Example: args '-p 3000:3000'
        }
    }
    environment {
        BRANCH_NAME = 'main'
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
                sh 'npm --version'
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
                // If npm start is supposed to run the app, consider using it in a post-build step or adjust as necessary for your CI process
                sh 'npm start'
            }
        }
    }
}
