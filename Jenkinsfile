pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/prakashk0301/maven-project'
        }
  }
    {
		stage ('CValidates that the project is correct') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn validate'
                }
            }
}	
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
}
		stage ('Runs the tests against the compiled source code') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean test'
                }
            }
}
		stage ('Packs the compiled code in its distributable format') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean package'
                }
            }
}
		stage ('Install the package into the local repository') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean install'
                }
            }
}
		stage ('Copies the final package to the remote repository') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean deploy'
                }
            }
}
}
}
