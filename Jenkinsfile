#!groovy

def AWS_ACCOUNT_ID = '729445844893'
def REGION = 'es-east-1'
def ROLE = 'arn:aws:iam::729445844893:role/june-s3'
def BUCKET = 'testings3file'
def PROJECT = '/home/ec2-user/maven-samples/single-module'

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
            }
        }
	stage('build and upload'){
        steps {
        script {
          // upload files to S3
	   sh 'mvn clean package'
          def jar_files = findFiles(glob: "${PROJECT}/target/*.jar")
          jar_files.each {
            echo "JAR found: ${it}"
            withAWS(region: "${REGION}", role: "${ROLE}", roleAccount: "${AWS_ACCOUNT_ID}") {
              s3Upload(file: "${it}", bucket: "${BUCKET}", path: "${PROJECT}/", acl: 'BucketOwnerFullControl')
            }
	  }
	}
      }
    }
  }
}
