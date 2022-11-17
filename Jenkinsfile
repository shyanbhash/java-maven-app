pipeline {
	agent any 
	tools {
		maven "m1"
	}
	stages {
		stage('Build') {
			steps {
				sh 'mvn -DskipTests clean install'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
			post {
				always {
					junit '**/target/surefire-reports/*.xml'
				}
			}
		}
		stage('Deliver') {
			steps {
				'./scripts/deliver.sh'
			}
		}
	}

}
