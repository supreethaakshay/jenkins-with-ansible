pipeline {
  agent { 
  label 'ansiblenode'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
        git credentialsId: '18717454-299b-45e2-9661-25fdd6635924', url: 'https://github.com/supreethaakshay/jenkins-with-ansible.git
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/icicibank.hosts --private-key=$AWSEC2_PRIVATEKEY playbooks/installTomcat.yml --ssh-common-args='-oStrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
