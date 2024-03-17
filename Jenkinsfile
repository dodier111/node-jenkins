pipeline {
    agent {
        label 'dock' 
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/dodier111/node-jenkins.git']]])
            }
        }

        stage('Deploy') {
            steps {
                sh 'pwd'
                sh 'ls'
                sh '/home/ubuntu/.nvm/versions/node/v20.11.1/bin/pm2 start /home/ubuntu/workspace/nodeeeejs/node.js' 
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
