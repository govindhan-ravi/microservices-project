pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EkS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8AF89C7EC2386D674C193CB44E1F63F0.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EkS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8AF89C7EC2386D674C193CB44E1F63F0.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
