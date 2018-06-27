pipeline {
    agent any
    tools {
        maven "maven_354"
        jdk "java_8"
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/jglick/simple-maven-project-with-tests.git'
            }
        }
        stage('Build') {
          steps{
             sh " mvn -Dmaven.test.failure.ignore clean package"
          }
       }
        stage('Results') {
           steps{
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
           }
       }
    }
}
