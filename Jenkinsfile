pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = "us-east-1"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Ruchitha7529/jenkins-terraform'
            }
        }

        stage('Terraform Init') {
            steps {
                sh '''
                  terraform --version
                  terraform init
                '''
            }
        }

        stage('Terraform Plan') {
            steps {
                sh '''
                  terraform plan -input=false
                '''
            }
        }

        stage('Terraform Apply') {
            steps {
                sh '''
                  terraform apply -auto-approve -input=false
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Terraform pipeline executed successfully!'
        }
        failure {
            echo '❌ Terraform pipeline failed. Check logs above.'
        }
    }
}
