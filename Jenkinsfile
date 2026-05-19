pipeline {
agent any 
tools {
gradle 'Gradle' 
jdk 'JDK'
}
stages {
stage('Checkout') {
steps {
git branch: 'master', url: 'https://github.com/Harshini-Medha/gradle_1BI24CS405_Final.git'
}
}
stage('Build') {
steps {
sh 'gradle build' 
}
}
stage('Test') {
steps {
sh 'gradle test' 
}
}
stage('Run Application') {
steps {
// Start the JAR application
sh 'gradle run'
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
