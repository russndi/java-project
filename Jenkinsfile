
pipeline {
  agent any
  stages {
    stage ("Unit Tests") {
      steps {
        sh 'ant -f test.xml -v'
      }
    }
    stage ("Build") {
      steps {
        sh 'ant -f build.xml -v'
      }
    }
    stage ("Deploy") {
      steps {
        sh 'aws s3 mb s3://jenkins-bucket'
        sh 'aws s3 cp rectangle-14.jar s3://jenkins-bucket'
      }
    }
  }
}
