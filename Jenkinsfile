pipeline {
   // 
   agent any
    
    stages {
     
        stage ('Checkout') {
          steps {
                git 'https://github.com/rashidhatami/spring-petclinic.git'
                 }
        }
        stage('Build') {
            agent { docker 'maven:latest' }
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts:'target/*.jar', fingerprint:true
		    }
        }
            stage('Deploy') {
            steps {
                input 'Do you approve the deployment?'
                    sh 'scp target/*.jar jenkins@172.17.0.3:/opt/pet'
                   // sh "ssh jenkins@172.17.0.3 'nohup java -jar /opt/pet/spring-petclinic-1.5.1.jar &'"
               
		    }
        }

    }
}

