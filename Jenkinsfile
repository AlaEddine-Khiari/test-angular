pipeline {
  agent any
    stages {
        stage('Getting project from Git') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/AlaEddine-Khiari/test-angular']]])
                }
            }
        }
        stage('Cleaning the project') {
             steps{
                script{
                    sh "npm ci"
                }
            }
        }
        stage('Artifact Construction') {
             steps{
                script{
                    sh "ng build"
                }
            }
        }


        stage('Build Docker Image') {
             steps{
                script{
                    sh "docker build -t alaeddine/test-angular:latest."
                }
            }
        }


       }
      }
