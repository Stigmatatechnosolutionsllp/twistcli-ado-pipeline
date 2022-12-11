 
 pipeline {
     environment {
      /*
       * Uses a Jenkins credential called "FOOCredentials" and creates environment variables:
       * "$FOO" will contain string "USR:PSW"
       * "$FOO_USR" will contain string for Username
       * "$FOO_PSW" will contain string for Password
       */
      SECR = credentials("prisma_secret")
      twistlock_url = credentials("prisma_secret")
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
                  curl -k -O -u $SECR_USR:$SECR_PSW $twistlock_url/api/v1/util/twistcli
                  pwd
                  ls
                  env
                  chmod a+x twistcli;
                '''
            }
        }
     stage('Pull Public Docker Image') { 
            steps {
                  sh '''#!/bin/bash
                  docker pull bitnami/rabbitmq
                '''
            }
        }
        stage('Image Vulnerability Scan') { 
            steps {
                  sh '''#!/bin/bash
                  echo "Start Image Scan"
                  ./twistcli images scan --details --address ${twistlock_url} --u ${SECR_USR} -p ${SECR_PSW} bitnami/rabbitmq
                '''
            }
        }
        stage('Runtime - Image Analysis Sandbox') { 
            steps {
                  sh '''#!/bin/bash
                  echo "Start Image Scan"
                  sudo ./twistcli sandbox --analysis-duration 30s --address ${twistlock_url} --u ${SECR_USR} -p ${SECR_PSW} bitnami/rabbitmq
                '''
            }
        }
    }
 }
