node('master') 
{
    stage('Continuous Download_newbranch') 
	{
    git 'https://github.com/sunildevops77/maven.git'
	}
    stage('Continuous Build_newbranch') 
	{
    sh label: '', script: 'mvn package'
	}
}
