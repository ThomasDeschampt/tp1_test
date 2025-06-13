pipeline {
    agent any
    tools {
        maven 'Maven 3.9.10'
        jdk 'JDK 17'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean test jacoco:report'
            }
        }
        stage('Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }
}
