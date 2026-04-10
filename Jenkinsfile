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
         stage('Pacakge the code ') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('upload to s3') {
            steps {
                step([$class: 'S3Publisher', entries: [[bucket: 'uploaded', sourceFile: '**/*.war', destinationBucket: '', selectedRegion: 'ap-south-1', flatten: false, managedArtifacts: true, noUploadOnFailure: false]]])
            }
        }
         stage('Deploying code ') {
            steps {
                sh 'cp target/*.war /home/ubuntu/apache-tomcat-9.0.117/webapps/'
            }
        }
    }
}
