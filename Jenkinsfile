pipeline {
    agent any

    stages {
        stage('Récupération du code du prof') {
            steps {
                git url: 'https://github.com/khalil1363/avec-maven.git', branch: 'master'
            }
        }

        stage('Compilation') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Tests (on ignore les échecs)') {
            steps {
                sh 'mvn test -Dmaven.test.failure.ignore=true'
            }
        }

        stage('Package (on saute les tests)') {
            steps {
                sh 'mvn package -Dmaven.test.skip=true'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            junit testResults: '**/target/surefire-reports/*.xml', allowEmptyResults: true
        }
        success {
            echo 'Build réussi avec Jenkinsfile depuis mon dépôt !'
        }
    }
}