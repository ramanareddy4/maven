#!groovy

pipeline {
  agent devops
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
          sh 'mvn clean package'
	  }
      }
    }
  }
}
