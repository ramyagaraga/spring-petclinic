node(node1) {
   
    stage('Build')
    { 
        sh './mvnw package',
        git url: 'https://github.com/ramyagaraga/spring-petclinic.git',
            branch: 'main'

    }
}