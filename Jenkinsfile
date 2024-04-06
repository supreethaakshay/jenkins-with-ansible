pipeline{

    agent{
    label 'ansiblenode'
    }

    environment{
        AWSEC2_PRIVATEKEY=credentials('ec2-private-key')
    }

    stages{
        stage('CheckoutCode'){
            steps{
                git credentialsId: '18717454-299b-45e2-9661-25fdd6635924', url: 'https://github.com/supreethaakshay/jenkins-with-ansible.git'

            }
        }

        stage('RunAnsiblePlaybook'){
            steps{
                sh "ansible-playbook -i inventory/icicibank.hosts --private-key=$AWSEC2_PRIVATEKEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
                
            }
        }

    }
}
