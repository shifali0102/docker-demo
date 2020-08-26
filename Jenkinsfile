pipeline {
    agent any
    environment {
        branch = 'master'
        scmUrl = 'https://github.com/shifali0102/docker-demo.git'
        serverPort = '8080'
        developmentServer = 'dev-myproject.mycompany.com'
        stagingServer = 'staging-myproject.mycompany.com'
        productionServer = 'production-myproject.mycompany.com'
    }
    stages {
        stage('checkout git') {
            steps {
                git branch: branch, credentialsId: 'GitCredentials', url: scmUrl
            }
        }
     }
	 }