// Define variable
def URL = "https://github.com/Udogerenew/large-payload-handling.git"
def credentialsId = "afe961f5-1351-4b38-895d-293f0386bf31"
def branchname = "master"




pipeline {
    agent any 
    environment {
        BRANCH_NAME = 'master'
        CRED_ID = 'afe961f5-1351-4b38-895d-293f0386bf31'
        URL = "https://github.com/Udogerenew/large-payload-handling.git"
    }
    stages {
        stage('git-clone') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '${CRED_ID}', url: '${URL}']]])
            }
        }
        stage('Docker-compose') { 
            steps {
                sh 'docker --version'
                sh 'docker compose version'
                sh 'docker compose -f /var/lib/jenkins/workspace/test/docker-composetest.yaml up'
                sh 'docker ps -a'				
            }
        }
        stage('test') { 
            steps {
                sh 'echo completed'
            }
        }
    }
}
