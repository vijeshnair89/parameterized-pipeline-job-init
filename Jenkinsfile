
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(branch: 'main', url: 'http://localhost:3000/siddharth/jenkins-hello-world.git')
        sh 'mvn clean package -DskipTests=true'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn clean test'
        junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
      }
    }
    
    stage('Containerization') {
      steps {
        sh 'echo Docker Build Image..'
        sh 'echo Docker Tag Image....'
        sh 'echo Docker Push Image......'
      }
    }

    stage('Kubernetes Deployment') {
      steps {
        sh 'echo Deploy to Kubernetes using ArgoCD'
      }
    }
    
    stage('Integration Testing') {
      steps {
        sh 'sleep 15s'
        sh 'echo Testing using cURL commands......'
      }
    }
  }
  tools {
    maven 'M396'
  }

}
