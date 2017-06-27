#!/usr/bin/groovy
@Library('jenkins-test-lib') _

node {
   stage("Example Stage") {
     sh 'mkdir -p build/files'
     sh 'env > build/files/env-output.txt'
     archiveArtifacts artifacts: 'build/files/*.txt'
     def filename1 = 'build/files/src-lib.txt'
     def z = new org.foo.Pot()
     z.createNewFile(filename1)
     sayHello 'Joe'
     sayHello() /* invoke with default arguments */
   }
}
