pipeline {
    agent { docker 'python:3.5.1' }
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
                sh 'eval echo $$myprintvar'
            }
        }
    }
}
