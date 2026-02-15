pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat "mvn clean install"
            }
        }
        stage('Test') {
		    steps {
		        bat 'mvn test'
		    }
		}
		stage('SonarQube Analysis') {
		    steps {
		        bat 'mvn sonar:sonar -Dsonar.projectKey=demo -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqa_af514370898dd2141842e76e86ddd4538844edc5'
		    }
		}// decommenter le sonar stage (refaire)

    }
}
