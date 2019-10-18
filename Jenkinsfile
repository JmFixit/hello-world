def props = [[$class: 'ParametersDefinitionProperty', parameterDefinitions: [
            [$class: 'BooleanParameterDefinition', name: 'Force include CI stages', defaultValue: false, description: "Force execution of IT tests?"],
            [$class: 'BooleanParameterDefinition', name: 'Create Release Build', defaultValue: false, description: "Force creation of docker image on this branch, also automatically increases version. Use this to create new builds from any branch beside develop."],
            [$class: 'BooleanParameterDefinition', name: 'Skip IT steps', defaultValue: false, description: "Skip IT stage?"],
            [$class: 'BooleanParameterDefinition', name: 'Do not skip build', defaultValue: false, description: "Do not skip build even if last commit contains ignore CI prefix"],
            [$class: 'BooleanParameterDefinition', name: 'Increment major version', defaultValue: false, description: "Increment major release version. Use this after promoting develop to staging."]
    ]]]

properties(props)

try {
  stage('Build') {
      compile()      
      unitTests()
      sonar()
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

class Pipeline {
            compile() {
                        echo("Compile source code")  
            }            
            unitTests() {
                        echo("Run Unit Tests")
            }
            sonar() {
                        echo("Run Sonar scan")
            }
}
