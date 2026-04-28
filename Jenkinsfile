pipeline {
    agent any

    tools {
        maven 'M2_HOME'
    }

    environment {
        GIT_SSH_CREDENTIALS_ID = 'github-ssh-key' // use your actual ID
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: "${env.GIT_SSH_CREDENTIALS_ID}",
                    url: 'https://github.com/Niharika-Ra/war-web-project.git',
                    branch: 'main'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive WAR') {
            steps {
                archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }
    }
}
