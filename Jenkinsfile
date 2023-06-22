pipeline {
	agent any
	// agent docker image with maven 3.6.3 and java 11
	// agent {
	// 	docker {
	// 		image 'maven:3.6.3-openjdk-11'
	// 		args '-v /root/.m2:/root/.m2'
	// 	}
	// }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH="$PATH:$dockerHome/bin:$mavenHome/bin"
	}

	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker --version'
				echo 'Building..'
				echo "$PATH"
				echo "$JAVA_HOME"
				echo "$env.JOB_NAME"
				echo "$env.BUILD_NUMBER"
				
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test'
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