pipeline {
  agent any
  stages {
    stage('get code') {
      environment {
        name = 'xadmin'
        web_url = 'www.xadmin.com'
      }
      steps {
        sh '''echo "delete workspace"
rm -rf ./*
echo "get code"
git clone root@172.17.53.26:monitor
'''
      }
    }
    stage('code build') {
      steps {
        sh 'touch hello.txt'
      }
    }
  }
}