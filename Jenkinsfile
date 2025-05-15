pipeline {
    agent any

    parameters {
        string(name: 'EC2_PRIVATE_IP', defaultValue: '', description: 'Private IP of the EC2 instance')
    }

    stages {
        stage('Update Inventory') {
            steps {
                script {
                    writeFile file: 'inventory.ini', text: """[web]
${params.EC2_PRIVATE_IP} ansible_user=ec2-user ansible_ssh_common_args='-o StrictHostKeyChecking=no'"""
                }
            }
        }

        stage('Deploy Flask App with Ansible') {
            steps {
                sshagent(['ec2-prod-key']) {
                    sh 'ansible-playbook -i inventory.ini deploy.yml'
                }
            }
        }
    }
}

