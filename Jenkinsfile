pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Pratikshadukare/jenkins.git'
            }
        }
        
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }
        
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'SonarQube Scanner'
            }
            
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=mypro -Dsonar.sources=src -Dsonar.host.url=http://13.233.156.173:9000/ -Dsonar.login=sqa_694797009a10142248780160d4f38a7c018abbfb"
                }
            }
        }
    }
}
