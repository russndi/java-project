
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
        sh 'aws s3 cp /workspace/java-pipeline2/dist/rectangle-26.jar s3://russmin-jenkinsbucket/rectangle11.jar'
      }
    }
    stage ("Report") {  
      steps { withCredentials ([[
        $class: 'AmazonWebServicesCredentialsBinding', 
        accessKeyVariable: 'AWS_ACCESS_KEY_ID', 
        credentialsId: 'AWS-Credentials-for-Jenkins', 
        secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
      ]]) {
          sh 'aws aws cloudformation describe- stack-resources --region us-east-1 --stack-name jenkins' 
            }
          }
    }
  }
}
