pipeline {

    agent any
       stages {
		stage('clone code') {
			steps {
				git url: "https://github.com/gsrkramkrishna/${params.service}"
			}
		}
		stage('build code') {
			steps {
				bat label: '', script: 'mvn clean install'
			}
		}
		stage('build image') {
			steps {
				bat label: '', script: "docker build -t gsrkramkrishna/${params.service}:%BUILD_NUMBER% ."
			}
		}
		
		stage('push image') {
			steps {
				bat label: '', script: "docker push gsrkramkrishna/${params.service}:%BUILD_NUMBER%"
			}
		}
	}
}
