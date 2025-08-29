pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17'
        }
    }
    stages {
        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }
        stage('Print PATH') {
            steps {
                sh 'echo $PATH'
                sh 'which docker'
            }
        }
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
