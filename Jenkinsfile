try {
  stage('Preporation') {      
    def userInput = input(
      id: 'userInput', message: 'What do you want me to do?', parameters: [
      [$class: 'ChoiceParameterDefinition', name: 'work', defaultValue: 'Build', choices: ['Build', 'Promote']], 
    ])
  }
  stage('Build') {
      echo("Compile")  
  }
  stage('Deploy RC') {
    echo("Publish Release Candidate Artifacts")
    echo("Deploy Release Candidate")
  }
  stage('IT RC') {
    echo("IT run on Release Candidate")
  }
  stage('Promote RC') {
    echo("Promote release candidate to release")
    echo("Publish Release Artifacts")
    echo("Deploy Release on dev-int")
  }
} catch (err) {
    currentBuild.result = 'FAILURE'
    throw err
}
