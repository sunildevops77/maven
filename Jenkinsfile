node('master') 
{
    stage('Cont_download_loans') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('Cont_build_loans') 
    {
       sh label: '', script: 'mvn package'
    }
    }
