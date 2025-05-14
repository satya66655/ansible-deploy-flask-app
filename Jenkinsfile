pipeline {
    agent any

    stages {
        stage('Deploy Flask App with Ansible') {
            steps {
                sshagent(['ec2-prod-key']) {
                    sh 'ansible-playbook -i inventory.ini deploy.yml'
                }
            }
        }
    }
}

