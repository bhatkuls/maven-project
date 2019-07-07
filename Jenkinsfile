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
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn validate'
                }
            }
}	
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn clean compile'
                }
            }
}
		stage ('Runs the tests against the compiled source code') {

            steps {
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn clean test'
                }
            }
}
		stage ('Packs the compiled code in its distributable format') {

            steps {
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn clean package'
                }
            }
}
		stage ('Install the package into the local repository') {

            steps {
                withMaven(maven : 'MAVEN-HOME') {
                    sh 'mvn clean install'
                }
            }
}
stage {
	steps {
      sshagent (credentials: ['deploy-dev']) {
      sh 'scp -o StrictHostKeyChecking=no **/*.war ec2-user@172.31.41.54:/var/lib/tomcat/webapps'
	}
	}	
  }
}
}
}
