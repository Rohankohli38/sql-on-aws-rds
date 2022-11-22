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
      stage ('Installing Python, Ansible, pymssql and boto3') {
          steps {
              script{
              sh '$ sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/8/prod.repo'
              sh 'sudo yum remove unixODBC-utf16 unixODBC-utf16-devel'
              sh 'sudo yum install -y mssql-tools unixODBC-devel'
              sh 'echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile'
              sh 'echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc source ~/.bashrc'
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
     stage ('Running Ansible playbook to create database on RDS SQL server') {
          steps {
              script{
              sh ' ansible-playbook main2.yml '
                    }
                 }
           }
   }  
}
