pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-nimmy1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://AD3BFA7CF12BD5A0AFC38B4BD4934E15.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-nimmy1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://AD3BFA7CF12BD5A0AFC38B4BD4934E15.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
