pipeline {
    agent any
    stages {    
        stage("Compilation") {
            steps {
                sh "./gradlew compileJava"
            }
        }
        
        stage("Unit Testing") {
            steps {
                sh "./gradlew test"
            }
        }
        
    }
}

