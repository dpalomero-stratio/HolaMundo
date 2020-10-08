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
            sh 'docker tag holaj:prueba dpalomerostratio/holaj2'
            sh 'docker push dpalomerostratio/holaj2'
        }
        echo 'genera'
    }
    stage('Anchore') {
        sh 'docker pull dpalomerostratio/holaj2'
        def imageLine = 'holaj2'
        writeFile file: 'anchore_images', text: imageLine
        anchore(name: 'anchore_images', engineRetries:'${util.getTimeout().toInteger() * 60}', forceAnalyze: true)
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
