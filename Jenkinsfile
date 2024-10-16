
//DECLARATIVE
pipeline {
	//agent 
	agent { docker { image 'maven:3.6.3'}}
	stages {
         stage  ('Build'){
			steps {
		   		sh 'mvn --version'
		   		echo "Test"
		   		echo "Test"
			}	
		 }
	} 
	post {
		always {
			echo 'I m awesome!'
		}
	}	
}
