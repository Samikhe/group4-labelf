pipeline {
    agent any
    stages {

        stage('Robot Framework System tests with Selenium') {
            steps {
                sh 'robot --variable BROWSER:headlesschrome -d AutoTests/Results AutoTests/Tests'
            }
            post {
                always {
                    script {
                          step(
                                [
                                  $class              : 'RobotPublisher',
                                  outputPath          : 'AutoTests/Results',
                                  outputFileName      : '/output.xml',
                                  reportFileName      : '/report.html',
                                  logFileName         : '/log.html',
                                  disableArchiveOutput: false,
                                  passThreshold       : 50,
                                  unstableThreshold   : 40,
                                  otherFiles          : "/.png,**/.jpg",
                                ]
                          )
                    }
                }
            }
        }
