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
                    echo "PATH = ${PATH}"
                    echo "M2_HOME=/home/ec2-user/maven"
                '''
            sh 'mvn clean package'
	  }
      }
    }
  }
}
