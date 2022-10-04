pipeline {
    agent any
    stages {
        stage('Build') {
            steps { 
                catchError(buildResult: 'SUCCESS') {
                sh 'docker stop samplerunning'
                sh 'docker rm samplerunning'
            }
                build 'BuildNowApp'
            }
        }
        stage('Test') {
            steps { 
                build 'TestNowApp'
            }
        }
        stage('Deploy') {
            steps { 
            snDevOpsChange()
            }
    }   
  } 
}
