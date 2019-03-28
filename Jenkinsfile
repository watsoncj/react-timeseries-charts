@Library('common-jenkins@1.7.11') _

timestamps {
    ansiColor('xterm') {
        def safeBranchName = env.BRANCH_NAME.replaceAll("\\W+", "");
        def wsName = "${safeBranchName}_${env.BUILD_ID}"
        slave('centos7aws', '8.12.0', wsName) {
            stage('Checkout') {
                shell "git checkout ${env.BRANCH_NAME}"
            }

            stage('Install') {
              shell 'npm install'
            }


            stage('Publish') {
              npm.publish()
            }
        }
    }
}
