node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

	
    stage('Build image') {
        /* This builds the actual image */

      /*  app = docker.build("hajer/nodeapp")    /* hajer/nodeapp --> is the name given to the created image*/
	 /*   sh 'docker build -t hacer572/my-app:3.0.0 .'  /*t for tagging  , hajer572 is the username in dockerhub*/
	    
	        sh 'docker build -t myweb-app:3.0.0 .'  /*t for tagging  , hajer572 is the username in dockerhub*/
    }

   /* stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }*/

     
    stage('Test') {
            // sh "yarn test -u"
        }
	

   /* stage('Push image') {
        /* You would need to first register with DockerHub before you can push images to your account*/
		
     /*  withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
   
	       sh "docker login -u hacer572 -p ${dockerHubPwd}"
	       
      }
	    sh 'docker push hacer572/my-app:2.0.0'
                echo "Trying to Push Docker Build to DockerHub"
    }*/
	
	/*395453232904.dkr.ecr.eu-central-1.amazonaws.com/drsa-app-core */
	/*stage('Push image') {
        docker.withRegistry('https://395453232904.dkr.ecr.eu-central-1.amazonaws.com', 'eu-central-1:push-To-ECR') {
            sh "docker push https://395453232904.dkr.ecr.eu-central-1.amazonaws.com/hacer572/my-app:2.0.0"
        }} */
		
stage('Push image') {
        docker.withRegistry('https://395453232904.dkr.ecr.eu-central-1.amazonaws.com', 'ecr:eu-central-1:push-To-ECR') {
            sh "docker tag myweb-app:3.0.0 395453232904.dkr.ecr.eu-central-1.amazonaws.com/drsa-app-core"
	    sh "docker push 395453232904.dkr.ecr.eu-central-1.amazonaws.com/drsa-app-core"
	    sh "docker rmi myweb-app:3.0.0 | true"

        }
    }
	
	
	
}
