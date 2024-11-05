pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // This triggers the job every minute to check for SCM changes; adjust as needed
    }


    stages {
        stage("Compilation") {
            steps {
                sh "./gradlew compileJava" // Compiles Java source files
            }
        }

        stage("Tests unitaires") {
            steps {
                sh "./gradlew test" // Runs unit tests
            }
        }

        stage("Couverture de code") {
            steps {
                sh "./gradlew jacocoTestReport" // Generates a JaCoCo code coverage report
                publishHTML(target: [
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: "Rapport JaCoCo"
                ])
                sh "./gradlew jacocoTestCoverageVerification" // Verifies code coverage metrics
            }
        }
    }
}

