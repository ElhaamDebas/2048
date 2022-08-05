pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('goraghad')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t goraghad/2048:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push goraghad/2048:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}