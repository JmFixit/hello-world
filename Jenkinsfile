try {
  stage('Preporation') {      
    def work = input(
      id: 'userInput', message: 'What do you want me to do?', parameters: [
      [$class: 'ChoiceParameterDefinition', name: 'choice', defaultValue: 'Build', choices: ['Build (Quick)', 'Build (Release)', 'Promote']], 
    ])
    echo("Value ${work}")
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
