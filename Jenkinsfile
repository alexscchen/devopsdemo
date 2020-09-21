node {
    stage("CI build"){
        checkout scm

        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-id') {

        def customImage = docker.build("alexchen2015/devopsdemo")

        /* Push the container to the custom Registry */
        customImage.push()
                 }
               } 
    stage(CD Test){
    }
}
