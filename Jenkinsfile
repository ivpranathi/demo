pipeline {
    agent any 

    stages {
        stage('Build') { 
            steps { 
               sh 'xcodebuild -scheme "TimeTable" -configuration "Debug" build test -destination "platform=iOS Simulator,name=iPhone 6,OS=10.0” -enableCodeCoverage YES | /usr/local/bin/xcpretty -r junit' 
            }
        }
        stage('Test'){
            steps {
                step([$class: 'JUnitResultArchiver', allowEmptyResults: true, testResults: 'build/reports/junit.xml']) 
            }
        }
        
    }
}