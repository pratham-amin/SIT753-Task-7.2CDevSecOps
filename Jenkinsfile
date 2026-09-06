pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                // your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // your test steps here
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Task 7.2C DevSecOps Report - Build ${currentBuild.fullDisplayName}: ${currentBuild.currentResult}",
                body: """Hello Team,

This is the automated report for Task 7.2C DevSecOps.

Build Name: ${currentBuild.fullDisplayName}
Build Result: ${currentBuild.currentResult}

You can check the detailed console output here:
${env.BUILD_URL}console

Regards,
Jenkins Automated Pipeline
""",
                to: 'yourteam@example.com'
            )
        }
    }
}
