pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/bhatkuls/maven-project.git'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
}
}
}
