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
	    
	    stage("Push to webserver"){
		  steps{
			  //sh 'ssh  -o "StrictHostKeyChecking=no" -i "/opt/ec2_oregon.pem" ec2-user@54.200.53.119 sudo yum install tree -y'
			  sh 'ssh  -o "StrictHostKeyChecking=no"  -i "/opt/ec2_oregon.pem" ec2-user@54.200.53.119 echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
			  sh 'ssh  -o "StrictHostKeyChecking=no" -i  "/opt/ec2_oregon.pem" ec2-user@54.200.53.119 sudo docker pull kedar1704/pipeline_deploytowebserver:latest'
			  sh 'ssh  -o "StrictHostKeyChecking=no" -i  "/opt/ec2_oregon.pem" ec2-user@54.200.53.119 sudo docker run -d -p 8090:80 kedar1704/pipeline_deploytowebserver:latest'
		  }
	    }
    }
}
