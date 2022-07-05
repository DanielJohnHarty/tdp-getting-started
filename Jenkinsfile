pipeline {
    agent any
    stages {
        stage('test') {
            steps {

                sh "scripts/install-dependencies.sh"
                sh "scripts/setup.sh -r stable"
                sh "ansible-playbook generate-node-deployment-config.yml"
                sh "vagrant box add centos/7 --provider virtualbox || true"
                sh "vagrant up --provider virtualbox"
                sh "ansible-playbook deploy-all.yml"
            }
        }
    }
}