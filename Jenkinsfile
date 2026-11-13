pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'scp /root/.jenkins/workspace/flipkarts_clone/target/flipkarts.war root@172.31.29.66:/root/tomcat/apache-tomcat-10.1.61/webapps'
	}
    }
}
}
