pipeline {
    agent any
    triggers{
        pollSCM('* * * * *')
    }
    
    tools{
            maven 'maven-3'
            jdk 'java11'
    }
    //Nothing Interesting Happening
    stages {
        stage('clean')
        {
            steps{
            sh 'mvn clean'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    
                        sh 'mvn package sonar:sonar'
                    
                }
            }
        }
    }
    
}
