#!groovy

pipeline {
     agent any
     stages {
        stage('Clean Workspace') {
            steps {
                deleteDir()
                echo 'Cleeanup done'
            }
        }
        stage('Init') {
            steps {
                checkout scm
	        echo 'cloning source code'
            }
        }
	stage('build'){
        steps {
        script {
          sh '''
		export M2_HOME=/home/ec2-user/maven
		export M2=$M2_HOME/bin
		export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk-1.8.0.222.b10-0.amzn2.0.1.x86_64
		PATH=$PATH:$HOME/bin:$M2:$JAVA_HOME
		export PATH '''
          sh 'mvn clean package'
	  }
      }
    }
  }
}
