pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M396" and add it to the path.
        maven "M396"
    }

    stages {
        stage('Maven Version') {
            steps {
                sh "echo Print Maven Version"
                sh "mvn -version"
            }
        }
        
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
               git branch: 'main', url: 'http://localhost:3000/siddharth/jenkins-hello-world.git'

                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Test') {
            steps {
                sh "mvn clean test"
            }
        }
        
    }
}
