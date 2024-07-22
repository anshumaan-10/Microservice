pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://EF316E690351D1DABE625111196F9D71.gr7.us-east-2.eks.amazonaws.com') {
                   sh "kubectl apply -f deployment-service.yml"
                   sleep 60
               }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://EF316E690351D1DABE625111196F9D71.gr7.us-east-2.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
