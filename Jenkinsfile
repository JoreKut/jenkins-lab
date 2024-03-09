pipeline {
    
    agent { docker { image 'python:3.12.1-alpine3.19' } }

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JoreKut/jenkins-lab']])
            }
        }
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/JoreKut/jenkins-lab'
	        sh 'python main.py'        
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'main.py', onlyIfSuccessful: true
            }
        }
    }
}
