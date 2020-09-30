FROM alpine:latest
USER root
ADD hola.jar /Hola_Mundo/src/Prueba
RUN apk --update add openjdk8-jre
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","./hola.jar"]
