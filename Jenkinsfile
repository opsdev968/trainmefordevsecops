pipeline {
    agent {
  label 'docker'
}

    stages {
        stage('Git Clone') {
            steps {
                    checkout scmGit(branches: [[name: '*/email-notification']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenlins-file', url: 'git@gitlab.com:devops3431/trainmefordevsecops.git']])

                }
        }
        stage('SAST') {
            steps {
                    sh ''
                }
            }
        stage('Build and Tag ') {
            steps {
                script {
                     app = docker.build("opsdev968/snake:${env.BUILD_ID}")
                }
                }
        }
        stage('Image and Vulnerabilty Scan ') {
            steps {
                     sh ''
                }
        }
        stage('Post to Docker Hub  ') {
            steps {
                script {             //https://hub.docker.com/repository/docker/opsdev968/snake  
                docker.withRegistry('https://registry.hub.docker.com','dockerhub') {
                    app.push("${env.BUILD_ID}")
                    app.push("latest")
                    }
                }
                }
        }
        stage('Pull image Server  ') {
            steps {
                     sh 'docker-compose down'
                     sh 'docker-compose up -d'
                
                }
        }
        stage('DAAST  ') {
            steps {
                     sh ''
                }
        }
    }
}
