pipeline {
    agent any

    stages {
        stage('Build') {
            stages {
                stage('Build dotnet') {
                    agent {
                        docker {
                            image 'mcr.microsoft.com/dotnet/sdk:7.0'
                            reuseNode true
                        }
                    }
                    steps {
                        echo 'Building dotnet'
                        dotnet build
                    }
                }
                stage('Build npm') {
                    agent {
                        docker {
                            image 'node:17-bullseye'
                            reuseNode true
                        }
                    }
                    steps {
                        echo 'Building npm'
                        npm install
                        npm run build
                    }
                }
            }
        }
    }
}