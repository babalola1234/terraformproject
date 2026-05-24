pipeline {
    agent {
        node { label 'terraform-node' }
    }

    environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

    stages {
        stage('Checkout code') {
            steps {
                checkout scm
            }
        }

        stage('terraform format check') {
            steps {
                sh "terraform fmt"
            }
        }

        stage('terraform Init') {
            steps {
                sh "terraform init"
            }
        }

        stage("terraform Action") {
            steps {
                script {
                    echo "Terraform action is --> ${params.action}"

                    if (params.action == "plan") {
                        sh "terraform plan"
                    } else {
                        sh "terraform ${params.action} --auto-approve"
                    }
                }
            }
        }
    }
}
