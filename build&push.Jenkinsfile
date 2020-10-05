node{
    
    environment {
    registry = "incepti0n/intermine_tomcat"
    registryCredential = 'dockerhub'
}
    
    
    stage ('Clone Repository'){
        git url: 'https://github.com/maksym-butusov/Final-task-app-intermine' ,credentialsId: 'jenkins_credentials'
    }

   def app

stage('Build image') {
    /* This builds the actual image; synonymous to
     * docker build on the command line */

    app = docker.build("incepti0n/intermine_builder", "-f intermine_builder/intermine_builder.Dockerfile .")
}

        
/***** PUSH IMAGE STEP ****/     
stage('Push image') {
    /* Finally, we'll push the image with two tags:
     * First, the incremental build number from Jenkins
     * Second, the 'win' tag.
     * Pushing multiple tags is cheap, as all the layers are reused. */
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        app.push("${env.BUILD_NUMBER}")
        app.push("latest")
    }
}
   def app2

stage('Build image') {
    /* This builds the actual image; synonymous to
     * docker build on the command line */

    app2 = docker.build("incepti0n/intermine_postgres", "-f postgres/postgres.Dockerfile .")
}

        
/***** PUSH IMAGE STEP ****/     
stage('Push image') {
    /* Finally, we'll push the image with two tags:
     * First, the incremental build number from Jenkins
     * Second, the 'win' tag.
     * Pushing multiple tags is cheap, as all the layers are reused. */
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        app2.push("${env.BUILD_NUMBER}")
        app2.push("latest")
    }
}
       def app3

stage('Build image') {
    /* This builds the actual image; synonymous to
     * docker build on the command line */

    app3 = docker.build("incepti0n/intermine_solr", "-f solr/solr.Dockerfile .")
}

        
/***** PUSH IMAGE STEP ****/     
stage('Push image') {
    /* Finally, we'll push the image with two tags:
     * First, the incremental build number from Jenkins
     * Second, the 'win' tag.
     * Pushing multiple tags is cheap, as all the layers are reused. */
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        app3.push("${env.BUILD_NUMBER}")
        app3.push("latest")
    }
}
           def app4

stage('Build image') {
    /* This builds the actual image; synonymous to
     * docker build on the command line */

    app4 = docker.build("incepti0n/intermine_tomcat", "-f tomcat/tomcat.Dockerfile .")
}

        
/***** PUSH IMAGE STEP ****/     
stage('Push image') {
    /* Finally, we'll push the image with two tags:
     * First, the incremental build number from Jenkins
     * Second, the 'win' tag.
     * Pushing multiple tags is cheap, as all the layers are reused. */
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        app4.push("${env.BUILD_NUMBER}")
        app4.push("latest")
    }
}    
}
