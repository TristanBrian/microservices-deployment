pipeline {
    agent any
    environment{
        SCANNER_HOME= tool 'sonar-scanner'
    }
    stages {
        stage('git checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/SushantOps/10-Tier-MicroService-Appliction.git'
            }
        }
        stage('SonarQube') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.ProjectName=10-Tier -Dsonar.java.binaries=. '''   
                }
                    
            }
                
        }
        stage('adservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/adservice') {
                            sh 'docker build -t sushantkapare1717/adservice:latest .'
                            sh "docker push sushantkapare1717/adservice:latest"
                            sh "docker rmi sushantkapare1717/adservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('cartservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                            sh 'docker build -t sushantkapare1717/cartservice:latest .'
                            sh "docker push sushantkapare1717/cartservice:latest"
                            sh "docker rmi sushantkapare1717/cartservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('checkoutservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice/') {
                            sh 'docker build -t sushantkapare1717/checkoutservice:latest .'
                            sh "docker push sushantkapare1717/checkoutservice:latest"
                            sh "docker rmi sushantkapare1717/checkoutservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('currencyservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice/') {
                            sh 'docker build -t sushantkapare1717/currencyservice:latest .'
                            sh "docker push sushantkapare1717/currencyservice:latest"
                            sh "docker rmi sushantkapare1717/currencyservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('emailservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice/') {
                            sh 'docker build -t sushantkapare1717/emailservice:latest .'
                            sh "docker push sushantkapare1717/emailservice:latest"
                            sh "docker rmi sushantkapare1717/emailservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('frontend'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/frontend/') {
                            sh 'docker build -t sushantkapare1717/frontend:latest .'
                            sh "docker push sushantkapare1717/frontend:latest"
                            sh "docker rmi sushantkapare1717/frontend:latest"
                        }
                    }
            }
            }
        }
    
        stage('loadgenerator'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator/') {
                            sh 'docker build -t sushantkapare1717/loadgenerator:latest .'
                            sh "docker push sushantkapare1717/loadgenerator:latest"
                            sh "docker rmi sushantkapare1717/loadgenerator:latest"
                        }
                    }
            }
            }
        }
    
        stage('paymentservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice/') {
                            sh 'docker build -t sushantkapare1717/paymentservice:latest .'
                            sh "docker push sushantkapare1717/paymentservice:latest"
                            sh "docker rmi sushantkapare1717/paymentservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('productcatalogservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice/') {
                            sh 'docker build -t sushantkapare1717/productcatalogservice:latest .'
                            sh "docker push sushantkapare1717/productcatalogservice:latest"
                            sh "docker rmi sushantkapare1717/productcatalogservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('recommendationservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice/') {
                            sh 'docker build -t sushantkapare1717/recommendationservice:latest .'
                            sh "docker push sushantkapare1717/recommendationservice:latest"
                            sh "docker rmi sushantkapare1717/recommendationservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('shippingservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice/') {
                            sh 'docker build -t sushantkapare1717/shippingservice:latest .'
                            sh "docker push sushantkapare1717/shippingservice:latest"
                            sh "docker rmi sushantkapare1717/shippingservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('K8-Deploy'){
            steps{
                withKubeConfig(caCertificate: '', clusterName: 'my-eks2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://EBCE08CF45C3AA5A574E126370E5D4FC.gr7.ap-south-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
}
}
