
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
        sh 'aws s3 cp /workspace/java-pipeline2/dist/rectangle-20.jar s3://russmin-jenkinsbucket/rectangle.jar'
      }
    }
  }
}
