def props = [[$class: 'ParametersDefinitionProperty', parameterDefinitions: [
            [$class: 'BooleanParameterDefinition', name: 'Force include CI stages', defaultValue: false, description: "Force execution of IT tests?"],
            [$class: 'BooleanParameterDefinition', name: 'Create Release Build', defaultValue: false, description: "Force creation of docker image on this branch, also automatically increases version. Use this to create new builds from any branch beside develop."],
            [$class: 'BooleanParameterDefinition', name: 'Skip IT steps', defaultValue: false, description: "Skip IT stage?"],
            [$class: 'BooleanParameterDefinition', name: 'Do not skip build', defaultValue: false, description: "Do not skip build even if last commit contains ignore CI prefix"],
            [$class: 'BooleanParameterDefinition', name: 'Increment major version', defaultValue: false, description: "Increment major release version. Use this after promoting develop to staging."]
    ]]]

properties(props)
pipeline = new Pipeline()

try {
  stage('Build') {
      pipeline.compile()      
      pipeline.ut()
      pipeline.sonar()
  }
  stage('Deploy RC') {
    pipeline.publishReleaseCandidate()
    pipeline.deployReleaseCandidate()
  }
  stage('IT RC') {
    pipeline.it()
  }
  stage('Promote RC') {
    pipeline.promoteReleaseCandidate()
    pipeline.publish()
    pipeline.deploy()
    
    echo("Publish Release Artifacts")
    
  }
} catch (err) {
    currentBuild.result = 'FAILURE'
    throw err
}

class Pipeline {
            def compile() {
                        echo('Compile source code')
            }            
            def ut() {
                        // echo("Run Unit Tests")
            }
            def sonar() {
                        // echo("Run Sonar scan")
            }
            def publishReleaseCandidate() {
                        // echo("Publish Release Candidate Artifacts")
            }
            def deployReleaseCandidate() {
                        // echo("Deploy Release Candidate")
            }
            def it() {
                         // echo("IT run on Release Candidate")
            }
            def promoteReleaseCandidate() {
                        // echo("Promote release candidate to release")
            }
            def publish() {
                        // echo("Publish release artifacts")
            }
            def deploy() {
                        // echo("Deploy Release on dev-int")
            }
           
}
