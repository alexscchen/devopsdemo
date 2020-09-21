stage 'Prep'
node {
}
stage 'Test Approval'
input "Continue?"

node {
    stage("CI build"){
        checkout scm

        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-id') {

        def customImage = docker.build("alexchen2015/devopsdemo")

        /* Push the container to the custom Registry */
        customImage.push()
                 }
               } 
    stage("CD Test"){
       }
    stage("CD Deploy"){
    
        sshPublisher(publishers: [sshPublisherDesc(configName: 'k8smaster', sshCredentials: [encryptedPassphrase: '{AQAAABAAAAAQusq939kGDsy8ol1iLJnXARQtkXZ/bIHAKDBl5fYqrkQ=}', key: '', keyPath: '', username: 'alexchen'], transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'kubectl rollout restart deployment/cdjenkinsdemo', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])  }
    
    }
