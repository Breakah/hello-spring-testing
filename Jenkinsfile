#!/usr/bin/env groovy

pipeline {
    agent any
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Build') {
            steps {	
                withGradle{
                        sh './gradlew dependencyCheckUpdate'     
                }
            }
        }
        stage('Dependency-Check') {
            steps {
                withGradle{
                    sh './gradlew dependencyCheckAnalyze'
                }                
            }
            post {
                always {
                    dependencyCheckPublisher pattern: 'build/reports/dependency-check-report.xml'
                }
            }
        }   
        stage('Publish'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'sonar_nexus', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {

                    sh './gradlew publish'
                }
            }
        }     
    }
}

