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
git clone git@gitee.com:kangjie1209/monitor.git
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