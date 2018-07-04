pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                sh 'scp /home/vagrant/.jenkins/workspace/Declarative_Pipeline/webapp/target/webapp.war vagrant@10.10.10.52:/var/lib/tomcat7/webapps/qaenv.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
      sh 'java -jar /home/vagrant/.jenkins/workspace/Scripted_Pipeline/testing.jar' 
            }
        }
    }
    post
    {
        success
        {
             input message: 'Waiting for approval', submitter: 'Sheshi'
        sh 'scp /home/vagrant/.jenkins/workspace/Scripted_Pipeline/webapp/target/webapp.war vagrant@10.10.10.53:/var/lib/tomcat7/webapps/prodenv.war'
        }
        failure
        {
            mail bcc: '', body: 'Testing has failed', cc: '', from: '', replyTo: '', subject: '', to: 'gandham.saikrishna@gmail.com'   
        }
        
        
        
        
    }
    
    
    
    
    
}
