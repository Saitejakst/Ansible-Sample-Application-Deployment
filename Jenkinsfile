pipeline {
    agent any
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/saitejakst/Ansible-Sample-Application-Deployment.git'
             
          }
        }
        
        
        
          stage('Ansible Init') {
            steps {
                script {
                
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }
        
        
        
        stage('Ansible Deploy') {
             
            steps {
                 
             
               
               sh "sudo ansible-playbook main.yml -i inventories/dev/hosts --user cloud_user --key-file /home/cloud_user/ansible_aut.pem -e '@configs/dev.yml' --ask-become-pass"

               
            
            }
        }
    }
}
