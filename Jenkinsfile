pipeline {

    agent any
    stages {

        stage('Checkout Codebase1'){
            steps{
                cleanWs()
                //checkout scm: [$class: 'GitSCM', branches: [[name: '*/main']],userRemoteConfigs:
                //[[ url: 'git@github.com:blueventuretech/junit-automation.git']]]

                 git branch: 'main', credentialsId: 'how2coding_github_token', url: 'https://github.com/blueventuretech/junit-automation.git'
            }
        }

        stage('Build'){
            steps{
                sh 'mkdir lib'
                sh 'cd lib/ ; wget https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.7.0/junit-platform-console-standalone-1.7.0-all.jar'
                sh 'cd src ; javac -cp "../lib/junit-platform-console-standalone-1.7.0-all.jar" CarTest.java Car.java App.java'
            }
        }
/*
        stage('Test'){
            steps{
                sh 'cd src/ ; java -jar ../lib/junit-platform-console-standalone-1.7.0-all.jar -cp "." --select-class CarTest --reports-dir="reports"'
                junit 'src/reports/*-jupiter.xml'
            }
        }

        stage('Deploy'){
            steps{
                sh 'cd src/ ; java App' 
            }
        }
        */
    }

}