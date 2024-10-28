pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                mvn '-B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                mvn 'test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                cmd '/c ./jenkins/scripts/deliver.bat' 
            }
        }
    }
}
