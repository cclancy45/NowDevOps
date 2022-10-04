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
              snDevOpsChange(changeRequestDetails: """
                {
                    "setCloseCode": false,
                        "attributes": {
                            "requested_by": {
                                "name": "Abel Tuter"
                            },
                            "category": "DevOps",
                            "priority": "2",
                            "comments": "This is a sample pipeline script to be added in your change step",
                            "work_notes": "Update this to work_notes",
                            "start_date": "2022-10-05 11:59:59",
                            "end_date": "2022-10-05 11:59:59"
                    }
                }""")
            }
    }   
  } 
}
