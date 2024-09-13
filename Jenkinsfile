pipeline {
        agent any
       
parameters {
        string(name: 'environment', defaultValue: 'default', description: 'Workspace/environment file to use for deployment')
        
        
    }

    stages {
       stage('Terraform apply or destroy for EKS') {
            steps {
                sh 'aws eks update-kubeconfig --region eu-central-1 --name ${params.environment}-infra-eks-cluster'
                sh 'kubectl config set-context --current --namespace=kube-system'
                sh 'kubectl get nodes'
                sh 'kubectl create namespace'
                sh 'kubectl describe cm aws-auth -n kube-system >aws-auth.txt'
                sh 'cat aws-auth.txt'
                
                
            }
       }
    }
        
    }
