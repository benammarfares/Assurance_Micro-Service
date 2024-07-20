pipeline {
    agent {
        docker {
            image 'maven'
            args '-u root -v $HOME/.m2:/root/.m2'
        }
    }

    stages {
        stage('Build configServer') {
            steps {
                script {
                    dir('configServer') {
                        sh "mvn compiler:compile"
                        withSonarQubeEnv('sonarserver') {
                            sh 'mvn sonar:sonar'
                        }
                        sh "mvn clean package"
                    }
                }
            }
        }

        stage('Build discoveryServer') {
            steps {
                script {
                    dir('discorveryServer') {
                        sh "mvn compiler:compile"
                        withSonarQubeEnv('sonarserver') {
                            sh 'mvn sonar:sonar'
                        }
                        sh "mvn clean package"
                    }
                }
            }
        }

        stage('Build assurance') {
            steps {
                script {
                    dir('assurance') {
                        sh "mvn compiler:compile"
                        withSonarQubeEnv('sonarserver') {
                            sh 'mvn sonar:sonar'
                        }
                        sh "mvn clean package"
                    }
                    sh 'cd ..'
                }
            }
        }

        stage('Build assurancePolicy') {
            steps {
                script {
                    dir('assurancePolicy') {
                        sh "mvn compiler:compile"
                        withSonarQubeEnv('sonarserver') {
                            sh 'mvn sonar:sonar'
                        }
                        sh "mvn clean package"
                    }
                    sh 'cd ..'
                }
            }
        }

        stage('Build gateway') {
            steps {
                script {
                    dir('gateway') {
                        sh "mvn compiler:compile"
                        withSonarQubeEnv('sonarserver') {
                            sh 'mvn sonar:sonar'
                        }
                        sh "mvn clean package"
                    }
                    sh 'cd ..'
                }
            }
        }
    }
}