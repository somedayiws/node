#!/usr/bin/env groovy

node {

withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
		accessKeyVariable: 'AWS_ACCESS_KEY_ID',
		credentialsId: 'aws',
		secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
		def branch = env.BRANCH_NAME
		def imageName = 'user-management'
		def imageTag = ''

		stage('PREPARATION') {
			// Setup Java
			env.JAVA_HOME="${tool 'Java8'}"
			env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
			sh 'java -version'

			awsId = awsIdentity()

			id = readJSON text: awsId

			println 'id: $id'

		}
	}

}
