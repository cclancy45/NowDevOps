   pipeline {
    agent any
    stages {
        stage('Build') {
            steps { 
                build 'BuildNowApp'
            }
        }
        stage('Test') {
            steps { 
                build 'TestNowApp'
            }
        }
        stage('Deploy') {
            agent {label 'Production'}
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
                            "work_notes": "Test work notes - CC",
                            "start_date": "2022-10-04 13:34:00",
                            "end_date": "2022-10-05 13:35:00"
                    }
                }""")
                build 'BuildNowApp-Prod'
            }
    }   
  } 
}