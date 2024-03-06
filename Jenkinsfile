pipeline {
    
	agent any	
	tools {
        maven "maven3"
        jdk "java8"
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 
        NEXUS_PASS = "sandeep"
        RELEASE_REPO = "vprofile-release"
	    CENTRAL_REPO  = "vprofile-maven-cental"
        NEXUSIP = '172.31.17.170'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-group'
        NEXUS_LOGIN = 'nexuslogin'
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }     
    }


}

        

