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
				sh "docker-compose up --no-color -d hub chrome firefox"
			}
		}
		stage("Run search-module Test") {
			steps {
				//sh "docker-compose up --no-color search-module"
				script {
                    def status = sh(script: "docker-compose up --no-color search-module", returnStatus: true)
					echo $status
                    println("step status = ${status}")
                }
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