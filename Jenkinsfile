
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
        sh 'aws s3 cp dist/rectangle-36.jar s3://russmin-jenkinsbucket/rectangle.jar'
      }
    }
    stage ("Report") {  
      steps { withCredentials ([[
        $class: 'AmazonWebServicesCredentialsBinding', 
        accessKeyVariable: 'AWS_ACCESS_KEY_ID', 
        credentialsId: 'AWS-Credentials-for-Jenkins', 
        secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
      ]]) {
          sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins' 
            }
          }
    }
  }
}
