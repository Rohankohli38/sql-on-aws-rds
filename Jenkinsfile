pipeline {
    agent {
	label 'aws'
    }
    stages {
       stage ('Installing Python, Ansible, pymssql and boto3') {
          steps {
	      script{
		sh 'sudo apt update'
           //   sh ' sudo yum install python3-pip -y'
           //   sh ' sudo pip3 install boto3 '
           //   sh ' sudo pip3 install ansible-core  '
           //   sh ' sudo pip3 install pymssql '
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
		      sh ' ansible-playbook main.yml --vault-password-file secret.txt --extra-vars " kms_key_id=$kms_key_id {"subnets_list": [$subnets_1,$subnets_2,$subnets_3]}"'
		}
              }
          }
   }  
}
