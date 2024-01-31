pipeline {
    agent {
  label 'ansible'
    }
    options {
        skipDefaultCheckout()
    }
    stages {
        stage('Checkout repository') {
            steps {
                dir('lighthouse-role') {
                    checkout scm
                }
            }
        }
        stage('Install molecule') {
            steps {
                sh 'pip3 install molecule==3.4.0 molecule-docker'
                sh 'pip3 install ansible-lint==5.1.3'
                sh 'pip3 install --upgrade requests'
            }
        }
        stage('Test role') {
            steps {
                dir('lighthouse-role') {
                    sh 'molecule test'
                }
            }
        }
    }
}
