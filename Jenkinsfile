
node('master') 
{
    stage('ContinuousDownload-Loans') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'

    }
    stage('ContinuousBuild-Loans') 
    {
      sh 'mvn package'
    }
    stage('ContinuousDeployment-Loans')
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.1.1.5:/var/lib/tomcat7/webapps/loansenv.war'
    }
    stage('Continuoustesting-Loans')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
    }
    
    
 
    
    
    
}

