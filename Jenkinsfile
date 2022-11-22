pipeline {
    agent {
	label 'aws'
}
    stages {
       stage ('Installing Python, Ansible and boto3') {
          steps {
	      script{
              sh ' sudo yum install python3-pip -y'
              sh ' sudo pip3 install boto3 '
              sh ' sudo pip3 install ansible-core  '
		}
          }
       }
   }  
}
