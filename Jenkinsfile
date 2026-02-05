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
		        bat 'mvn sonar:sonar -Dsonar.projectKey=demo -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqa_1b790f3e22887a726ddee53b77049abecc9d50fa'
		    }
		}

    }
}
