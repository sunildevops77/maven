node('master') 
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild')
    {
       sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.32:/var/lib/tomcat7/webapps/qaenv.war'

    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        sh 'java -jar /home/vagrant/.jenkins/workspace/ScriptedPipeline/testing.jar' 
    }
    stage('ContinuousDelivery')
    {
        mail bcc: '', body: 'Waiting for approval..plz login and approve', cc: '', from: '', replyTo: '', subject: '', to: 'gandham.saikrishna@gmail.com'
        
        
        input message: 'Waiting for approval', submitter: 'Sudha'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.33:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
    
    
    
    

    
    
   
}