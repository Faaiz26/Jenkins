pipeline {
    agent {
        docker {
            image 'python:3.9'
            
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies'){
            steps {
                sh '''
                export HOME=/tmp
                pip install -r requirements.txt 
                pip install  pytest
                '''
            }
        }

        stage('Run tests') {
            steps {

                sh '''
                export PATH=/tmp/.local/bin:$PATH
                pytest tests/'''
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage -containerized environment'
            }
        }

        stage('deploy') {
            steps {
                echo 'Deploy Stage -- commands here'
                
            }
        }
    }
}

post {
    sucess {
        echo 'Pipeline Sucess'
    }
    failure{
        echo 'Pipeline failed'
    }
}