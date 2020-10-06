node {
    stage('Download') {
        git 'https://github.com/dpalomero-stratio/HolaMundo.git'
        echo 'llega'
    }
    stage('Compile') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'javac hola.java'
            sh 'jar -cfm hola.jar manifest.mf hola.class'
        }
        echo 'compila'
    }
    stage('Generate') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'docker build -t holaj:prueba .'
        }
        echo 'genera'
    }
    stage('Anchore') {
        //def imageLine = 'docker.io/hello-world'
        writeFile file: 'anchore_images', text: 'holaj:prueba'
        anchore name: 'anchore_images'
        echo 'prueba anchore'
    }
    /*stage('Ejecute') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'docker run -d --name "holamundo" holaj:prueba'
            sh 'docker logs holamundo'
        }
        echo 'ejecuta'
    }*/
}