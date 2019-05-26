// Powered by Infostretch 

timestamps {

node () {

	stage ('SampleProject - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git-login', url: 'https://github.com/tawnydev/jenkins-sample-1/']]]) 
	}
	stage ('SampleProject - Build') {
 			// Maven build step
	withMaven(maven: 'Maven 3.6.0') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		} 
	}
	stage ('Analyse de la qualité'){
		    withMaven(maven: 'Maven 3.6.0') { 
	 			if(isUnix()) {
	 				sh "mvn sonar:sonar \
  						-Dsonar.projectKey=fr.orsys.samples.fr.orsys.samples \
  						-Dsonar.host.url=http://localhost:9000 \
  						-Dsonar.login=f5e2cd355013d251cbe549e9aee323a7b3b77bf4" 
				} else { 
	 				bat "mvn sonar:sonar \
  						-Dsonar.projectKey=fr.orsys.samples.fr.orsys.samples \
  						-Dsonar.host.url=http://localhost:9000 \
  						-Dsonar.login=f5e2cd355013d251cbe549e9aee323a7b3b77bf4" 
				} 
	 		} 		    
		}
	stage ('SampleProject - Post build actions') {
/*
Please note this is a direct conversion of post-build actions. 
It may not necessarily work/behave in the same way as post-build actions work.
A logic review is suggested.
*/
		// Mailer notification
		step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'kevin.matrix@hotmail.fr', sendToIndividuals: false])
 
	}
}
}