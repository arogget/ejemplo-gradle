// pipeline {
//     agent any
//     environment {
//         NEXUS_USER         = credentials('useradminnexus')
//         NEXUS_PASSWORD     = credentials('userpasswordnexus')
pipeline {
    agent any
    environment {
        NEXUS_USER         = credentials('useradminnexus')
        NEXUS_PASSWORD     = credentials('userpasswordnexus')
    }
    parameters {
        choice(
            name:'compileTool',
            choices: ['Maven', 'Gradle'],
            description: 'Seleccione herramienta de compilacion'
        )
    }
    stages {
        stage("Pipeline"){
            steps {
                script{
                  switch(params.compileTool)
                    {
                        case 'Maven':
                            def ejecucion = load 'maven.groovy'
                            ejecucion.call()
                        break;
                        case 'Gradle':
                            def ejecucion = load 'gradle.groovy'
                            ejecucion.call()
                        break;
                    }
                }
            }
        }
    }
}