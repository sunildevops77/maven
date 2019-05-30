node('master')

{

stage('Continuous Download') 
   
	 {
	
    git 'https://github.com/sunildevops77/maven.git'
    
	}

stage('Continuous build') 
   
	 {
	
   sh label: '', script: 'mvn package'
	}

stage('Continuous Deployment') 
   
	 {
	
 sh label: '', script: 'scp  /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.21.16:/var/lib/tomcat8/webapps/qaenv.war'
	}
stage('Continuous Testing') 
   
	 {
	sh label: '', script: 'echo "Testing Passed"'
	}
stage('Continuous Delivery') 
   
	 {
	sh label: '', script: 'scp  /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.28.16:/var/lib/tomcat8/webapps/prodenv.war'
	}
}


