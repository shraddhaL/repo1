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
				 git 'https://github.com/shraddhaL/jenkinsdocker-local.git' }
        
			   }
	    
	 
        
        }
}
