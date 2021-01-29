#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        jdk 'openJDK-15.0.02'
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Setup'){
            steps{
                git url:'http://10.250.8.1:8929/root/hello-spring-testing.git',branch:'master' 
            }            
        }
        stage('Test'){
            steps{
                withGradle{
                    sh './gradlew test'
                }
            }
        }
        stage('Build') {
            steps {                
                withGradle {
                    sh './gradlew assemble'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy...."
            }
        }
    }
}
