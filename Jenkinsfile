
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'}}
	environment {
		dockerHome= tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
         stage  ('Checkout'){
			steps {
		   		sh 'mvn --version'
		   		echo "Test"
		   		echo "$PATH"
				echo "BUILD_NUMBER $env.BUILD_NUMBER"
			}	
		 }
		 stage  ('Compile'){
			steps {
		   		sh 'mvn clean compile'
		   		
			}	
		 }
		 stage  ('Test'){
			steps {
		   		echo 'mvn test'
		   		
			}	
		 }		 
		 stage  ('Package'){
			steps {
		   		sh 'mvn package -DskipTests'
		   		
			}	
		 }
		 stage('Build Docker Image'){
				steps {
					scripts {
						dockerImage = docker.build("in28min/currency-exchange-devops:${env.BUILD_TAG}")
					}
				}
		 }
		 stage('Push Docker Image'){
			steps {
					scripts {
						docker.withRegistry('','dockerhub') {}
							dockerImage.push();
							dockerImage.push('latest');
						}
					}
				}
		 }
	}
	post {
		always {
			echo 'I m awesome!'
		}
	}	
}
