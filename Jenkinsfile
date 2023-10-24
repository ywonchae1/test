node {
def app
stage('Clone repository') {
git 'https://github.com/ywonchae1/test'
}
stage('Build image') {
app = docker.build("ywonchae1/opensource")
}
stage('Test image') {
app.inside {
sh 'echo 1234'
}
}
stage('Push image') {
docker.withRegistry('https://registry.hub.docker.com', 'ywonchae1') {
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}
}
}