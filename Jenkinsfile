node {
   stage('SCM Checkout'){
	git 'https://github.com/venki2211/javaparser-maven-sample'
   }
   stage('Compile-Package'){
	   // Get maven home path 
	   def mvnHome = tool name: 'maven-3', type: 'maven'
	   sh "${mvnHome}/bin/mvn package"
   }
}
