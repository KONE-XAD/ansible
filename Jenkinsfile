pipeline {
  agent any
  stages {
    stage('get code') {
      agent any
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
        sh '''tar -zvxf /data/$BUILD_TAG.tar.gz ./*
'''
      }
    }
  }
}