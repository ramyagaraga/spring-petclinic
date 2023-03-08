pipeline {
    agent { label 'node1'} 
    triggers { pollscm ('* * * * *') } 
    parameters {
        choice(name: 'MAVEN_GOAL', choices: ['package', 'install', 'clean'], description: 'Maven Goal')
    }
    stages {
        stage('vcs') { 
            steps {
                git url: 'https://github.com/ramyagaraga/spring-petclinic.git',
                    branch: 'sonar'

            }
        }
        stage('Build') { 
            steps {
                sh './mvnw package'
            }
        } 
        stage('sonal analysis') {
            steps { 
                "withSonarQubeEnv(<Name of server configured in jenkins)" 
                     withSonarQubeEnv('sonar') {
                         sh 'mvn clean package sonar:sonar -Dsonar.organization=sonar-ramya'
                     } 

            }
        } 
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar',
                                 onlyIfSuccessful: true 
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}