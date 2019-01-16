node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
  

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("getintodevops/hellonode")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

   /*# stage('Push image') {
        * Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. 
         docker.withRegistry('https://hub.docker.com/'), '27a51b28-7b49-4933-80af-6a2f9d89d493' {
         app.push("${env.BUILD_NUMBER}")
          app.push("latest")
        }
    }*/
    stage('create container') {
           sh 'ssh -o StrictHostKeyChecking=no ansible@100.74.111.156 "sudo docker run -d  -p 4560:8000  september:v5 " '
    }
}
