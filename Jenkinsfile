pipeline {
    agent any

    environment {
        KUBE_CONFIG = credentials('kubeconfig')  // Use Jenkins credentials for kubeconfig
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo DEBIAN_FRONTEND=noninteractive apt-get install -y npm'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t my-node-app:1.0 .'
            }
        }    
    }
}
