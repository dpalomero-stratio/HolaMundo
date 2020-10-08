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
            sh 'docker tag holaj:prueba localhost:5000/holaj'
            sh 'docker push localhost:5000/holaj'
        }
        echo 'genera'
    }
    stage('Anchore') {
        def imageLine = 'holaj'
        writeFile file: 'anchore_images', text: imageLine
        anchore(name: 'anchore_images', engineRetries: "${util.getTimeout().toInteger() * 60}", forceAnalyze: true)
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
