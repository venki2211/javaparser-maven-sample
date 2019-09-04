node {
   stage('SCM Checkout'){
	git 'https://github.com/venki2211/maven-sample'
   }
   stage('Compile-Package'){
	   // Get maven home path 
	   def mvnHome = tool name: 'maven', type: 'maven'
	   sh "${mvnHome}/bin/mvn package"
   }
   stage('SonarQube analysis') {
	                    withSonarQubeEnv('sonarserver') {
	                        sh  '/opt/sonar-scanner-3.2.0.1227-linux/bin -D sonar.host.url=http://3.219.234.113:9000 -D sonar.login=9d3da743bc7b22699ded27ad934b06c4d3d436e7 -D sonar-project.properties'
	                    }
	                }

	   stage('Slack Notification'){
	   slackSend baseUrl: 'https://hooks.slack.com/services/', 
		   channel: '#sample-project', 
		   color: 'Good', 
		   message: 'Welcome to DXC Slack', 
		   tokenCredentialId: 'slack-secret'
	   }
	   }
   }

