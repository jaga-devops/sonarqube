pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
    stages{
        stage('Build'){
            steps {
		dir('addressbook')
		sh 'pwd'
                sh 'mvn clean package'
            }    
        }
	stage('SonarQube analysis') {
            steps{
		    dir('addressbook')
		    withSonarQubeEnv(credentialsId: 'sonar-id', installationName: 'sonar') { // You can override the credential to be used
		    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.projectName='test'"
    }
	    }
  }
    }
}
