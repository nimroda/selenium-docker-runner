pipeline {
	agent any
	stages {
		stage("Pull Latest Image") {
			steps {
				sh "docker pull nimo1975/selenium-docker"
			}
		}
		stage("Start Grid") {
			steps {
				sh "docker-compose up -d --no-color hub chrome firefox"
			}
		}
		stage("Run Test") {
			steps {
				sh "docker-compose up --no-color book-flight-module search-module"
			}
		}
		}
		post{
		    always{
		        archiveArtifacts artifacts: 'output/**'
		        sh "docker-compose down"
		    }
		}
    }
 



