pipeline {
	agent any

	stages {
		// This is a single-line comment added for testing purposes
		/*
		stage('Build') {
			agent {
				docker {
					image 'node:18-alpine'
					reuseNode true
				}
			}
			steps {
				sh '''
					ls -al
					node --version
					npm --version
					npm ci
					npm run build
					ls -al
				'''
			}
		}
		*/
		stage('Test') {
			agent {
				docker {
					image 'node:18-alpine'
					reuseNode true
				}
			}
			steps {
				sh '''
					ls -l ./build
					# ls -lhrt build | grep 'index.html'
					npm test
				'''
			}
		}
	}

	post {
		always {
			junit 'test-results/junit.xml'
		}
	}
}
