pipeline {
  agent any
    stages {
      stage('Setting up environment variables'){
        def AWS_ACCOUNT_ID = '729445844893'
        def REGION = 'es-east-1'
        def ROLE = 'arn:aws:iam::729445844893:role/june-s3'
        def BUCKET = 'testings3file'
        def PROJECT = 'maven/single-module'
      }
      stage ('Build app and upload artifacts to S3'){
        agent {
        }
        steps {
          // build source code
          dir('./SourceCode') {
            sh 'mvn -B clean package'            
          }
        }
        script {
          // upload files to S3
          def jar_files = findFiles(glob: "**/SourceCode/${PROJECT}/target/*.jar")
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
