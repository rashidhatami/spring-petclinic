

 stage('Build') {
            
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml' 
		    }
	}
