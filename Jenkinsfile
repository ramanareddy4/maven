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
            withAWS(region: "${REGION}", role: "${ROLE}", roleAccount: "${AWS_ACCOUNT_ID}") {
              s3Upload(file: "/home/ec2-user/maven-samples/single-module/target/single-module-project.jar", bucket: "${BUCKET}", path: "${PROJECT}/", acl: 'BucketOwnerFullControl')
            }
	  }
      }
    }
  }
}
