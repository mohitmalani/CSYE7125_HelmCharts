#!/usr/bin/env groovy
pipeline {
  agent any
  tools {nodejs "node"}
  environment {
    GH_TOKEN = credentials('GH_TOKEN')
  }
  stages {

    stage('Clone Repository'){
      steps {
        checkout scm
      }
    }
    
    stage ('Deploy') {
      steps {
        sh"""
        export GH_TOKEN=${env.GH_TOKEN}
        npm install semantic-release-helm
        npm install --save-dev semantic-release
        npx semantic-release
        """ 
      }
    }
  } 
}
