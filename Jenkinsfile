#!/usr/bin/groovy
@Library('github.com/fabric8io/osio-pipeline@master')_

osio {

  config runtime: 'node'

  ci {
    echo "Test CI branching from same fork"
    sh 'npm install'
    sh 'npm test'
    def app = processTemplate(params: [
          release_version: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: app
  }

  cd {

    def resources = processTemplate(params: [
          release_version: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources, commands: """
          npm install
          npm test
    """
  }
}
