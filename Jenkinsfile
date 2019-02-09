pipeline {
  agent {
    label "jenkins-maven"
  }
  environment {
    ORG = 'ssathi'
    APP_NAME = 'jx-spring-demo'
    CHARTMUSEUM_CREDS = credentials('jenkins-x-chartmuseum')
  }
  stages {
    stage('Promote to Environments') {
      when {
        branch 'master'
      }
      steps {
        container('maven') {
          sh "jx step split monorepo -o ssathi --glob "spring" "
        }
      }
    }
  }
  post {
        always {
          cleanWs()
        }
  }
}
