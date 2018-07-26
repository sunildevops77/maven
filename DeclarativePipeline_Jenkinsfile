pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarative_Pipeline/webapp/target/webapp.war vagrant@10.10.10.32:/var/lib/tomcat7/webapps/qaenv.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
                sh 'java -jar  /var/lib/jenkins/workspace/Declarative_Pipeline/testing.jar'
            }
        }
    }
    post
    {
        success
        {
            input message: 'Waiting for approval from DM', submitter: 'Srinivas'
    sh 'scp /var/lib/jenkins/workspace/Declarative_Pipeline/webapp/target/webapp.war vagrant@10.10.10.33:/var/lib/tomcat7/webapps/prodenv.war'
        }
        failure
        {
            mail bcc: '', body: '', cc: '', from: '', replyTo: '', subject: 'Build failed', to: 'gandham.saikrishna@gmail.com'
            
        }
        
     }
      
    
}
