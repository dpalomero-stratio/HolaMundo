FROM alpine:latest
USER root
ADD hola.jar /Hola_Mundo/src/Prueba/hola.jar
RUN apk --update add openjdk8-jre
ENTRYPOINT ["java","-jar","/Hola_Mundo/src/Prueba/hola.jar"]
