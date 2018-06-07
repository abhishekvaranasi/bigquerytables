pipeline {
	agent none
	stages {

		stage("Infrastructure Build") {
			agent { label "master" }
			steps {
				echo "Terraform initialization started..."
				echo "git pull github.com/infra_code.git"
				echo "Terraform initialization complete!"
			}
		}
		stage ("Infrastructure Deploy"){
			agent { label "master" }
			steps {
				echo "Terraform deployment started..."
				bat "cd scripts"
				sh "scripts/infra_script.sh"
				echo "Terraform deployment complete!"
			}
		}
		stage ("Application Build"){
			agent { label "Slave node" }
			steps {
				echo "git pull github.com/application_code.git"
				echo "Application code ready!"
			}
		}

		stage ("Application Deploy") {
			agent { label "Slave node" }
			steps {
				echo "Application deployement started..."
				bat "cd scripts"
				sh "scripts/app_script.sh"
				echo "Application deployment complete!"
				}
			}
		}
}

