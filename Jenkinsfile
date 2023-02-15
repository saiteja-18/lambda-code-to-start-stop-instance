pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('d4a20c5a-12a4-4aca-87d3-a9bf3d85d4e5')
        AWS_SECRET_ACCESS_KEY = credentials('d4a20c5a-12a4-4aca-87d3-a9bf3d85d4e5')
        TF_WORKING_DIR = "\Code\Aws-lambda-function-to-start-stop-instance-when-tags-matched"
    }

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', credentialsId: 'e8da9276-cad8-490e-841b-1141af1e508f', url: 'https://github.com/saiteja-18/Aws-lambda-function-to-start-stop-instance-when-tags-matched.git'
            }
        }
        
        stage('Initialize Terraform') {
            steps {
                sh 'terraform init ${TF_WORKING_DIR}'
            }
        }
        
        stage('Validate Terraform') {
            steps {
                sh 'terraform validate ${TF_WORKING_DIR}'
            }
        }
        
        stage('Plan Terraform') {
            steps {
                sh 'terraform plan -out=myplan ${TF_WORKING_DIR}'
            }
        }
        
        stage('Apply Terraform') {
            steps {
                sh 'terraform apply myplan'
            }
        }
        

    }
}
