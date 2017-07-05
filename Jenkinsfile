pipeline{
  agent any

  stages{
    stage('build'){
      steps{
        sh 'export JAVA_HOME="/usr/java/latest"'
        sh 'export PATH="${JAVA_HOME}"/bin:$PATH'
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
