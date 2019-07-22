pipeline {
    agent any
     stages {
        stage('Build') {
            steps {
                echo 'Building..'
                checkout scm
              }
          }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'mvn test'
                }
          }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'mvn clean package'
              } 
          }
        }
     }
