pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('sonarcloud-token')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/pratham-amin/SIT753-Task-7.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                bat """
                    sonar-scanner ^
                    -Dsonar.projectKey=pratham-amin_SIT753-Task-7.2CDevSecOps ^
                    -Dsonar.organization=pratham-amin ^
                    -Dsonar.sources=. ^
                    -Dsonar.host.url=https://sonarcloud.io ^
                    -Dsonar.login=%SONAR_TOKEN%
                """
            }
        }
    }

    post {
        success {
            echo 'SonarCloud analysis completed successfully!'
        }
    }
}
