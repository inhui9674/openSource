node {
	def app
	stage('Clone repository') {
		git 'https://github.com/inhui9674/openSource.git'
	}
	stage('Build image') {
		app = docker.build("yih0322/test")
	}
	stage('Test image') {
		app.inside {
			sh 'make test'
		}
	}
	stage('Push image') {
		docker.withRegistry('https://registry.hub.docker.com', 'yih0322') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}	
}

