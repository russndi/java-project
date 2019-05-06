
pipeline {
  agent any
  stages {
    stage ("Unit Tests") {
      steps {
        ant -f test.xml -v
      }
    }
  }
}
