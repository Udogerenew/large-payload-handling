pipeline {
    agent any 
    #agent {label 'node1'}
    stages {
        stage('git-clone') { 
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/${env.branchname}']], extensions: [], userRemoteConfigs: [[credentialsId: '${env.credentialsId}', url: '${env.URL}']]])
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
	    stage('generate AFT report') {
				//System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "")
				publishHTML (target: [
				allowMissing: false,
				alwaysLinkToLastBuild: false,
				keepAll: true,
				reportDir: "${workspace}",
				reportFiles: "${report_append}_${pod_number}.Maestro_AFT_report.html",
				reportName: "${pod_number} AFT report"])
				junit '**/*.xml'
        }								
        }
    }
}
