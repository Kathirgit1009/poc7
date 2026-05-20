pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Kathirgit1009/poc7.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t poc7-app:latest .'
            }
        }

        stage('Continuous Delivery via Ansible') {
            steps {
                sh 'ansible-playbook -i ansible/inventory ansible/deploy.yml'
            }
        }

    }

    post {
        success {
            echo '✅ POC-7 Deployed Successfully via Ansible!'
        }
        failure {
            echo '❌ Deployment Failed. Check Console Output.'
        }
    }
}
