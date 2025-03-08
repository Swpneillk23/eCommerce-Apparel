
pipeline {
    agent any // Runs the pipeline on any available agent

    stages {
        stage('Deploy To Kubernetes') { // Defines the first stage for deploying to Kubernetes
            steps {
                // Uses Kubernetes credentials to apply deployment configuration
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C1FBCDFB86CE243473C59C7EA48FD06D.gr7.us-east-1.eks.amazonaws.com']]) {
                }
                    
                    sh "kubectl apply -f deployment-service.yml"
                    
pipeline { 
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t adijaiswal/shippingservice:latest ."
                    }
 shippingservice
                }
            }
        }
    
        stage('verify Deployment') { // Defines the second stage for verifying the deployment
            steps {
                // Uses Kubernetes credentials to check the status of deployed services
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C1FBCDFB86CE243473C59C7EA48FD06D.gr7.us-east-1.eks.amazonaws.com']]) {
                    // Retrieves information about services deployed in the 'webapps' namespace
                    sh "kubectl get svc -n webapps"

        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push adijaiswal/shippingservice:latest "
                    }
 shippingservice
                }
            }
        }
    }
}
