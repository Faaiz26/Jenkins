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
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                pip install pytest
                '''
            }
        }

        stage('Run tests') {
            steps {

                sh '''
                . venv/bin/activate
                pytest tests/
                '''
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