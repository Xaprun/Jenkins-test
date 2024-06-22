pipeline {
  agent any
  stages {
    stage('Init') {
      parallel {
        stage('Init') {
          steps {
            sh '''
pwd
ls -al
'''
          }
        }

        stage('SysCheck') {
          steps {
            sh 'mount'
          }
        }

      }
    }

    stage('File') {
      steps {
        sh '''echo "$(date) - Jeknkins test" >> logfile.txt
chmod 0777 logfile.txt
ls -al'''
        sh 'echo "file created"'
      }
    }

    stage('File Check') {
      parallel {
        stage('File Check') {
          steps {
            sh '''lsattr logfile.txt
'''
            sh 'stat logfile.txt'
          }
        }

        stage('NewUser') {
          steps {
            sh '''groupadd insiders
               getent group |grep insiders
               '''
            echo 'Group created'
            sh 'useradd insider01 -G insiders'
            echo 'User Created'
          }
        }

      }
    }

    stage('File Own Mod') {
      steps {
        sh '''chgrp insiders logfile.txt
           chown insider01 logfile.txt 
            ls -al'''
      }
    }

  }
}
