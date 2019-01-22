#!/usr/bin/groovy
@Library('github.com/rupalibehera/osio-pipeline@pod_template') _

osio {

  config runtime: 'node'

  ci {

    echo "Test CI....."

    runTest commands: 'npm install && npm test'

  }

  cd {
    echo "Test CD"

    def resources = processTemplate(params: [
          release_version: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources
    
    deploy resources: resources, env: 'stage'

    deploy resources: resources, env: 'run', approval: 'manual'
  }
}
