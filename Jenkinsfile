pipeline {
	agent any
	stages {
		stage("Infrastructure Build") {
			steps {
				echo "Terraform initialization started..."
				echo "git pull github.com/infra_code.git"
				echo "Terraform initialization complete!"
			}
		}
		stage("Infrastructure Deploy"){
			steps {
				echo "Terraform deployment started..."
				cd scripts
				sh infra_script.sh
				echo "Terraform deployment complete!"
			}
		}
		stage("Application Build"){
			steps {
				echo "git pull github.com/application_code.git"
				echo "Application code ready!"
			}
		}
		stage ("Application Deploy") {
			steps {
				echo "Application deployement started..."
				cd scripts
				sh app_script.sh
				echo "Application deployment complete!"
			}
		}
	}
}
