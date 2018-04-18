//Changes done for the jenkins file

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
        sh 'scp /var/lib/jenkins/workspace/CodeasPipeline/webapp/target/webapp.war vagrant@10.0.0.11:/var/lib/tomcat7/webapps/qaenv.war'
    }
    
    stage('ContinuousTesting')
    {
        
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        
        sh 'java -jar /var/lib/jenkins/workspace/CodeasPipeline/testing.jar'
        
    }
    
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for approval for delivery from Delivery manager', submitter: 'Venu'
        sh 'scp /var/lib/jenkins/workspace/CodeasPipeline/webapp/target/webapp.war vagrant@10.0.0.13:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    

    
    
    
    
}

