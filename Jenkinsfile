pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git(url: 'https://github.com/clamismagic/DVWA.git', branch: 'master')
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'lab-test'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
