pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/khalil1363/avec-maven.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}