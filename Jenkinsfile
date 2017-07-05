pipeline{
  agent {
      Slave1
    }
  stages{
    stage('build'){
      steps{
        sh 'ant -f build.xml -v'
      }
    }
  }
  post{
    always{
      archiveArtifacts artifacts: 'dist/*.jar',fingerprint:true
    }
  }
}
