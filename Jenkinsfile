pipeline {
    agent any
   
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
                 archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
        stage("upload war to Nexus")
		{
		  steps{
		  
		  nexusArtifactUploader artifacts: [[
		  
		  artifactId: 'simpla-app', 
		  classifier: '', 
		  file: 'target/simple-app.war', 
		  type: 'war']], 
		  credentialsId: 'nexus3', 
		  groupId: 'in.javahome',
		  nexusUrl: '172.31.7.111:8081',
		  nexusVersion: 'nexus3', 
		  protocol: 'http', 
		  repository: 'maven-releases',
		  version: '1.0'
		    	 }
		}
        }
    }

