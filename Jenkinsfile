def buildNumber = BUILD_NUMBER
pipeline {
    agent any
    

stages {
      stage('git clone') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/MithunTechnologiesDevOps/java-web-app-docker.git'
         }        
      }         

       stage('maven build ') {
           steps {
                  // Run Maven on a Unix agent.
            sh label: '', script: '''/opt/maven/bin/mvn clean package'''
           }
           }
         stage ('build docker image') {
		    steps { 
		         sh "docker build -t naruto304/java-web-app-docker-bnc:${buildNumber} ."  
		    }
         }
         stage ('docker login and push') {
	        steps {
	            withCredentials([string(credentialsId: '1fa11338-4811-4093-a024-36efa84f4c4a', variable: 'docker_passwd')]) {
                 sh "docker login -u naruto304 -p ${docker_passwd}"
                 sh "docker push naruto304/java-web-app-docker-bnc "
	            }
}
}
}
}
