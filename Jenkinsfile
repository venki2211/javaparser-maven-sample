node {
   stage('SCM Checkout'){
	git 'https://github.com/venki2211/maven-sample'
   }
   stage('Compile-Package'){
	   // Get maven home path 
	   def mvnHome = tool name: 'maven', type: 'maven'
	   sh "${mvnHome}/bin/mvn package"
   }
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven', type: 'maven'
        withSonarQubeEnv('sonarserver') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
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

