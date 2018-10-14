#This is a pipeline code
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
    
   
   
   
   
   
   
}
