node('new job')
{
     stage 'build'
	        checkout scm
			sh 'mvn clean pacakge'
	 stage 'test'
	        checkout scm
			sh 'mvn clean test'
}
