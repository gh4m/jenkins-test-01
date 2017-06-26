#!/usr/bin/groovy
@Library('jenkins-test-lib') import static org.foo.Zot.*

node {
   stage("Example Stage") {
     sh 'pwd'
     sh 'mkdir -p build/files'
     createFile "build/files/lib-output.txt"
     sh 'env > build/files/env-output.txt'
   }
}
