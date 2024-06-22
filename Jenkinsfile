pipeline {
  agent any
  stages {
    stage('Init') {
      steps {
        sh '''
pwd
ls -al
'''
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
      steps {
        sh 'lsattr logfile.txt'
      }
    }

  }
}