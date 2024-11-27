pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: 'ee669b76-2cac-4cf5-a747-e48cf0bd8e68', path: '', url: 'http://localhost:8080')], contextPath: '/ci-cd-jk', war: '**/*.war'}
 }
 }
}
