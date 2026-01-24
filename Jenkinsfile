pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:/Program Files/Java/jdk-21.0.10'
        PATH = "${JAVA_HOME}/bin;${env.PATH}"
    }

    tools {
        maven 'M3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Maitri0503/java-jenkins-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat '''
                    mvn sonar:sonar ^
                    -Dsonar.projectKey=java-jenkins-demo ^
                    -Dsonar.projectName=java-jenkins-demo
                    '''
                }
            }
        }
    }
}
