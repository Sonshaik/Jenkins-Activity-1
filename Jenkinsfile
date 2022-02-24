pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java'
    }

    stages {
        stage('Build_S') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test_S') {
            steps {
                wrap([$class: 'Xvfb', debug: true, displayName: 12, displayNameOffset: 0, timeout: 15]) {
                    sh 'mvn test'
                }
            }
        }
        stage('Report_S') {
            steps {
                step([$class: 'Publisher'])
            }
        }
        stage('Post_Actions') {
            steps {
                echo 'Tests finished'
            }
        }
    }
}
