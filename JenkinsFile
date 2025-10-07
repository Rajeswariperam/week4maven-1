pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'  // Make sure this matches your Jenkins Maven tool name
    }
    stages {
        stage('Checkout & Clean') {
            steps {
                cleanWs()  // Clean workspace before starting
                git url: 'https://github.com/Rajeswariperam/week4maven-1.git'
            }
        }
        stage('Build') {
            steps {
                dir('week4maven-1') {
                    bat "mvn clean install"
                }
            }
        }
        stage('Test') {
            steps {
                dir('week4maven-1') {
                    bat "mvn test"
                }
            }
        }
        stage('Package') {
            steps {
                dir('week4maven-1') {
                    bat "mvn package"
                }
            }
        }
    }
    post {
        success {
            echo 'Build completed successfully!'
            archiveArtifacts 'week4maven-1/target/*.jar'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
