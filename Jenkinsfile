pipeline {
    agent any
    @Library('github.com/releaseworks/jenkinslib') _
    withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'aws-key', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        AWS("--region=eu-east-1 s3 ls")
    }
    stages {
        stage('deploy') {
            steps {
              sh "aws configure set region $AWS_DEFAULT_REGION" 
              sh "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"  
              sh "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
              sh "aws s3 cp index.html s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/css/reset.css s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/css/styles.css s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/logo.png s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/adobo1.jpg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/adobo2.jpeg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/karekare.jpg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/lechon.jpg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/lumpia.jpg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/pancit.jpg s3://static-bucket-jenkins"
              sh "aws s3 cp ./resources/images/filipinoman.jpg s3://static-bucket-jenkins"
            }
        }
    }
}