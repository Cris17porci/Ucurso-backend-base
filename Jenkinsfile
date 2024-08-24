pipeline {
    agent any
    stages {
        stage('Build and test') {
            agent {
                docker {
                    image 'node:20.11.1-alpine3.19' //imagen de node que contiene npm
                    reuseNode true
                }
            }
            stages {
               stage('Instalar dependencias') {
                   steps {
                       sh 'npm install'
                   }
               } 
                stage('ejecucion de test') {
                   steps {
                       sh 'npm run test'
                   }
               } 
                stage('ejecucion de build') {
                   steps {
                       sh 'npm run build'
                   }
               } 
            }
        }
        stage('deploy'){
            steps {
                sh 'docker build -t backend-base:latest .'
            }
        }
    }
}