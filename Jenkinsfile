//#!/usr/bin/env groovy

pipeline {

    agent {
        label('jenkins-slave-docker-node')
    }
    stages {
        stage('Compile') {
            steps {
                script {
                    sh "mvn clean compile -DskipTest"
                }
            }
        }
        stage('Unit Test') {
            steps {
                script {
                    sh "mvn test"
                }
            }
        }
        stage('package') {
            steps {
                script {
                    sh "mvn package assembly:single"
                }
            }
        }
        stage('Install') {
            steps {
                script {
                    sh "mvn install"
                }
           }    
        }  
      stage('Execute') {
            steps {
                script {
                sh "java -jar /tmp/workspace/p-docker2/main/target/main-1.0.0-SNAPSHOT-jar-with-dependencies.jar"
                }
            }
        }  
    }
}
