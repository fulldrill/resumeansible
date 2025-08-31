pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/fulldrill/resumeansible.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t resumeans-app:latest ./app'
            }
        }

        stage('Run Ansible Playbook') {
           steps {
                bat '''
               wsl ansible-playbook /mnt/c/Users/PHRENCH/.jenkins/workspace/resumeansible/playbook.yml
             '''
            }
        }
}
}