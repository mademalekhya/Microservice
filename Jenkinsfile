pipeline {                                      
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://D43A4D84493A96E6AB33E9044468E070.gr7.ap-south-1.eks.amazonaws.com']]) {
    
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://D43A4D84493A96E6AB33E9044468E070.gr7.ap-south-1.eks.amazonaws.com']]) {
    
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
