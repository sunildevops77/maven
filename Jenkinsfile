node('master') 
{
    stage('Continuous Download_multibranch') 
	{
    git 'https://github.com/sunildevops77/maven.git'
	}
    stage('Continuous Build_multibranch') 
	{
    sh label: '', script: 'mvn package'
	}

}
