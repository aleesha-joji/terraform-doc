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
            }
        }
        stage('Get') {
            steps {
                sh 'terraform get'
            }
        }
        stage('Plan') {
            steps {
                sh 'terraform plan'
            }
        }
    }
}
