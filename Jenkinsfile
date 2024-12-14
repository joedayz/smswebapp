pipeline {
    agent any

    environment {
        PATH = "/usr/local/share/dotnet:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

    stage('SonarQube Analysis') {
        def scannerHome = tool 'SonarScanner for MSBuild'
        withSonarQubeEnv() {
          sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"scandotnetwithjenkins\""
          sh "dotnet build"
          sh "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
        }
    }
    
}
