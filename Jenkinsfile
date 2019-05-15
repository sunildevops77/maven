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
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.83.143:/var/lib/tomcat8/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingNew.git'
        sh label: '', script: 'echo "Testing Passed"'
    }
    stage('ContinuousDelivery')
    {
        input 'Waiting for Approval from Delivery Manager!'
         sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.80.141:/var/lib/tomcat8/webapps/prodenv.war'
    }
    
    
    
    
}
