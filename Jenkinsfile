pipeline {
    agent { docker 'python:3.5.1' }
    parameters {
        string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    }
    environment {
        mysecret = credentials('test-secret-id')
        myprintvar = 'mysecret'
    }
    stages {
        stage('build') {
            environment {
                JENKINS_TEST_01 = 'jenkins 01'
                JENKINS_TEST_02 = 'jenkins 02'
            }
            steps {
                sh 'python --version'
                sh 'ip addr'
                sh 'pwd'
                sh 'mkdir -p build/files'
                sh 'env > build/files/env-output.txt'
            }
        }
        stage('Example') {
            steps {
                echo "${params.Greeting} World!"
            }
        }
    }
    post {
        always {
            archive 'build/files/*'
            mail to: 'fromaws@srmstar.net',
                subject: "ran Pipeline: ${currentBuild.fullDisplayName}",
                 body: "looks okay ${env.BUILD_URL}"
        }
    }
}
