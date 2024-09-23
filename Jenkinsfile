node ('agent007') {
    def app
    stage ('Cloning Git') {
        checkout scm
    }
    stage ('Build-and-Tag') {
        app = docker.build("cjmydog/sudoku")
    }
    stage ('Post-to-dockerhub') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_login') {
            app.push("latest")
        }
    }
    stage ('Pull-image-server') {
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}
           
