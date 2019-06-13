#!groovy

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        checkout scm
      }
    }
    stage('Setup') {
      steps {
        sh 'npm config set strict-ssl false'
        sh 'npm install'
      }
    }
    stage('Mocha test') {
      steps {
        sh './node_modules/mocha/bin/mocha'
      }
    }
    stage('Cleanup') {
      steps {
        echo 'prune and cleanup'
        sh 'npm prune'
        sh 'rm -rf node_modules'
      }
    }
  }
}
