pipeline {
    agent any
    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' E-commerce', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D9ACBF09A5F587EB7D22A6DFE34536E1.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'E-commerce', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D9ACBF09A5F587EB7D22A6DFE34536E1.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
