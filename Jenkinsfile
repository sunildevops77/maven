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
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp
				    /target/webapp.war 
					           vagrant@172.31.18.210:/var/lib/tomcat7/webapps/qaenv.war'

            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'       
            }
        }
    }
    post
    {
        success
        {
             sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target
			      /webapp.war vagrant@172.31.31.227:/var/lib/tomcat7/webapps/prodenv.war'
        }
        failure
        {
            mail bcc: '', body: 'FAILED', cc: '', from: '', replyTo: '', 
			         subject: 'Jenkins job status', to: 'gandham.saikrishna@gmail.com'
        }
    }  
}



























pipeline

{

    agent any

    stages

    {
<<<<<<< HEAD

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

                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war vagrant@172.31.18.210:/var/lib/tomcat7/webapps/qaenv.war'

            }

        }

        stage('ContTesting')

        {

            steps

            {

                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'

               

            }

        }
=======
       sh label: '', script: 'mvn clean package'
>>>>>>> 890a4dfe3742292f6af294b302f11d046baf9fe3
    }
    post
    {
        success
        {
             sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline/webapp/target/webapp.war vagrant@172.31.31.227:/var/lib/tomcat7/webapps/prodenv.war'
        }
        failure
        {
            mail bcc: '', body: 'FAILED', cc: '', from: '', replyTo: '', subject: 'Jenkins job status', to: 'gandham.saikrishna@gmail.com'
        }
    }
<<<<<<< HEAD
       

   
}
















=======

#####################
>>>>>>> 890a4dfe3742292f6af294b302f11d046baf9fe3
