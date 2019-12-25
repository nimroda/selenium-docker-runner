pipeline {
	agent any
	stages {
		stage("Pull Latest Image") {
			steps {
				sh "docker pull nimo1975/selenium-docker"
				//sh "docker pull IL02VLAPP5004.cfrm.dev.local:5000/selenium-docker"
			}
		}
		stage("Start Grid") {
			steps {
				sh "docker-compose up -d --scale hub=1 chrome=4 firefox=4 book-flight-module search-module"
			}
		}
		//stage("Run book-flight-module Test") {
		//	steps {
		//		sh "docker-compose up --no-color book-flight-module"
		//	}
		//}
		//stage("Run search-module Test") {
		//	steps {
		//		sh "docker-compose up --no-color search-module"
		//	}
		// }
		}
		post{
		    always{
		        archiveArtifacts artifacts: 'output/**'
		        sh "docker-compose down"
		    }
		}
    }

