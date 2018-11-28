pipeline {
     tools {
        maven 'maven 3.6'
        jdk 'java11'
    }
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('deploy to Staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
    }
}
