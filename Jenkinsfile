pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], extensions: [], 
                userRemoteConfigs: [[url: 'https://github.com/Kaleakash/python_jenkins_file.git']]])
            }
        }
        stage("Installation"){
            steps{
                sh 'exec -it -u 0 f5787dfbdfa2 /bin/bash'
                sh 'apt-get update'
                sh 'apt-get install python3'
                sh 'apt-get install python3-pip'    
            }
        }
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/Kaleakash/python_jenkins_file.git'
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