
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
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.1.1.5:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('Continuoustesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for Approval from DM !', submitter: 'Srinivas'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.1.1.6:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
 
    
    
    
}

