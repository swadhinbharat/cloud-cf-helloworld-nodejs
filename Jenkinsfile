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
        cloudFoundryDeploy script: this
        tmsUpload script:this, verbose: true, nodeName: 'Develop', credentialsId: 'CF_CREDENTIALSID', mtaPath: './com.sap.piper.node.hello.world.mtar', customDescription: 'JobName: '+ env.JOB_NAME+' Build Nr: '+ env.BUILD_NUMBER
    }
}
