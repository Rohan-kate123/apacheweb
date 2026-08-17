pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {

        stage('code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/tom-cat-1-dot/apachewe.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Artifacts') {
            steps {
                sh 'mvn package'
            }
        }
 
        stage('build image') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://65.2.153.97:8080')], contextPath: 'netflix', war: 'target/*'
            }
        }
        

    }
}
