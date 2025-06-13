pipeline {
    agent any
    
    tools {
        maven 'Maven 3.9.10'  // Nom exact dans Global Tool Configuration
        jdk 'JDK 17'          // Nom exact dans Global Tool Configuration
    }
    
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean compile test jacoco:report'
            }
        }
        
        stage('Test Results') {
            steps {
                publishTestResults testResultsPattern: '**/target/surefire-reports/*.xml'
                script {
                    if (fileExists('**/target/jacoco.exec')) {
                        publishCoverage adapters: [
                            jacocoAdapter('**/target/site/jacoco/jacoco.xml')
                        ], sourceFileResolver: sourceFiles('STORE_LAST_BUILD')
                    }
                }
            }
        }
    }
}