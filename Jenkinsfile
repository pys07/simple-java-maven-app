pipeline {
    agent any
    tools {
        maven 'Maven' // Refers to the Maven installation configured in Jenkins
    }
    stages {
        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Check the console output for details.'
        }
    }
}