pipeline {
    agent { label 'node1'} 
    stages {
        stage('vcs') { 
            steps {
                git url: 'https://github.com/ramyagaraga/spring-petclinic.git
                    branch: 'develop'

            }
        }
    }
}
