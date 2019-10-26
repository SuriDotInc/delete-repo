#!groovy
import groovy.json.JsonSlurperClassic

def codeCheckout(){
      stage('Checkout') {
        checkout scm
       }
}

node {
  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '90', numToKeepStr: '30'))])

  try {
    if (env.BRANCH_NAME=="master") {
       sh 'printenv|sort'
       codeCheckout()
    }
}catch (err) {
        currentBuild.result = "FAILURE"
        throw err
        }
        finally {
        stage ('CleanUp') {
            deleteDir()
    }
  }
}
