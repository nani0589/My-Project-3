node {
    stage('Download') {
    git branch: 'test', url: 'https://github.com/nani0589/My-Project-3.git'
                      }
    stage('Convert into Artifacts') {
    sh 'mvn package'
                                    }
    stage('Doploy into Container') {
    deploy adapters: [tomcat9(credentialsId: 'a2bdccfe-031d-4f93-a4bd-e28d99f50527', path: '', url: 'http://43.204.150.139:8080')], contextPath: '/testapp', war: '**/*.war'
                                   }
}
