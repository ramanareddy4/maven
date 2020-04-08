#!groovy

pipeline {
	agent any
	 tools {
        maven 'Maven 3.6.3'
        jdk 'jdk8'
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
          sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${maven}"
                '''
            sh 'mvn clean package'
	  }
      }
    }
  }
}
