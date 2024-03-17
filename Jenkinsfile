pipeline {
    agent any // This will allow Jenkins to execute the pipeline on any available agent

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/dodier111/node-jenkins.git']]])
            }
        }

        stage('Deploy') {
            steps {
                sh 'pwd'
                sh 'ls'
                sh "echo 'admin' | sudo -S -u ubuntu /usr/local/bin/pm2 start /var/lib/jenkins/workspace/pro/node.js"
 
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
