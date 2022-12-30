pipeline {
    agent any
    environment{
        registry='barayathel/spring-backend-lightweight'
        dockerImage=''
        dockerHubCredentials='030d510e-c949-42ae-83ef-f89d8956f697'
    }
    
    stages{
        stage("build image"){
            steps{
        
		script{
			dockerImage = docker.build "$registry"
		}
	}
	}
        stage("publish image"){
            steps{
		 script{
		   docker.withRegistry('',dockerHubCredentials){
 			dockerImage.push("$currentBuild.number")
			dockerImage.push("latest")
		   }
		 }
            }
        }
	stage("run image"){

	    steps{
		script {
			docker.image(dockerImage).withRun('-p 7000:7000') 
		}
	    }
	}
    }			

}

