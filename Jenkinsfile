 
 pipeline {
     environment {
      /*
       * Uses a Jenkins credential called "FOOCredentials" and creates environment variables:
       * "$FOO" will contain string "USR:PSW"
       * "$FOO_USR" will contain string for Username
       * "$FOO_PSW" will contain string for Password
       */
      SECR = credentials("prismacloudsecrets")
    }
  withCredentials([usernamePassword(credentialsId: 'prisma_secret', passwordVariable: 'pass', usernameVariable: 'user')]) {
    // the code here can access $pass and $user
   
    agent any 
    stages {
        stage('Install TwistCli') { 
            steps {
                 sh '''#!/bin/bash
                  echo "hello world"
                  echo "Install TwistCLI"
                  ls
                  echo $SECR_USER
                  echo $SECR_CONSOLEURL
                  echo $SECR_PASSWORD
                  curl -k -O -u $user:$password $SECR_CONSOLEURL/api/v1/util/twistcli
                  pwd
                  ls
                  chmod a+x twistcli;
                '''
            }
        }
    }
  }
 }
