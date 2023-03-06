pipeline {
    agent {
        label 'docker'
    }

    stages {
        stage('Cloning Git') {
            steps {
                // Get some code from a GitHub repository
                //git 'https://github.com/jglick/simple-maven-project-with-tests.git'
               checkout scmGit(branches: [[name: '*/email-notification']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenlins-file', url: 'git@gitlab.com:devops3431/trainmefordevsecops.git']])
            }
        }
        stage('SAST') {
            steps {
                sh ''
            }
        }     
        stage('Build and Tag') {
            steps {
                script {
                  app = docker.build("opsdev968/snake:${env.BUILD_ID}")
                }
            }
        }
        
        stage('Image Scan') {
            steps {
                  sh ''
            }
        }
        stage('Post to Docker Hub') {
            steps {
                sh ''
            }
        }
        stage('Pull Image Server') {
            steps {
                  sh ''
            }
        }
        stage('DAAS') {
            steps {
                  //sh 'docker-compose down'
                  //sh 'docker-compose up'
                  sh ''
            }
        }
      
    }
}

