pipeline {
   agent {
  node  { label 'terraform-node' }
   }
  environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
  }
stages {
    stage('Checkout code') {
      steps {
	  // Assuming your terraform file is in a SCM git 
        checkout scm
      }
    }
   stage('terraform format check') {
      steps {
           sh 'terraform fmt'
       }
   }
   stage( 'terraform init') {
     steps{
         sh 'terraform init '
      }
   }
   stage ("terraform Action") {
     steps {
         echo "Terraform action is --> ${action}"
     	 sh ('terraform ${action} --auto-approve')
       }
     }
   }
}
