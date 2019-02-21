node('master') 
{
   stage('ContnuousDownload') 
   {
      git 'https://github.com/selenium-saikrishna/maven.git'
   }
   stage('ContnuousBuild') 
   {
      sh label: '', script: 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.31.191:/var/lib/tomcat8/webapps/qaenv.war'
   }
   stage('ContinuousTesting')
   {
       git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
   }
   stage('ContinuousDelivery')
   {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.18.210:/var/lib/tomcat8/webapps/prodenv.war'
   }
   
   
   
   
   
   
   
   
   
   
   
}
