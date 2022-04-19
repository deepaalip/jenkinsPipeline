pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '"BUILD STAGE"'
                sh 'rm -rf build'
                sh 'mkdir build'
                sh 'touch build/demo-build.txt'
                sh 'echo "code build" >> build/demo-build.txt'
                sh 'echo "environment" >> build/demo-build.txt'
                sh 'echo "variables" >> build/demo-build.txt'
            }
        }
        stage('Test') {
            steps {
                echo '"TEST STAGE"'
                sh 'test -f build/demo-build.txt'
                sh 'grep "code build" build/demo-build.txt'
                sh 'grep "environment" build/demo-build.txt'
                sh 'grep "variables" build/demo-build.txt'
            }
        }
        stage('Publish') {
            steps {
                echo '"PUBLISH STAGE"'
                archiveArtifacts artifacts: 'build/'
            }
        }
    }
}
