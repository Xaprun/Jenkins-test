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
            sh '''#groupadd insiders
getent group 
               '''
            sh '''# cat /etc/passwd
# cat /etc/shadow
# cut -d: -f1 /etc/passwd
# getent passwd
# getent passwd | cut -d: -f1
awk -F: \'{ printf "Username: %-10s UID: %-5d GID: %-5d Home: %-20s Shell: %-15s\\n", $1, $3, $4, $6, $7 }\' /etc/passwd
# awk -F: \'$3 >= 1000 { print $1 }\' /etc/passwd
# getent passwd | awk -F: \'{ print $1 " - Home Directory: " $6 }\''''
          }
        }

      }
    }

    stage('File Own Mod') {
      steps {
        sh '''#chgrp insiders logfile.txt
# chown games logfile.txt 
cat logfile.txt
'''
        sh 'chmod u+s logfile.txt'
        sh 'lsattr logfile.txt'
        sh 'stat logfile.txt'
      }
    }

  }
}