    // Change `url` value to your own
    def inputParams=new URL('http://maven.com/sefs/sefs-scm.txt').text    
    
    // Change `message` value to the message you want to display
    // Change `description` value to the description you want
    def selectedProperty = input( id: 'userInput', message: 'Choose properties file', 
        parameters: [ [
          $class: 'ChoiceParameterDefinition', 
          choices: inputParams, 
          description: 'Properties', 
          name: 'prop'] ])
    
    println "Property: $selectedProperty"
