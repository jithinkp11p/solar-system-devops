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
                  
                '''
                // npm audit --audit-level=critical
                //  echo $1

              }
            }
            stage('OWASP dependency check'){
              steps{
                dependencyCheck additionalArguments: '''
                --scan \'./\'
                --out \'./\'
                --format \'ALL\'
                --prettyPrint''', odcInstallation: 'OWASP Dep-Check 10'

              dependencyCheckPublisher pattern: 'dependency-check-report.xml'

              publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, keepAll: true, reportDir: './', reportFiles: 'dependency-check-jenkins.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
              }
            }
        }
    }



  }
}