node {
  def commit_id
  stage("Prepration") {
    checkout scm
    sh "git rev-parse --short HEAD > .git/commit-id"
    commit-id = readFile(".git/commit-id").trim()
    }
  stage("docker build/push") {
    docker.withRegistry("https://index.docker.io/v1", "dockerhub") {
      def app = docker.build("multra/docker-hello:${comit_id}", ".").push()
    }
  }
}
