pipeline {
    agent any 
	
   environment{
	   dockerhub=credentials("ee2cfeb8-89a3-4ec0-84da-1ad12fc784cd")
	}
		

    stages{
        
	    stage("Git login"){
  		steps {
      		git branch: 'main', url: 'https://github.com/kedar1704/Jenkins-Docker-Webserver-Project.git'

  }
	 }

	    stage("Build docker image"){
		    steps{
            		sh 'docker build -t $JOB_NAME:$BUILD_ID .'
		}
        }
	    stage("Push docker image to docker hub"){
		    steps{
			    sh 'docker tag $JOB_NAME:$BUILD_ID kedar1704/$JOB_NAME:latest'
			    sh 'docker push kedar1704/$JOB_NAME:latest'
		    }
	    }
    }
}
