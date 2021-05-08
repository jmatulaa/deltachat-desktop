pipeline {
	agent any
	tools {
	    nodejs "node"
	}
	stages {
		stage('Build') {
			steps {
				sh 'git pull origin master'
				sh 'npm install'
				sh 'npm run build'
				
				}
		post {
			failure{
				emailext attachLog: true,
				body: "Error is in ${env.BUILD_URL}",  
				subject: "Failed Pipeline: ${currentBuild.fullDisplayName}", 
				to: 'julaa.mat@gmail.com'
				}
			success{
				emailext attachLog: true, 
				body: "Success",  
				subject: "Success Pipeline: ${currentBuild.fullDisplayName}", 
				to: 'julaa.mat@gmail.com'
				
				}	
			}
		}
		stage('Test') {
			steps {
				echo 'Testing'
				sh 'npm test'
			}
		}
	}
		post {
			success {
            			echo 'Test success!'
			}
			failure {
        			emailext attachLog: true,
        			body: "Error is in ${env.BUILD_URL}",  
        			subject: "Failed Pipeline: ${currentBuild.fullDisplayName}", 
        			to: 'julaa.mat@gmail.com'
    		}
	}
	
}
