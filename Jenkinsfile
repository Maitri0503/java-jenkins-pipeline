pipeline {
    agent any

    tools {
        sonarQube 'SonarScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'git-credentials',
                    url: 'https://github.com/username/repo.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh """
                    sonar-scanner \
                    -Dsonar.projectKey=my-project \
                    -Dsonar.projectName=my-project \
                    -Dsonar.sources=.
                    """
                }
            }
        }
    }
}
