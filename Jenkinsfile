node('slavebranch') 
{
    stage('Continuous Download_sales') 
	{
    git 'https://github.com/kiran-113/maven.git'
	}
    stage('Continuous Build') 
	{
    sh label: '', script: 'mvn package'
	}

}
