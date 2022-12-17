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
              withCredentials([file(credentialsId: 'vault-password', variable: 'vault-password')]) {
 		sh ' ansible-playbook db-vault.vault --vault-password-file ${vault-password} main.yml --extra-vars "subnets_1=$subnets_1 subnets_2=$subnets_2 db_engine=$db_engine db_engine_version=$db_engine_version"' 
		}
              }
          }
       }
   }  
}
