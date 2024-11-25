pipeline {
	agent any
	environment {
		DOCKER_IMAGE = 'hello-world-java:latest'
	}
	stages {
		stage('Checkout') {
			steps {
				checkout scm
			}
		}
		stage('Build') {
			steps {
				sh 'javac HelloWorld.java'
				sh 'jar cf HelloWorld.jar HelloWorld.class'
			}
		}
		stage('Docker Build') {
			steps {
				sh """
				docker build -t $DOCKER_IMAGE .
				"""
			}
		}
	}
	post {
		success {
			echo 'Build completed sucessfully.'
		}
		failure {
			echo 'Build failed.'
		}
	}
}
