pipeline {
    agent any 
	
		

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
			    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
			    sh 'docker tag $JOB_NAME:$BUILD_ID kedar1704/$JOB_NAME:latest'
			    sh 'docker push kedar1704/$JOB_NAME:latest'
		    }
	    }
	    
	    stage("Push to webserver from ansibleserver"){
		  steps{
			ansiblePlaybook credentialsId: 'tomcat_newcred', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 'docker_pullrun.yaml'		  }
	    }
    }
}
