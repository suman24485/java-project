pipeline{
  agent {
    label 'CentOS'
  }

  stages{
      stage('Unit Tests'){
        agent{
          label 'apache'
        }
        steps{
          sh 'ant -f test.xml -v'
          junit 'reports/result.xml'
        }
      }
    stage('build'){
      agent{
        label 'apache'
      }
      steps{
        sh 'ant -f build.xml -v'
      }
      post{
        success{
          archiveArtifacts artifacts: 'dist/*.jar',fingerprint:true
        }
      }
    }
    stage('deploy'){
      agent{
        label 'apache'
      }
      steps{
        sh "cp dist/rectangle_${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all"
      }
    }
    stage ("Running on CentOS"){
      agent{
          label 'CentOS'
      }
      steps{
        sh "wget http://masterj/rectangles/all/rectangle_${env.BUILD_NUMBER}.jar"
        sh "java -jar rectangle_${env.BUILD_NUMBER}.jar 3 4"
      }
    }
    stage("Test on Debian"){
      agent {
        docker 'openjdk:8u131-jre'
      }
      steps{
        sh "wget http://masterj.suman.com/rectangles/all/rectangle_${env.BUILD_NUMBER}"
        sh "java -jar rectangle_${env.BUILD_NUMBER}.jar 3 4"
      }
    }
  }
}
