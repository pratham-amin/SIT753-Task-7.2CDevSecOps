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
                        bat """
                            "${scannerHome}\\bin\\sonar-scanner.bat" ^
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
