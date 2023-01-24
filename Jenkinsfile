pipeline {
    agent any

    environment {
        DOTNET_CLI_HOME = '/tmp/dotnet_cli_home'
        XDG_DATA_HOME = '/tmp'
    }

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
                        script{
                            npm install
                            npm run build
                        }
                        
                    }
                }
            }
        }
    }
}