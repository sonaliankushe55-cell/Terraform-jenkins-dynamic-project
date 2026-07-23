pipeline {

    agent {
        label 'terraform-agent'
    }

    stages {

        stage('Terraform Init') {
            steps {
                dir('terraform') {
                    sh 'pwd'
                    sh 'ls -la'
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Validate') {
            steps {
                dir('terraform') {
                    sh 'terraform validate'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                dir('terraform') {
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                input message: 'Do you want to apply the Terraform changes?'
                dir('terraform') {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
