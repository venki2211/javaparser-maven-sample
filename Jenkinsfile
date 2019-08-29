pipeline {
    agent any
    
    stages {
        stage ('Package Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
