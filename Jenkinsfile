 pipeline {
      agent any
      stages {
         stage ('clone my code') {
           git 'https://github.com/bhatkuls/maven-project.git'
           }
         stage ('compile my code') {
           steps {
             withMaven(maven : 'LocalMaven') {
               sh 'mvn compile'
               }
             }
           }
         }
       }
