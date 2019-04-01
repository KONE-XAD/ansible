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
        sh '''tar -zvcf /data/$BUILD_TAG.tar.gz ./*
'''
      }
    }
    stage('push code') {
      steps {
        sh '''rm -rf /dockerweb
cd /data/ && tar -zvxf /data/$BUILD_TAG.tar.gz
'''
      }
    }
    stage('nginx-lbdocker') {
      steps {
        sh '''docker rm -f `docker ps -aq`
docker run -d --name nginx-lb -v /docker/conf.d/lb.conf:/etc/nginx/conf.d/default.conf nginx:latest'''
      }
    }
    stage('nginx-rs') {
      parallel {
        stage('nginx-rs-01') {
          steps {
            sh 'docker run -d --name nginx-rs-01 -v /data/monitor:/usr/share/nginx/html nginx:latest'
          }
        }
        stage('nginx-rs02') {
          steps {
            sh 'docker run -d --name nginx-rs-02 -v /data/monitor:/usr/share/nginx/html nginx:latest'
          }
        }
        stage('nginx-rs03') {
          steps {
            sh 'docker run -d --name nginx-rs-03 -v /data/monitor:/usr/share/nginx/html nginx:latest'
          }
        }
      }
    }
  }
}