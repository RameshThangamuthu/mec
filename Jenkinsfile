node("docker") {
    docker.withRegistry('https://hub.docker.com/u/rameshthangamuthu/edgepoc', 'DockerHub') {
    
        git url: "https://github.com/RameshThangamuthu/mec", credentialsId: 'GitHub'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
