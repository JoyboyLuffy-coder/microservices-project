pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Luffy-EKS', contextName: '', credentialsId: 'k8s-token', namespace: 'luffy-app', serverUrl: 'https://8C5055940A3E62079050CDCCDC6B45C2.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'Luffy-EKS', contextName: '', credentialsId: 'k8s-token', namespace: 'luffy-app', serverUrl: 'https://8C5055940A3E62079050CDCCDC6B45C2.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n luffy-app"
                }
            }
        }
    }
}
