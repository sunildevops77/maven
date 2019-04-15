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
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.23.186:/var/lib/tomcat8/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingNew.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
        
    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for Approval from Delivery Team', submitter: 'Ravi'
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.20.249:/var/lib/tomcat8/webapps/prodenv.war'
    }
    
    
    
    
}
