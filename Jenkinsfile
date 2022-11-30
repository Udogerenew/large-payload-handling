pipeline {
    agent any 
    environment {
        CRED_ID = 'afe961f5-1351-4b38-895d-293f0386bf31'
    }
    stages {
        stage('git-clone') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '${CRED_ID}', url: 'https://github.com/Udogerenew/large-payload-handling.git']]])
            }
        }
        stage('Test') { 
            steps {
                sh 'docker --version'
                sh 'printenv'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo completed'
            }
        }
    }
}
