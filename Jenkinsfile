pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kubeconfig-jenkins') // Jenkins credential ID for kubeconfig
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-cred', url: 'https://github.com/Mythri532/Newapp.git', branch: 'main'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f secret-portalProperties.yaml'
                sh 'kubectl apply -f configMap-portalProperties.yaml'
                sh 'kubectl apply -f thapim-portal-deployment.yaml'
                sh 'kubectl apply -f thapim-portal-service.yaml'
            }
        }
    }
}
