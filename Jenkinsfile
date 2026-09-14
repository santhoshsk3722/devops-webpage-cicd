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
            environment {
                MINIKUBE_HOME = 'C:\\Users\\Hp'
            }

            steps {
                bat 'echo MINIKUBE_HOME=%MINIKUBE_HOME%'
                bat 'minikube profile list'
                bat 'minikube status'
                bat 'minikube image load my-webpage:%BUILD_NUMBER%'
            }
        }

        stage('Check Kubernetes') {
            environment {
                KUBECONFIG = 'C:\\ProgramData\\Jenkins\\.kube\\config'
            }

            steps {
                bat 'kubectl get nodes'
            }
        }

        stage('Deploy') {
            environment {
                KUBECONFIG = 'C:\\ProgramData\\Jenkins\\.kube\\config'
            }

            steps {
                bat 'kubectl apply -f k8s/ --validate=false'
                bat 'kubectl set image deployment/my-webpage my-webpage=my-webpage:%BUILD_NUMBER%'
                bat 'kubectl rollout status deployment/my-webpage'
            }
        }
    }
}