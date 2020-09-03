pipeline {
    agent { label 'linux' }
    stages {
        stage('Checkout'){
            steps{
                git 'https://github.com/rachit2501/spring-petclinic'
            }
        }
        stage('Build'){
            agent {docker 'maven:3.5-alpine'}
            steps{
                sh 'mvn clean package'
                junit '**/target/surefire-reports/Test-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerptint: true
            }
        }
        stage('Deploy'){
            steps {
                input 'Do you approve the deploymment'
                sh 'scp target/*.jar jenkins@192.168.50.10:/opt/pet'
                ssh "ssh jenkins@192.168.50.10 'nohup java -jar /opt/pet/spring-petclinic-1.5.1.jar &'"
            }
        }
    }
}
 