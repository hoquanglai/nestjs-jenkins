pipeline {
    agent any
    environment {
        BRANCH_NAME = 'main'
    }
    stages {
        // stage('Prepare Environment') {
        //     steps {
        //         sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash'
        //         sh 'export NVM_DIR="$HOME/.nvm"'
        //         sh '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"'
        //         sh 'nvm install 20.11.1'
        //         sh 'nvm use 20.11.1'
        //     }
        // }
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
