pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        branch = 'master'
        scmUrl = 'https://github.com/shifali0102/docker-demo.git'
        serverPort = '8080'
        developmentServer = 'dev-myproject.mycompany.com'
        stagingServer = 'staging-myproject.mycompany.com'
        productionServer = 'production-myproject.mycompany.com'
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
  }
}
