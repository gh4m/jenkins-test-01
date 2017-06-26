#!/usr/bin/groovy
@Library('jenkins-test-lib') 
import org.foo.Zot.createFile

def z = new org.foo.Zot()
z.createFile("/tmp/test-jenkins-lib")

pipeline {
    agent { docker 'python:3.5.1' }
    parameters {
        string(name: 'Greeting1', defaultValue: 'Hello1', description: 'How should I greet the declarative world?')
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
                echo "${params.Greeting1} World!"
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
properties([parameters([string(defaultValue: 'Hello2', description: 'How should I greet the script  world?', name: 'Greeting2')])])

node {
    echo "${params.Greeting2} World!"
}
