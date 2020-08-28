pipeline {
    agent any
	tools {
     nodejs	'nodejs'
	 }
    environment {
        branch = 'master'
        scmUrl = 'https://github.com/shifali0102/docker-demo.git'
        serverPort = '8080'
        HOME = '.'
    }
    stages {
        stage('checkout git') {
            steps {
                git branch: branch, credentialsId: 'GitCredentials', url: scmUrl
            }
        }
	stage('NPM INSTALL') {
            steps {
                sh 'npm -version'
                sh 'npm install'
            }
        }
	stage('Build Docker Image' ) {
	    steps {
	         sh 'docker build -t shifalisri0102/nodejs:$BUILD_ID .'
	         withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {
      		     sh 'docker push shifalisri0102/nodejs:$BUILD_ID'
	                }
             }
        }
	stage('Using kubernetes'){
	     steps{
	   	withKubeConfig(caCertificate: '', 
			       clusterName: 'devcluster.k8s.local', 
			       contextName: 'devcluster.k8s.local', 
			       credentialsId: 'k8s', 
			       namespace: '', 
			       serverUrl: '  https://api-devcluster-k8s-local-2a2k6f-1035094534.us-east-1.elb.amazonaws.com') {
    					 sh 'kubectl apply -f deployment.yaml'
                        }
		   }
	     }
        
    }
}
