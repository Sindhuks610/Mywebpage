pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sindhuks610/Mywebpage.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory deploy.yml'
            }
        }
    }
}
