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
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn clean compile'
                }
            }
}
}
}
