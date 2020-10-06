pipeline {
    agent any
    stages {
        stage('Download') {
            steps {
                git 'https://github.com/dpalomero-stratio/HolaMundo.git'
                echo 'llega'
            }
        }
        stage('Compile') {
            steps {
               dir("Hola_Mundo/src/Prueba") {
                    sh 'javac hola.java'
                    sh 'jar -cfm hola.jar manifest.mf hola.class'
                }
                echo 'compila'
            }
        }
        stage('Generate') {
            steps {
                dir("Hola_Mundo/src/Prueba") {
                    sh 'docker build -t holaj:prueba .'
                }
                echo 'genera'
            }
        }
        stage('Ejecute') {
            steps {
                dir("Hola_Mundo/src/Prueba") {
                    sh 'docker run -d --name "holamundo" holaj:prueba'
                    sh 'docker logs holamundo'
                }
                echo 'ejecuta'
            }
        }
    }
}
