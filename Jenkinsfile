node {
    step('Download') {
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
            sh 'docker tag holaj:prueba dpalomerostratio/holaj2'
            sh 'docker push dpalomerostratio/holaj2'
        }
        echo 'genera'
    }
    stage('Anchore') {
        writeFile file: 'anchore_images', text: 'dpalomerostratio/holaj2'
        echo 'prueba anchore'
        anchore(name: 'anchore_images', forceAnalyze: true)
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
