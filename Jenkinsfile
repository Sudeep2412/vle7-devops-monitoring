pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'minikube image build -t myapp:latest .'
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
