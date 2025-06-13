pipeline {
    agent any
    
    tools {
        maven 'Maven 3.9.10'  // Nom exact dans Global Tool Configuration
        jdk 'JDK 17'          // Nom exact dans Global Tool Configuration
    }
    
    stages {
        stage('Build and Test') {
            steps {
                bat 'mvn clean compile test jacoco:report'
            }
        }
    }
}