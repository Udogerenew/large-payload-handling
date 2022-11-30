pipeline {
    agent any 
    environment {
        CRED_ID = 'afe961f5-1351-4b38-895d-293f0386bf31'
    }
    stages {
        stage('git-clone') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'afe961f5-1351-4b38-895d-293f0386bf31', url: 'https://github.com/Udogerenew/large-payload-handling.git']]])
            }
        }
        stage('generate AFT report') {
	    steps {	
		//System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "")
		publishHTML (target: [
		allowMissing: false,
		alwaysLinkToLastBuild: false,
		keepAll: true,
		reportDir: "${workspace}",
		reportFiles: "/var/lib/jenkins/workspace/test.html",
		reportName: "AFT report"])
		junit skipPublishingChecks: true
		junit skipPublishingChecks: true, testResults: '**/*.xml'
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
