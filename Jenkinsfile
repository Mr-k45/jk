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
deploy adapters: [tomcat9(credentialsId: '790a269c-6a3a-4567-b6c5-38661615ee94', path: '', url: 'http://localhost:8080')], contextPath: 'jk', war: '**/*.war' }
 }
 }
 }
}
