pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install || exit /b 0'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {

                    script {
                        def scannerHome = tool name: 'SonarScannerCLI', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                        def scannerBin = "${scannerHome}\\sonar-scanner-5.0.1.3006-windows\\bin\\sonar-scanner.bat"

                        bat """
                            "${scannerBin}" ^
                            -Dsonar.projectKey=pratham-amin_SIT753-Task-7.2CDevSecOps ^
                            -Dsonar.organization=pratham-amin ^
                            -Dsonar.sources=. ^
                            -Dsonar.host.url=https://cloud.sonarsource.com
                        """
                    }

                }
            }
        }
    }
}
