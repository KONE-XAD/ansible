pipeline {
  agent any
  stages {
    stage('') {
      environment {
        name = 'xadmin'
        web_url = 'www.xadmin.com'
      }
      steps {
        sh '''echo first
echo $name
echo $web_url'''
        sh 'echo hello'
      }
    }
    stage('second') {
      parallel {
        stage('second') {
          steps {
            sh 'echo hello'
          }
        }
        stage('second_third') {
          steps {
            sh 'echo second_third'
          }
        }
      }
    }
    stage('third') {
      parallel {
        stage('third') {
          steps {
            sh 'echo third'
          }
        }
        stage('df') {
          steps {
            sh 'echo hhh'
          }
        }
        stage('dfdf') {
          steps {
            sh 'echo fsdfs'
          }
        }
      }
    }
    stage('end') {
      steps {
        sh 'echo end'
      }
    }
  }
}