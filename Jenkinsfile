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

  
    }
    
    post{
    	always{
    	mail to: 'elgbourihaytam@gmail.com',
    	subject:"notif de l'état : ${env.BUILD_URL}",
    	body:"votre build est accompli : ${env.BUILD_URL}"
    	}
    }
}

