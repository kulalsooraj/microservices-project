pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://357898865A3A0E6B1BB76EC1E7CB4A26.yl4.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-raham12', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://357898865A3A0E6B1BB76EC1E7CB4A26.yl4.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
