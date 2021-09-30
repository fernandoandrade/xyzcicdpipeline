pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/fernandoandrade/xyzcicdpipeline.git'
            }
        }
        stage('package') {
            steps {
                sh 'mvn package'
                echo 'Packaged created.'                
            }
            
        }
        stage('deploy') {
            steps {
                sh "sudo ansible-playbook main.yml -i inventories/dev/hosts --user jenkins --key-file ~/.ssh/xyz.pem -e '@configs/dev.yml'"
                echo 'Deploy completed'             
            }
        }
    }
}
