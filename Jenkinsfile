 
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
    agent any 
    stages {
        stage('Install TwistCli') { 
            steps {
                  sh '''#!/bin/bash
                  echo "hello world"
                  echo "Install TwistCLI"
                  ls
                  pwd
                  ls
                '''
            }
        }
    }
 }
