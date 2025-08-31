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
                docker run --rm ^
                    -v %cd%:/workspace ^
                    -v //./pipe/docker_engine://./pipe/docker_engine ^
                    -w /workspace ^
                    cytopia/ansible:latest ^
                    sh -c "pip3 install requests docker && ansible-playbook -i inventory.ini playbook.yml"
                '''
            }
        }
    }
}
