pipeline {
    agent any

    tools {
        gradle 'Gradle'    // Must match Jenkins tool name
        jdk 'JDK'          // Must match Jenkins tool name
    }

    environment {
        // Optional: set environment variables
        JAVA_OPTS = "-Xmx1024m"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                git branch: 'master', url: 'https://github.com/Harshini-Medha/gradle_1BI24CS405_Final'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'gradle build --stacktrace --info'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'gradle test --stacktrace'
                // Publish test results to Jenkins
                junit '**/build/test-results/test/*.xml'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'build/libs/app.jar', fingerprint: true
            }
        }

        stage('Run Application (Optional)') {
            steps {
                echo 'Running application...'
               
                sh 'gradle run'
            }
        }
    }

    post {
        success {
            echo 'Build, tests, and artifacts completed successfully!'
        }
        failure {
            echo 'Build failed. Check the logs!'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}pipeline {
agent any
tools {
gradle 'Gradle'
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
