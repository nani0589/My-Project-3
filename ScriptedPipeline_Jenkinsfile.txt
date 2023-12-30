node {
    stage('Download') {
    git branch: 'dev', url: 'https://github.com/nani0589/My-Project-3.git'
                      }
    stage('Convert into Artifacts') {
    sh 'mvn package'
                                    }
    stage('Doploy into Container') {
    deploy adapters: [tomcat9(credentialsId: '2d7c7414-c543-44a9-bf5f-51d421058fee', path: '', url: 'http://35.154.173.181:8080')], contextPath: '/devapp', war: '**/*.war'
                                   }
}
