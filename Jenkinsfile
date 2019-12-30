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
				sh "docker-compose up --no-color -d hub chrome firefox book-flight-module search-module"
			}
		}
		}
    }

