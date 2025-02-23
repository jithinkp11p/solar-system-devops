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

    stage('Install dependency'){
      steps{
          sh 'npm install --no-audits'
      }
    }

    stage('npm dependency Audit'){
      steps{
        sh '''
           npm audit --audit-level=critical
           echo $1
        '''

      }
    }



  }
}