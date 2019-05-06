
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
        sh 'aws s3 cp /workspace/java-pipeline2/dist/rectangle-21.jar s3://russmin-jenkinsbucket/rectangle.jar'
      }
    }
    stage ("Report") {
      steps { 
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', AKIAI2VHK2MZAXJ6FTXA: 'AWS-Credentials-for-Jenkins', +4fUfxHLbuFJO2sLpjoc8wallRBYmSG5289pmL4g: 'AWS_SECRET_ACCESS_KEY']]{
          sh 'aws aws cloudformation describe- stack-resources --region us-east-1 --stack-name jenkins' 
            }
          }
       }
  }
}
