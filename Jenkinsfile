
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
        sh 'aws s3 cp rectangle-13.jar s3://russmin-assignment-4/'
      }
    }
  }
}
