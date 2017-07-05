pipeline{
  agent any

  stages{
    stage('build'){
	environment{
	     JAVA_HOME=/usr/java/latest		
		}
      steps{
        sh 'ant -f build.xml -v'
      }
    }
  }
}
