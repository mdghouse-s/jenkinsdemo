pipeline {
	// agent any
	// aget docker image with maven
	agent {
		docker {
			image 'maven:3-alpine'
			args '-v /root/.m2:/root/.m2'
		}
	}
	stages {
		stage('Build') {
			steps {
				echo 'Building..'
				sh 'mvn --version'
			}
		}
		stage('Test') {
			steps {
				echo 'Testing..'
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying....'
			}
		}
	}
	post {
		always {
			echo 'This will always run'
		}
		success {
			echo 'This will run only if successful'
		}
		failure {
			echo 'This will run only if failed'
		}
		unstable {
			echo 'This will run only if the run was marked as unstable'
		}
		changed {
			echo 'This will run only if the state of the Pipeline has changed'
			echo 'For example, if the Pipeline was previously failing but is now successful'
		}
	}
}