pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
    stages{
        stage('Build'){
            steps {
		dir('/var/lib/jenkins/workspace/sonar-pipeline/addressbook/addressbook_main')
                sh 'mvn clean package'
            }    
        }
	stage('SonarQube analysis') {
            steps{
		    dir('/var/lib/jenkins/workspace/sonar-pipeline/addressbook/addressbook_main')
		    withSonarQubeEnv(credentialsId: 'sonar-id', installationName: 'sonar') { // You can override the credential to be used
		    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=test -Dsonar.projectName='test'"
    }
	    }
  }
    }
}
