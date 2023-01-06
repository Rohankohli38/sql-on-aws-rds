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
		      sh ' ansible-playbook main.yml --vault-password-file secret.txt --extra-vars "{"subnets_list": "$subnets_list", "kms_key_id": "$kms_key_id", "db_engine": "$db_engine", "db_engine_version": "$db_engine_version", "engine_name": "$engine_name", "major_engine_version": "$major_engine_version", "para_engine": "$para_engine", "instance_class": "$instance_class", "instance_identifier": "$instance_identifier", "master_username": "$master_username", "port": "$port", "region": "$region", "vpc_security_group_id": "$vpc_security_group_id", "multi_az": "$multi_az", "read_replica": "$read_replica"}"'
                }
              }
          }
   }  
}
