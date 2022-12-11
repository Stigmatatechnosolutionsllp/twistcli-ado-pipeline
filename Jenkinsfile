 
 pipeline {
     environment {
      /*
       * Uses a Jenkins credential called "FOOCredentials" and creates environment variables:
       * "$FOO" will contain string "USR:PSW"
       * "$FOO_USR" will contain string for Username
       * "$FOO_PSW" will contain string for Password
       */
      SECR = credentials("prisma_secret")
    }
   
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
                  curl -k -O -u $SECR_USR:$SECR_PSW https://us-east1.cloud.twistlock.com/us-1-111573457/api/v1/util/twistcli
                  pwd
                  ls
                  env
                  chmod a+x twistcli;
                '''
            }
        }
    }
 }
