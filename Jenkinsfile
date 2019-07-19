// Obtaining an Artifactory server instance defined in Jenkins:
			
def server = Artifactory.server 'Artifactory Version 6.11.1'

		 //If artifactory is not defined in Jenkins, then create on:
		// def server = Artifactory.newServer url: 'Artifactory url', username: 'username', password: 'password'

//Create Artifactory Maven Build instance
def rtMaven = Artifactory.newMavenBuild()

def buildInfo

pipeline {
    agent any

	//tools {
		//jdk "jdk12"
		//maven "M3"
	//}

    stages {
        stage('Git Checkout'){
            steps {
                git url: 'https://github.com/Debasis04/Testpipelinesrccode.git'
            }
        }

     	stage('SonarQube analysis') {
	     steps {
		//Prepare SonarQube scanner enviornment
		echo 'SonarQubeAnalysis will be done here'
		
	      }
	}


	    stage('Build') {
		steps {
		   script {
		echo 'Execute Maven will build the pom.xml which is there in source code repository'
			}
		}
		
	}
	stage('Staging') {
		
	   steps {
		script {
			rtMaven.tool = 'Maven-3.6.1' //Maven tool name specified in Jenkins configuration
			echo 'The artefacts beuilt in Build stage are pushed to Artefactory repo'
			}
	    }
	}

	

	stage('Deploy') {
		steps {
		  script {
		echo 'Publish the artifacts in Release repo of Artifactory'
		//server.publishBuildInfo buildInfo
		}
		}
	}
}
}
