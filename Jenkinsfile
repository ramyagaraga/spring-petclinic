node('node1') {

    stage('vcs')
    {
        git url: 'https://github.com/ramyagaraga/spring-petclinic.git',
            branch: 'main'

    }
    stage('Build')
    { 
        sh './mvnw package'
        
    }
}