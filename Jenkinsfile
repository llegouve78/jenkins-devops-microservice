
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
		   		sh 'mvn test'
		   		
			}	
		 }		 
		 stage  ('Integration Test'){
			steps {
		   		sh 'mvn failesafe:integration-test failsafe:verify'
		   		
			}	
		 }
	}
	post {
		always {
			echo 'I m awesome!'
		}
	}	
}
