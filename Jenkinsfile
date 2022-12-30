pipeline {
    agent any
    environment{
        registry='barayathel/spring-backend-lightweight'
        dockerImage=''
        dockerHubCredentials='docker-access'
    }
    
    stages{
        stage("build image"){
            steps{
        
		script{
			dockerImage = docker.build "$registry"
		}
	}
        stage("publish image"){
            steps{
		 script{
		   docker.withRegistry('',dockerHubCredentials){
 			dockerImage.push("currentBuild.number")
			dockerImage.push("latest")
		   }
		 }
            }
        }
    }
}
