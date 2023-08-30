pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], 
                userRemoteConfigs: [[url: 'https://github.com/Kaleakash/python_jenkins_with_docker.git']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/Kaleakash/python_jenkins_with_docker.git'
                sh 'python3 ops.py'
            }
        }
        stage('Test') {
            steps {
                 sh 'python3 -m pytest'
            }
        }
    }
}