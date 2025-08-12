pipeline {
    agent {
        docker {
            image 'python:3.9'
            
        }
    }

    stages {
        stage('Checkout') {
            steps {
                Checkout scm
            }
        }

        stage('Install dependencies'){
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest tests/'
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