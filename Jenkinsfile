#!/usr/bin/env groovy

node {


		def branch = env.BRANCH_NAME
		def imageName = 'user-management'
		def imageTag = ''

		stage('PREPARATION') {
			// Delete all images, which have been built before!
			sh returnStatus: true, script: 'docker rmi -f $(docker images -q)'

			// Setup Java
			env.JAVA_HOME="${tool 'Java8'}"
			env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
			sh 'java -version'

			// Checkout branch
			// Need to set LocalBranch extension, since: https://stackoverflow.com/questions/44006070/jenkins-gitscm-finishes-the-clone-in-a-detached-head-state-how-can-i-make-sure
			checkout([$class: 'GitSCM',
				branches: [
					[
						name: "*/$branch"
					]
				],
				doGenerateSubmoduleConfigurations: false,
				extensions: [],
				extensions: [
					[$class: 'CleanBeforeCheckout'],
					[$class: 'LocalBranch', localBranch: "**"]
				],
				submoduleCfg: [],
				userRemoteConfigs: [
					[
						credentialsId: '314bae8b-b71a-42d7-955b-0d4d1e7ae67e',
						url: 'https://github.com/somedayiws/node.git'
					]
				]
			])
		}

}
