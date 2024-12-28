pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-MyCluster1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://A6B1F83BCB39C5481B4DA68833CF131C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-MyCluster1', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://A6B1F83BCB39C5481B4DA68833CF131C.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
