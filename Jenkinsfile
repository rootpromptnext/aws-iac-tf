pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-id')  // Jenkins credential ID
        AWS_SECRET_ACCESS_KEY = credentials('aws-id')  // Jenkins credential ID
        AWS_DEFAULT_REGION = 'us-east-1'  // Optional: Set your AWS region
    }
    stages {
        stage('Setup') {
            steps {
                echo "Initializing Terraform"
                sh 'terraform init'
            }
        }
        stage('Plan') {
            steps {
                echo "Generating Terraform plan"
                sh 'terraform plan'
            }
        }
        stage('Apply') {
            steps {
                echo "Applying Terraform plan"
                sh 'terraform destroy --auto-approve'
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
