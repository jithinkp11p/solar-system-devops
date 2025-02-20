pipeline {
  agent any

  tools {
    nodejs 'nodejs-22-6-0'
  }

  stages{
    stage('check node version'){
      steps{
         sh 'node -v'
         sh 'npm -v'
      }
    }
  }
}git 