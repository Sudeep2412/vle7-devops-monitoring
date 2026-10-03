pipeline {
    agent any

    environment {
        MINIKUBE_HOME = '/var/lib/jenkins/.minikube'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh '''
                    eval $(minikube docker-env)
                    docker build -t myapp:latest .
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl rollout status deployment/myapp'
            }
        }
    }
}
