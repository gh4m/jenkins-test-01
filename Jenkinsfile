#!/usr/bin/groovy
@Library('jenkins-test-lib') _

node {
   stage("Example Stage") {
     def z = new org.foo.Pot()
     z.createNewFile(filename1)
     sh 'mkdir -p build/files'
     sh 'env > build/files/env-output.txt'
     archiveArtifacts artifacts: 'build/files/*.txt'
     sayHello 'Joe'
     sayHello() /* invoke with default arguments */
   }
}
