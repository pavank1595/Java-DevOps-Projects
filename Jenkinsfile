pipeline {
    agent any

    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.8/bin"
    }

    stages {
        
        stage('Get-Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/pavank1595/Java-DevOps-Projects.git'
            }
        }

        stage('Build-Code') {
            steps {
                sh "mvn clean package"
            }
        }

        stage('SonarQube-Analysis') {
            steps {
                withSonarQubeEnv('Sonar-Server-10.6') {
                    sh "mvn sonar:sonar"
                }
            }
        }
    }
}