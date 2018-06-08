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
        sh 'scp /var/lib/jenkins/workspace/Pipeline/webapp/target/webapp.war vagrant@10.10.10.92:/var/lib/tomcat7/webapps/qaenv.war'
    }
    
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
    
        sh 'java -jar /var/lib/jenkins/workspace/Pipeline/testing.jar'
        
    }
    
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for Delivery', submitter: 'Venu'
        sh 'scp /var/lib/jenkins/workspace/Pipeline/webapp/target/webapp.war vagrant@10.10.10.93:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
    
    
   
}

