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

    stage('Dependency Scanning'){
        parallel {
            stage('npm dependency Audit'){
              steps{
                sh '''
                  npm audit --only=prod
                  echo $1
                '''
                // npm audit --audit-level=critical

              }
            }
            stage('OWASP dependency check'){
              steps{
                dependencyCheck additionalArguments: '''
                --scan \'./\'
                --out \'./\'
                --format \'ALL\'
                --prettyPrint''', odcInstallation: 'OWASP Dep-Check 10'
              }
            }
        }
    }



  }
}