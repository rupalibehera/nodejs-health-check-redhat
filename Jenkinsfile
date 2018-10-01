#!/usr/bin/groovy
@Library('github.com/fabric8io/osio-pipeline@master')_

osio {

  config runtime: 'node'

  ci {
    echo "Test CI changes"
    sh 'npm install'
    sh 'npm test'
  }

  cd {

    def resources = processTemplate(params: [
          release_version: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources, commands: """
          npm install
          npm test
    """

    deploy resources: resources, env: 'stage'

  }
}
