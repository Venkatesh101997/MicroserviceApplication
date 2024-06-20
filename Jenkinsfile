pipeline {
    agent any
      
    stages { 
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKScluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9491A57A278FA7C05ECC864733156D01.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKScluster', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9491A57A278FA7C05ECC864733156D01.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
