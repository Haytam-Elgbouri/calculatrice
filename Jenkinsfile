pipeline {
    agent any

    triggers {
        pollSCM('*****')
    }

    stages {
        stage("Compilation") {
            steps {
                sh "./gradlew compileJava"
            }
        }

        stage("Tests unitaires") {
            steps {
                sh "./gradlew test"
            }
        }

        stage("Couverture de code") {
            steps {
                sh "./gradlew jacocoTestReport"
                publishHTML(target: [
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: "Rapport JaCoCo"
                ])
                sh "./gradlew jacocoTestCoverageVerification"
            }
        }
    }
}

