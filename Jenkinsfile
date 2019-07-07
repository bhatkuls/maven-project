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
		agent{label 'maven'}
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
		stage ('connecting Tomcat with ec2-user') {
	
			steps {
			sshagent (credentials: ['9c3b3ee9-ffad-4c42-aef7-f12fb3f82231']) {
				sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.41.54:/var/lib/tomcat/webapps'
			}
		
		}
	}
}
}
