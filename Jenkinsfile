pipeline {
    agent any 

    stages{
        
	    steps("Git login")
            {
	            sh 'https://github.com/kedar1704/Jenkins-Docker-Webserver-Project.git'
            }

	    steps("Build docker image")
        {
            sh 'docker build -t $JOB_NAME:$BUILD_ID .'
            sh 'docker tag $JOB_NAME:$BUILD_ID kedar1704/$JOB_NAME:latest'
            sh 'docker push kedar1704/$JOB_NAME:latest'
            
        }
    }
}
