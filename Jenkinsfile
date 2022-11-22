pipeline {
    agent {
	label 'aws'
    }
    stages {
       stage ('Installing Python, Ansible, pymssql and boto3') {
          steps {
	      script{
              sh ' sudo yum install python3-pip -y'
              sh ' sudo pip3 install boto3 '
              sh ' sudo pip3 install ansible-core  '
              sh ' sudo pip3 install pymssql '
               	    }
                 }
          }
      stage ('Installing Required Ansible modules') {
          steps {
              script{
              sh ' ansible-galaxy collection install community.aws'
              sh ' ansible-galaxy collection install community.general'
                    }
                 }
           }
      stage ('Running Ansible playbook to install RDS SQl on AWS') {
          steps {
              script{
              sh ' ansible-playbook main.yml ' 
                    }
                 }
           }
   }  
}
