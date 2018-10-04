pipeline {
  agent any
  stages {
    stage('Example') {
      steps {
node {
    // Change `url` value to your own
    git url: 'file:////Users/evildethow/workspace/spike/project-w-property-files.git'
    
    def inputParams = inputParamsString(new File(pwd()))
    
    // Change `message` value to the message you want to display
    // Change `description` value to the description you want
    def selectedProperty = input( id: 'userInput', message: 'Choose properties file', parameters: [ [$class: 'ChoiceParameterDefinition', choices: inputParams, description: 'Properties', name: 'prop'] ])
    
    println "Property: $selectedProperty"
    
    // Change `job` value to your downstream job name
    // Change `name` value to the name you gave the string parameter in your downstream job
    build job: 'downstream-freestyle', parameters: [[$class: 'StringParameterValue', name: 'prop', value: selectedProperty]]
}

import static groovy.io.FileType.FILES

@NonCPS
def inputParamsString(dir) {
    def list = []
    
    // If you don't want to search recursively then change `eachFileRecurse` -> `eachFile`
    dir.eachFileRecurse(FILES) {
        // Change `.properties` to the file extension you are interested in
        if(it.name.endsWith('.properties')) {
            // If the full path is required remove `.getName()`
            list << it.getName()
        }
    }
    
    list.join("\n")
}
      }
