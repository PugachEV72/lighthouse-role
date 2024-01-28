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
        stage('Get role') {
            steps {
                dir('lighthouse-role') {
                    git branch: 'master', credentialsId: 'ac3dd0c9-9321-427a-8c76-8bf862119ead', url: 'https://github.com/PugachEV72/lighthouse-role.git'
                }
            }
        }
        stage('Install molecule') {
            steps {
                sh 'pip3 install molecule==3.4.0 molecule-docker'
                sh 'pip3 install ansible-lint==5.1.3'
                sh 'pip3 install --upgrade requests'
                sh 'export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/usr/local/bin/'
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
