FROM alpine:latest
USER root
COPY . Hola_Mundo/src/Prueba
WORKDIR Hola_Mundo/src/Prueba
RUN apk --update add openjdk8-jre 
ENTRYPOINT ["java","-jar","hola.jar"]
