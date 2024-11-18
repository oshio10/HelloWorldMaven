pipeline { 
    agent any 
    stages {
        stage('Build') { 
            steps {
               script {
		       sh "mvn clean"
	       }
            }
        }
        stage('Deploy') {
            steps {
               script {
		       sh "mvn package"
	       }
            }
        }
    }
}
