pipeline{

    agent any

    stages{

        stage("Continous Download") {

            steps{
                git branch: 'main', url: 'https://github.com/Hadijah-ateh/DEVOPS-PROJECT-4.git'
            }
        }
        stage('Intergration Testing'){

            steps{
                sh 'mvn verify -DskipUnitTest'
            }
        }
        stage('Unit Testing'){

            steps{
                sh 'mvn test'
            }
        }
        stage('Static Test Analysis'){

            steps{

                script{
                    withSonarQubeEnv(credentialsId: 'sonarqube-token'){
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}