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
          sh 'export M2_HOME=/home/ec2-user/maven/bin'
          sh 'mvn clean package'
	  }
      }
    }
  }
}
