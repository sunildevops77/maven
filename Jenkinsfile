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
        sh 'scp /home/vagrant/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war vagrant@10.10.10.52:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
      sh 'java -jar /home/vagrant/.jenkins/workspace/Scripted_Pipeline/testing.jar'  
    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for approval', submitter: 'Sheshi'
        sh 'scp /home/vagrant/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war vagrant@10.10.10.53:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
    
    
    
}
