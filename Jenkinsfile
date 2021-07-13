pipeline {
    agent {label 'agent' }
    tools { terraform 'terraform' }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }  
    stages {
        stage('Terraform initialization') {
            steps {
                sh 'cat /etc/os-release'
                sh 'terraform init'
                sh 'tarraform get'
                sh 'terraform plan'
            }
        }
        stage('Apply') {
            steps {
                sh "terraform apply --auto-approve"
            }
        }
    }
}
