pipeline{
	agent any

	tools{
		maven 'LOCAL_MAVEN'
	}

	stages{

		stage('Build'){
			steps{
				sh 'mvn clean package'
				sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
			}
			post{
				success{
					echo 'Application Docker image built Successfully!'
					echo 'Starting Docker Container'
					sh "docker run -d -p 9${env.BUILD_ID}9${env.BUILD_ID}:8080 tomcatwebapp:${env.BUILD_ID}"
					echo "Docker Container started successfully at port : 8${env.BUILD_ID}8${env.BUILD_ID}"
					echo '9"${env.BUILD_ID}-1"9"${env.BUILD_ID}-1"'
				}
				failure{
					echo 'Deployment Failed!'
				}
			}
		}
	}
}
