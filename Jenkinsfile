node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

      /*  app = docker.build("hajer/nodeapp")    /* hajer/nodeapp --> is the name given to the created image*/
	    sh 'docker build -t hajer572/my-app:2.0.0 .'  /*t for tagging  , hajer572 is the username in dockerhub*/
    }

   /* stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }*/

     
    stage('Test') {
            // sh "yarn test -u"
        }
	

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
       withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
   
	       sh "docker login -u hacer572 -p ${dockerHubPwd}"
	       
      }
	    sh 'docker push hacer572/my-app:2.0.0'
                echo "Trying to Push Docker Build to DockerHub"
    }
}
