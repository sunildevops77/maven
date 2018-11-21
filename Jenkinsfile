
node('master') 
{
    stage('ContinuousDownload-master') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'

    }
    stage('ContinuousBuild-master') 
    {
      sh 'mvn package'
    }
    stage('ContinuousDeployment-master')
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.1.1.5:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('Continuoustesting-master')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
    }
    
    
 
    
    
    
}

