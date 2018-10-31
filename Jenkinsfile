#!/usr/bin/groovy
@Library('github.com/yzainee/osio-pipeline@analytics-plugin')_

osio {

  config runtime: 'node'

  ci {

    def app = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])
    

    build resources: app, commands: """
          npm --version
          oc version
    """
    
  }
  

  cd {

    def resources = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])
   

    build resources: resources, commands: """
         npm --version
         oc version
    """
    

    deploy resources: resources, env: 'stage'

    deploy resources: resources, env: 'run', approval: 'manual'

  }
}
}

