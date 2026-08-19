pipeline {
    agent any

    tools {
        maven 'maven'
    }

    stages {

        stage('Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Rohan-kate123/apacheweb.git'
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

        stage('Docker Build') {
            steps {
                sh 'docker build -t netflix5 .'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy(
                    adapters: [
                        tomcat9(
                            alternativeDeploymentContext: '',
                            credentialsId: 'jenkins',
                            path: ''
                            url: 'http://65.1.100.168:8080'
                        )
                    ],
                    contextPath: 'sample',
                    war: 'target/*.war'
                )
            }
        }
    }
}
