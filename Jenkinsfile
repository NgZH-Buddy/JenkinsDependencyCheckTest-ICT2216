pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/NgZH-Buddy/JenkinsDependencyCheckTest-ICT2216'
				git credentialsId: '13cbfc6c-7216-4c57-8cbe-d5efd67fb076', url: 'https://github.com/NgZH-Buddy/JenkinsDependencyCheckTest-ICT2216'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}