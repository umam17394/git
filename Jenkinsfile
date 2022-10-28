pipeline {
    agent any
    options { buildDiscarder(logRotator(numToKeepStr: '3')) }
  
    tools{
        maven 'maven36'
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('github test'){
           steps{
               git branch: 'main', credentialsId: 'jenkins-ssh-key', url: 'git@github.com:malleshdevops/maven-project.git'
           }
        }
        stage('maven build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('allure report'){
            steps{
                allure includeProperties: false, jdk: '', results: [[path: 'target/allure-results']]
            }
        }
        stage('archive build'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage('cleanup'){
            steps{
                cleanWs()
            }
        }
    }
}
