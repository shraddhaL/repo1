pipeline {
     agent any
	 
	 environment {
        registryCredential ='docker'
    }
    stages { 	
	    stage('Clone repository') {
			   steps {	       
				git branch: 'main', url:'https://github.com/ShivaniJ-hub/MusicStoreDemo.git'//  git 'https://github.com/shraddhaL/jenkinsdocker-local.git' }
			   }
			   }
	    
	  stage('Build Jar') {
	    
		steps {
		        sh 'mvn clean package'
        }
        }
	   
	    
	  stage('Build Image') {
            steps {
                script {
                	app = docker.build("shivani221/mytomcatimage")
                }
            }
        }
	    
	       stage('Docker Push') {
            steps {
		    script{
			    docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
			    dockerImage.push("${BUILD_NUMBER}")
			    dockerImage.push("latest")
			    }
          }
        }
      }
      
      stage('Docker Tomcat server') {
              steps {
               		sh 'docker stop mytomcatimage'
			sh 'docker rm mytomcatimage'
			sh 'docker run -d --name mytomcatimage -p 9090:8080 shivani221/mytomcatimage:latest'
            }
        }
	 
	 stage('archive') {
              steps {
               		archiveArtifacts  'target/*.war'
            }
        } 
        
        
         stage('Docker Cleanup') {
              steps {
 		          		         sh 'docker system prune --all --volumes --force'
            }
        }
        
        }
}
