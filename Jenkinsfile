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
                sh 'kubectl apply -f thapim-keycloak-deployment.yaml'
                sh 'kubectl apply -f thapim-mariadb-deployment.yaml'
            }
        }
    }
}
