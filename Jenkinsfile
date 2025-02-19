pipeline {
	agent any

	stages {
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
		stage('Test stage') {
			steps {
				sh '''
					ls -l ./build
					ls -lhrt build | grep 'index.html'
					npm test
				'''
			}
		}
	}
}
