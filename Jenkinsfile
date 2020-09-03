pipeline {
    agent { docker 'maven:3.5-alpine'}
    stages {
        stage('Checkout'){
            steps{
                git 'https://github.com/rachit2501/spring-petclinic'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
                junit '**/target/surefire-reports/Test-*.xml'
            }
        }
    }
}
