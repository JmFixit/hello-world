def props = [[$class: 'ParametersDefinitionProperty', parameterDefinitions: [
            [$class: 'BooleanParameterDefinition', name: 'force_include_ci_stages', defaultValue: false, description: "Force execution of IT tests?"],
            [$class: 'BooleanParameterDefinition', name: 'create_docker_build', defaultValue: false, description: "Force creation of docker image on this branch, also automatically increases version. Use this to create new builds from any branch beside develop."],
            [$class: 'BooleanParameterDefinition', name: 'skip_it_tests', defaultValue: false, description: "Skip IT stage?"],
            [$class: 'BooleanParameterDefinition', name: 'dont_skip_build', defaultValue: false, description: "Do not skip build even if last commit contains ignore CI prefix"],
            [$class: 'BooleanParameterDefinition', name: 'inc_release_ver', defaultValue: false, description: "Increment release version. Use this after promoting develop to staging."]
    ]]]

properties(props)

try {
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
