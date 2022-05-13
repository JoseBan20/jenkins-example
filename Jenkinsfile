pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                   bat 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    bat 'mvn test'
                }
            }
        }


           stage ('zap Stage') {
            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    bat 'mvn zap'
                    IF %ERRORLEVEL% EQU 1 (exit /B 0) ELSE (exit /B 1)
                }
            }
               
        }
        
    }
}
