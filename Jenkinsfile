
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'}}
	environment {
		dockerHome= tool 'mydocker'
		mavenHome = tool 'mymaven'
		PATH = "$dockerHome/bin:$mavenHome/bin$PATH"
	}
	stages {
         stage  ('Build'){
			steps {
		   		sh 'mvn --version'
		   		echo "Test"
		   		echo "$PATH"
				echo "BUILD_NUMBER $env.BUILD_NUMBER"
			}	
		 }
	} 
	post {
		always {
			echo 'I m awesome!'
		}
	}	
}
