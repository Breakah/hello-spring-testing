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
            /*post {
                always {
                	recordIssues enabledForFailure: true, aggregatingResults:true, tool: trivy(pattern: 'trivy-*.json')
                }
            }*/
        }        
    }
}

