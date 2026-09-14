pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-webpage:%BUILD_NUMBER% .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run -d -p 8082:80 --name webpage-test my-webpage:%BUILD_NUMBER%'
                bat 'curl http://localhost:8082'
                bat 'docker rm -f webpage-test'
            }
        }

        stage('Load Image into Minikube') {
            steps {
                bat 'minikube image load my-webpage:%BUILD_NUMBER%'
            }
        }

        stage('Deploy') {
            environment {
                HOME = 'C:/ProgramData/Jenkins'
                MINIKUBE_HOME = 'C:/ProgramData/Jenkins'
            }

            steps {
                bat 'minikube kubectl -- apply -f k8s/ --validate=false'

                bat 'minikube kubectl -- set image deployment/my-webpage my-webpage=my-webpage:%BUILD_NUMBER%'

                bat 'minikube kubectl -- rollout status deployment/my-webpage'
            }
        }
    }
}