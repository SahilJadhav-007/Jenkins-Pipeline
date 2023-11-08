# jenkins-pipeline-example


pipeline {
    agent any
    tools{
        maven 'MAVEN'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SahilJadhav-007/Jenkins-Pipeline.git']])
               
            }
        }
    }
    post{
        always{
            junit(
                allowEmptyResults:true,
                testResults:'*test-reports/.xml'
                )
        }
    }
}

USE This in pipeline syntax

u
