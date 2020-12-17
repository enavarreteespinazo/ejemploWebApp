pipeline{
    agent any
    stages{
        stage('Repositorio'){
            steps{
                echo 'Repositorio clonar'
                git url: 'https://github.com/enavarreteespinazo/ejemploWebApp'
            }
        }
        stage('Empaquetado'){
            steps{
                echo 'Empaqueto mediante maven'
                sh 'mvn package'
            }
        }
        stage('EnviarTomcat'){
            steps{
                echo 'Deploy'
                deploy adapters: [tomcat9(credentialsId: '23f9c33f-591a-4e06-9e75-3395f4774d18', path: '', url: 'http://localhost:8082')], contextPath: 'prueba1', war: 'target/miweb.war'
            }
        }
       
    }
    post{
        always{
              echo 'Me ejecuto siempre'
        }
        success{
              echo 'Me ejecuto success'
        }
        failure{
              echo 'Me ejecuto falla'
        }
        changed{
              echo 'Me ejecuto siempre que la ejecución anterior es diferente a la actual'
        }
    }
}