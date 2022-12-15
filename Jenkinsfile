
pipeline{

   agent any

	//create dockerhub credential in github with your dockerhub Username and Password/Token
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
	
	stages {

		stage('gitclone') {

		      steps {
		         git 'https://github.com/theitern/Dec6Class.git+'
		      }
		}
		
		stage('Build') {
			steps {
			
			   sh 'docker build -t ifnobegod/class_app:${BUILD_NUMBER} .'
			}
		}
		
		stage('Login') {
		
			steps {
			   sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login --username ifnobegod --password-stdin'    
			}
		}

		stage('Push') {
			
			steps {
			   sh 'docker push ifnobegod/class_app:${BUILD_NUMBER}'
			}
		}
