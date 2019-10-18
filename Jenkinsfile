pipeline {
  agent any
  stages {
    stage('Preporation') {
      steps {
        input(message: 'What you want me to do ?', id: 'preporation', ok: 'a,b,c,d,e')
      }
    }
    stage('Compile') {
      steps {
        echo 'Compiling code'
      }
    }
    stage('UT') {
      steps {
        echo 'UT Tests'
      }
    }
    stage('Sonar') {
      steps {
        echo 'Sonar'
      }
    }
    stage('Publish RC') {
      steps {
        echo 'Prepare Release Candidate'
      }
    }
    stage('Deploy RC') {
      steps {
        echo 'Deploy RC'
      }
    }
    stage('Publish Release') {
      steps {
        echo 'Publish Release'
      }
    }
    stage('Promote to dev-int') {
      steps {
        echo 'Promote to dev-int'
      }
    }
  }
}