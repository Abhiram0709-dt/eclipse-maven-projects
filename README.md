required plugins are :
copy artifacts to send all files **/* in first mavenjava job
Build Pipeline plugin for viewing the pipeling
for script:
pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Abhiram0709-dt/eclipse-maven-projects'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
}
