node('master') 
{
   stage('ContinuousDownload') 
   {
     git 'https://github.com/selenium-saikrishna/maven.git'
   }
   stage('ContinuousBuild') 
   {
     sh label: '', script: 'mvn package'
   }
   stage('ContinuousDeployment')
   {
       sh label: '', script: ' scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.26.19:/var/lib/tomcat7/webapps/qaenv.war'
   }
   stage('ContinuousTesting')
   {
       git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
   }
   stage('ContinuousDelivery')
   {
       sh label: '', script: ' scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.24.246:/var/lib/tomcat7/webapps/prodenv.war'
   }
   
   
   
   
   
   
   
    
    
    
}
