pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sthita933/project01-maven.git'
            }
        }
         stage('Compilitation') {
            steps {
                sh 'mvn clean compile'
            }
        }
         stage('Testing code') {
            steps {
                sh 'mvn clean test'
            }
        }
         stage('Pacakge') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('Deploy') {
            steps {
                sh 'sudo cp target/*.war /home/ubuntu/apache-tomcat-9.0.117/webapps/'
            }
        }
    }
}
