pipeline {
    agent {
	label 'aws'
}
    stages {
       stage ('Building Docker image form docker file') {
          steps {
	      script{
              sh 'echo Hello'
		}
          }
       }
       stage ('Listing docker image') {
          steps {
              sh ' echo hello '
          }
       }
       stage ('Building docker container using docker image') {
          steps {
              sh 'echo hello'
          }
       }
   }  
}
