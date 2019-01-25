node('master') 
{
    stage('Cont_download') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('Cont_build') 
    {
       sh label: '', script: 'mvn package'
    }
    stage('Cont_Deployment')
    {
       sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Pipe/webapp/target/webapp.war ubuntu@172.31.43.180:/var/lib/tomcat7/webapps/qaenv.war' 
    }
    stage('Cont_Testing')
    {
        git 'https://github.com/selenium-saikrishna/TestingNew.git'
    }
    stage('Cont_Delivery')
    {
        input message: 'Waiting for Approval', submitter: 'srinivas'
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/Pipe/webapp/target/webapp.war ubuntu@172.31.42.143:/var/lib/tomcat7/webapps/prodenv.war' 
    }
}
