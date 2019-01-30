node('master') 
{
    stage('Cont_download_master') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('Cont_build_master') 
    {
       sh label: '', script: 'mvn package'
    }
    }
