pipeline {
    
	agent any	
	tools {
        maven "3.9.6"
        jdk "java8"
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'sandeep'
        RELEASE_REPO = "vprofile-release"
	    CENTRAL_REPO  = "vprofile-maven-cental"
        NEXUSIP = '172.31.17.170'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-group'
        NEXUS_LOGIN = 'nexuslogin'
	SONARSERVER = 'sonarserver'
	SONARSCANNER = 'sonarscanner'
    }
	
    stages {
        stage('BUILD') {
            steps {
                sh 'mvn clean install -DskipTests'
            }

              }
       stage('Sonar Analysis') {
        environment {
            scannerHome = tool "${SONARSCANNER}"
        steps {
            withSonarQubeEnv("${SONARSERVER}") {

            } sh '''${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
                   -Dsonar.projectName=vprofile-repo \
                   -Dsonar.projectVersion=1.0 \
                   -Dsonar.sources=src/ \
                   -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/ \
                   -Dsonar.junit.reportsPath=target/surefire-reports/ \
                   -Dsonar.jacoco.reportsPath=target/jacoco.exec \
                   -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
	}

        }
       }
	    
      }
	
}
