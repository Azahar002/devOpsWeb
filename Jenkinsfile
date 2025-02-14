pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the Artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '777c256d-4566-45a6-8370-e9adde9e8b76', path: '', url: 'http://44.220.80.201:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
