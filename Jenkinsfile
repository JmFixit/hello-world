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
    publishReleaseCandidate()
    deployReleaseCandidate()
  }
  stage('IT RC') {
    integrationTests()
  }
  stage('Promote RC') {
    promoteReleaseCandidate()
    publish()
    deploy()
  }
} catch (err) {
    currentBuild.result = 'FAILURE'
    throw err
}


def compile() {
            echo('Compile source code')
}            
def unitTests() {
            echo("Run Unit Tests")
}
def sonar() {
            echo("Run Sonar scan")
}
def publishReleaseCandidate() {
            echo("Publish Release Candidate Artifacts")
}
def deployReleaseCandidate() {
            echo("Deploy Release Candidate")
}
def integrationTests() {
            echo("IT run on Release Candidate")
}
def promoteReleaseCandidate() {
            echo("Promote release candidate to release")
}
def publish() {
            echo("Publish release artifacts")
}
def deploy() {
            echo("Deploy Release on dev-int")
}
