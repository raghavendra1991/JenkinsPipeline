pipeline {
  agent {
	    label 'slave'
  }
  stages { 
      stage('CleanUp WorkSpace & Git Checkout') {
          steps {
              // Clean before build
              cleanWs()
              // We need to explicitly checkout from SCM here
              checkout scm
          }
      }	  
      stage('Build & Test') {
         agent {
	          dockerfile {
      	       filename 'Dockerfile'
   	           reuseNode true
	          }	        
	       }
	       steps {
	           echo "Building Image and Conatiner"
	           sh 'python3 test.py'
	           sh 'python3 -m coverage xml -o test-reports/coverage.xml'
	       }
     }
  }
}
