Pipeline {
 agent any
 stages {
  stage ('Build') {
    steps {
      sh 'printenv'
      
     }
  }
  stage ('Publish ECR') {
    steps {
      withEnv (["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}","AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}",AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"] {
       sh 'docker login -u AWS -p $(aws ecr-public get-login-password --region us-east-1) public.ecr.aws/m5i8y1n9'
       sh 'docker built -t my_repository .'
       sh 'docker push public.ecr.aws/m5i8y1n9/my_repository:latest
      }
     }
    } 
   }
  }
 
 
