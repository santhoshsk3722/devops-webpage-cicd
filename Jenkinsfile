pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                checkout scm
            }
        }
        stage('Build Docker Image'){
            steps{
                bat 'docker build -t my-webpage:%BUILD_NUMBER% .'
            }
        }
        stage('test'){
            steps{
                bat 'docker run -d -p 8082:80 --name webpage-test my-webpage:%BUILD_NUMBER%'
                bat 'curl http://localhost:8082'
                bat 'docker rm -f webpage-test'
            }
        }
        stage('deploy'){
            steps{
                bat 'minikube kubectl -- apply -f k8s/ --validate=false'
            }
        }
    }

}
