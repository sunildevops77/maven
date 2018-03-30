node('master') 
{
   
   stage('ContinuousDownload') 
   {
     git 'https://github.com/selenium-saikrishna/maven.git'
   } 

   stage('ContinuousBuild') 
   {
     
        sh '''
         mvn package'''
    } 
     
    stage('ContinuousDeployment')
    {
        sh 'scp /var/lib/jenkins/workspace/CodeasPipeline@2/webapp/target/webapp.war vagrant@10.10.10.22:/var/lib/tomcat7/webapps/qaenv.war'

    }
    
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        sh 'java -jar /var/lib/jenkins/workspace/CodeasPipeline/testing.jar'

        
    }
    
    stage('ContinuousDelivery')
    {
       input message: 'Waiting for approval from Delivery Manager', submitter: 'Venu'
        sh 'scp /var/lib/jenkins/workspace/CodeasPipeline@2/webapp/target/webapp.war vagrant@10.10.10.23:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
    
    
    
    
    
    
    
    
    
    
    
    



}
