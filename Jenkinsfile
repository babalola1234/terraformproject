pipeline {
 
  agent {
  node  { label 'terraform-node' }
 
  }
  environment {
        AWS_ACCESS_KEY_ID     = credentials('AKIATKKR4TVVROSZW5PF')
        AWS_SECRET_ACCESS_KEY = credentials('KnEx070rr+dzMnrDNelw5BFtixnhgcHnSEjGgwlc')
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
    
  stage( 'terraform action') {
     steps{
         echo "Terraform action is -->${action}"
	 sh ( 'terraform ${action} --auto-approve')
            
      }
   }
    
 }

}
