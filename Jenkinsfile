#!groovy

def AWS_ACCOUNT_ID = 'aws-credential'
def REGION = 'us-east-1'
def ROLE = 'arn:aws:iam::729445844893:role/june-s3'
def BUCKET = 'testings3file'
def PROJECT = 'maven/single-module'


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
            withAWS(region: "${REGION}", credentials: "${AWS_ACCOUNT_ID}") {
              s3Upload(file: "pom.xml", bucket: "${BUCKET}", path: "/", acl: 'BucketOwnerFullControl')
            }
	  }
      }
    }
  }
}
