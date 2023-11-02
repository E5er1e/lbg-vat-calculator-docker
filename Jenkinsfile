pipeline{
environment{
registry = "emilyserle1912/vatcal"
registryCredentials = "dockerhub_id"
dockerImage = ""
}
agent any
stages {
stage('Build Docker Image'){
steps{
script{
dockerImage = docker.build(registry)
}
}
}

stage("Push to Docker Hub")}
steps {
script {
docker.withRegistry(",registryCregentials){
dockerImage.push("${env.BUILD_NUMBER}")
dockerImage.push("latest")
}
}
}
}

stage("Clean up"){
steps {
script {
sh 'docker image prune --all --force --filter "until=48h"
}
}
}
}
}