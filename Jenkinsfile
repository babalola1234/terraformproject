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
   stage('terraform init') {
     steps{
         sh 'terraform init '
      }
  }
   stage('Terraform Action') {
    steps {
        echo "Terraform action is --> ${action}"
        script {
            // Only apply --auto-approve if the action is NOT 'plan'
            def flags = (action == 'plan') ? "" : "--auto-approve"
            sh "terraform ${action} ${flags}"
        }
    }
}

 }
}
