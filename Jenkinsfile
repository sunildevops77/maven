pipeline {
    agent any 
    stages {
        stage('ContinuousDownload') {
            steps {
                git 'https://github.com/selenium-saikrishna/maven.git'
            }
        }
		stage('ContinuousBuild') {
            steps {
                sh 'mvn package'
            }
        }
		stage('ContinuousDeployment') {
            steps {
                sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.32:/var/lib/tomcat7/webapps/qaenv.war'
            }
        }
		stage('ContinuousTesting') {
            steps {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        sh 'java -jar /home/vagrant/.jenkins/workspace/ScriptedPipeline/testing.jar' 
            }
        }
	}
	post
	{
	    success
		{
		   input message: 'Waiting for approval', submitter: 'Sudha'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.33:/var/lib/tomcat7/webapps/prodenv.war'
		}
		failure
		{
		    mail bcc: '', body: 'Waiting for approval..plz login and approve', cc: '', from: '', replyTo: '', subject: '', to: 'gandham.saikrishna@gmail.com'
		}
	
	
		
		
		
    }
}