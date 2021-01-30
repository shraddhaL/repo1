pipeline {
     agent any
	 tools {
        maven 'Maven' 
        
    }
	 environment {
        registryCredential ='docker'
    }
    stages { 	
	    stage('Clone repository') {
			   steps {	       
				   script{git 'https://github.com/shraddhaL/repo1.git'} }
        
			   }
	    
	 
        
        }
}
