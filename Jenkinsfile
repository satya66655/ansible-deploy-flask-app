pipeline {
    agent any

    stages {
        stage('Deploy Flask App with Ansible') {
            steps {
                sh '''
                ansible-playbook -i inventory.ini deploy.yml
                '''
            }
        }
    }
}

