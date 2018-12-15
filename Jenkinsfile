// Powered by Infostretch 

timestamps {

node () {

	stage ('jenkins-sample-1 - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-login', url: 'https://github.com/tawnydev/jenkins-sample-1']]]) 
	}
	stage ('jenkins-sample-1 - Build') {
 	
withEnv(["JAVA_HOME=${ tool '"+JDK+"' }", "PATH=${env.JAVA_HOME}/bin"]) { 
		// Maven build step
	withMaven(jdk: 'Java 8', maven: 'Maven 3.5.3') { 
 			if(isUnix()) {
 				sh "mvn clean install package " 
			} else { 
 				bat "mvn clean install package " 
			} 
 		} 
	}
}
}
}