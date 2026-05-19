pipeline {
agent any
tools {
maven 'Maven'
jdk 'JDK'
}
stages {
stage('Checkout') {
steps {
git branch: 'master', url: 'https://github.com/Harshini-Medha/gradle_1BI24CS405_Final'
}
}
stage('Build') {
steps {
sh 'mvn clean package'
}
}
stage('Test') {
steps {
sh 'mvn test'
}
}
stage('Run Application') {
steps {

sh 'java -jar app/build/libs/app.jar'
}
}
}
post {
success {
echo 'Build and deployment successful!'
}
failure {
echo 'Build failed!'
}
}
}
