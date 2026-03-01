pipeline {
  agent any
  tools { maven 'M3' }
  stages {
    stage('Build') {
      steps {
        git branch: 'master', url: 'https://github.com/mammar1-csc/simple-maven-project-with-tests.git'
        sh 'mvn -Dmaven.test.failure.ignore=true clean package'
      }
    }
  }
  post {
    always {
      junit 'target/surefire-reports/*.xml'
      archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
    }
  }
}
