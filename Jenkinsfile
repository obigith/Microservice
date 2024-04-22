pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-microcluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D6921E068A6AB4D35CC47C3B649DE0F2.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }




        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-microcluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D6921E068A6AB4D35CC47C3B649DE0F2.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
