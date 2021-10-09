@Library('piper-lib-os') _
node() {
    stage('prepare') {
        checkout scm
        setupCommonPipelineEnvironment script:this
    }
    stage('build') {
        mtaBuild script: this
    }
    stage('deploy') {
        cloudFoundryDeploy(
            script: script,
            deployType: 'blue-green',
            cloudFoundry: [apiEndpoint: 'https://api.cf.us10.hana.ondemand.com', appName:'cfAppName', credentialsId: 'cfCredentialsId', manifest: 'cfManifest', org: 'bd4bb13etrial', space: 'dev'],
            deployTool: 'cf_native'
        )
    }
}
