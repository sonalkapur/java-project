node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/sonalkapur/java-project.git'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    stage('Build'){
        sh 'ant -f build.xml -v'
    }
    stage('Deploy'){
         sh "aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://seis665-03-1"
    }
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'd9ecb87d-e98e-4c0b-8121-fc187c7c324d', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
          // some block
          sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
       } 
   }
}
