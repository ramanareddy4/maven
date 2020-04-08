#!groovy

pipeline {
	agent {
	label 'devops'
	}
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
              withMaven(maven : 'maven') 
            sh 'mvn clean package'
	  }
      }
    }
  }
}
