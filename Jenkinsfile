node {
    stage('Download') {
        git 'https://github.com/dpalomero-stratio/HolaMundo.git'
    }
    stage('Compile') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'javac hola.java'
            sh 'jar -cfm hola.jar manifest.mf hola.class'
        }
    }
    stage('Generate') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'docker build -t holaj:prueba .'
            sh 'docker tag holaj:prueba dpalomerostratio/holaj2'
            sh 'docker push dpalomerostratio/holaj2'
        }
    }
    stage('Anchore') {
        writeFile file: 'anchore_images', text: 'dpalomerostratio/holaj2'
        anchore(name: 'anchore_images', forceAnalyze: true)
    }
    stage('Ejecute') {
        dir("Hola_Mundo/src/Prueba") {
            sh 'docker run -d --name "holamundo" holaj2'
            sh 'docker logs holamundo'
        }
    }
}
