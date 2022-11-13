pipeline {
environment {
registry = "mohamedaitlahcen/tp4"
registryCredential = 'dockerHub'
dockerImage = ''
}
agent any
stages {
stage('Cloning Git') {
steps {
git([url: 'https://github.com/mohamed-ait/tp4DevOps.git', branch: 'main',credentialsId:'GitCredential'])
}
}
stage('Building image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Test image') {
steps{
script {
echo "Tests passed" 
}
}
}
stage('Publish Image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
stage('Deploy image') {
steps{
bat "docker run -d $registry:$BUILD_NUMBER"
}
}
}
}

 
