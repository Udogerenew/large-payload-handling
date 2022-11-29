pipeline {
    agent any 
    stages {
        stage('git-clone') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'afe961f5-1351-4b38-895d-293f0386bf31', url: 'https://github.com/Udogerenew/large-payload-handling.git']]])
            }
        }
        stage('Test') { 
            steps {
                sh 'docker --version'
                sh 'docker-compose -f docker-composetest.yml up -d'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo completed'
            }
        }
    }
}
