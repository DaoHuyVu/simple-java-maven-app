pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'mvn.cmd -B -DskipTests clean package' 
            }
        }
				 stage('Test') {
            steps {
                bat 'mvn.cmd test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
				stage('Deliver') {
            steps {
                bat './jenkins/scripts/deliver.sh'
            }
        }
    }
}
