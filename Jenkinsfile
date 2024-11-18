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
	        stage("Tag Version. Release") {
            environment {
                GIT_TAG = "Version-2.$BUILD_NUMBER"
            }
            steps {
                script {
                    // Set Git configurations
                    sh 'git config user.name "oshio10"'
                    sh 'git config user.email "patricksunchen@gmail.com"'
                    
                    // Tagging the repository
                    sh "git tag -a ${GIT_TAG} -m 'Release ${GIT_TAG}'"
                    
                    // Push the tag to the repository securely
                    withCredentials([usernamePassword(credentialsId: 'hoang6337', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/HoangPham6337/HelloWorldMaven.git ${GIT_TAG}"
                    }
                }
            }
        }
    }
}
