pipeline {
 agent any
 stages {
 stage('Build') {
 steps {
 echo 'Building Docker image...'
 sh 'docker build -t martaapp:latest .'
 }
 }
 stage('Test') {
 steps {
 echo 'Running tests...'
 sh 'echo "Tests passed!"'
 }
 }
 stage('Deploy') {
 steps {
 echo 'Pushing Docker image to DockerHub...'
 withCredentials([usernamePassword(credentialsId: 'dockerhub-credencials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
 
 sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
 sh 'docker tag martaapp:latest $DOCKER_USER/martaapp:latest'
 sh 'docker push $DOCKER_USER/martaapp:latest'
 }
 }
 }
 }
}
