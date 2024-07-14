pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Specify the correct remote repository URL and potentially credentials
                git url: 'https://github.com/lestertann/JenkinsDependencyCheckTest'
            }
        }

        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
            }
        }
    }   
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
