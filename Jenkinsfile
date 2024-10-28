pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                powershell 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                powershell 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                bat './jenkins/scripts/deliver.bat' 
            }
        }
    }
}
