pipeline {
  agent any
  stages {
    stage('Preporation') {
      steps {
        input(message: 'What you want me to do ?', id: 'preporation')
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
      parallel {
        stage('Publish Release') {
          steps {
            echo 'Publish Release'
          }
        }
        stage('Publish 2') {
          steps {
            echo 'Promote'
          }
        }
        stage('Publish 3') {
          steps {
            echo 'Another message'
          }
        }
      }
    }
    stage('Promote to dev-int') {
      steps {
        echo 'Promote to dev-int'
      }
    }
  }
}