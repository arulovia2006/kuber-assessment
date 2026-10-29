
pipeline {
    agent any

    stages {
        stage('Check Workspace') {
            steps {
                bat 'cd'
                bat 'dir'
                bat 'dir k8s'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl rollout status deployment/sample-web --timeout=120s'
                bat 'kubectl get pods -l app=sample-web'
            }
        }
    }
}
