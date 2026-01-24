 pipeline { 
     agent any
     environment {
         // Set JAVA_HOME to the path of your Java 17 installation
         JAVA_HOME = 'C:/Program Files/Java/jdk-21.0.10' 
         // Add Java bin directory to PATH
         PATH = "${JAVA_HOME}//bin;${env.PATH}"
         }  
    tools { 
        maven 'M3' 
        
    } 
    stages { 
        stage('Maven version') { 
            steps {
                bat 'java -version' 
                bat 'mvn --version' 
            } 
        }
        stage('GetCode') {
            steps { 
                git branch: 'main', url: 'https://github.com/Maitri0503/java-jenkins-pipeline.git'
            }
        } 
        stage('Build') { 
            steps {
                bat 'mvn clean package'
                }
            } 
            stage('SonarQube analysis') {
                steps { 
                    withSonarQubeEnv('SonarQube') {
                        bat 'mvn sonar:sonar' 
                    } 
                }
            } 
    }
}   
